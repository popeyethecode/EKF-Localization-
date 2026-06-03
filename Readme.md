# Extended Kalman Filter (EKF) Localization

## Overview

This project implements **robot localization using the Extended Kalman Filter (EKF)** in MATLAB/Octave. The robot moves in a 2D environment containing known landmarks and estimates its pose `(x, y, θ)` while accounting for motion and sensor uncertainty.

The implementation follows concepts from:

* *Probabilistic Robotics* by Thrun, Burgard, and Fox
* EKF Localization lectures and robotics coursework

## Objective
The goal of this project is to estimate the robot's position and orientation using:
* Motion commands (control inputs)
* Noisy sensor measurements
* Known landmark locations
The EKF continuously combines prediction and measurement updates to reduce uncertainty in the robot's state estimate.

## State Representation
The robot state is defined as:
[
x =
\begin{bmatrix}
x \
y \
\theta
\end{bmatrix}
]

where:

* `x` = robot position along X-axis
* `y` = robot position along Y-axis
* `θ` = robot orientation (heading)

---

## EKF Workflow

### 1. Prediction Step

Using the robot motion model:

* Predict the next state
* Linearize the motion model using Jacobians
* Propagate uncertainty

Outputs:

* Predicted state estimate
* Predicted covariance matrix

---

### 2. Measurement Update

For each observed landmark:

* Compute expected range and bearing
* Calculate innovation (measurement error)
* Compute Kalman Gain
* Correct state estimate
* Reduce uncertainty

Outputs:

* Updated state estimate
* Updated covariance matrix

---

Features
* EKF localization in 2D
* Known landmark map
* Motion noise modeling
* Sensor noise modeling
* Covariance propagation
* Kalman gain computation
* Trajectory visualization
* Ground truth vs estimated trajectory comparison
* 
## Project Structure
├── ekf_localization.m
├── prediction_step.m
├── measurement_update.m
├── motion_model.m
├── plots/
└── README.md

## Mathematical Formulation

### Prediction

State prediction:

[
\hat{x}*t = g(u_t, x*{t-1})
]

Covariance prediction:

[
P_t = G_t P_{t-1} G_t^T + Q_t
]

where:

(G_t) = Motion Jacobian
(Q_t) = Process noise covariance

### Measurement Update

Innovation:
[
y_t = z_t - \hat{z}_t
]

Innovation covariance:
[
S_t = H_t P_t H_t^T + R_t
]

Kalman Gain:
[
K_t = P_t H_t^T S_t^{-1}

State correction:
[
x_t = \hat{x}_t + K_t y_t
]

Covariance correction:
[
P_t = (I - K_t H_t)P_t
]

The simulation visualizes:
* Ground truth trajectory
* Dead-reckoning trajectory
* EKF estimated trajectory
* Landmark locations
* Covariance uncertainty evolution

 Future Improvements
* EKF-SLAM
* Unscented Kalman Filter (UKF)
* Particle Filter Localization
* Data Association
* Real robot implementation using ROS

Through this project, I learned:
* Bayesian state estimation
* Gaussian uncertainty representation
* Jacobian linearization
* Kalman filtering concepts
* Robot localization fundamentals
* Probabilistic robotics algorithms

References
1. *Probabilistic Robotics* — Sebastian Thrun, Wolfram Burgard, Dieter Fox
2. EKF Localization Lecture Notes by Cyril Stachniss.
3. Robotics and Autonomous Systems coursework

 Author

**Lakshit Khandal**

Robotics | Autonomous Systems | State Estimation | Localization
