# 1 About Kalman Filter

## 1.1 Introduction

> Most of the modern systems are equipped with numerous sensors that provide estimation of hidden (unknown) variables based on the series of measurements

Ex.1: GPS receiver provides us the <u>location</u> and <u>velocity</u>, which is derived from differential time of <u>satellite signals</u>. Here the location and velocity are hidden variables, and satellite signals are measurements.

> One of the biggest challenges of tracking and control system is to provide accurate and precise estimation of the hidden variables in presence of uncertainty

Ex.2: thermal noise, atmospheric effects, slight changes in satellite's positions, receiver clock precision could result in imprecise measurement of GPS.

* Based on these two insights, what does Kalman filter do ?
  1. The Kalman Filter produces estimates of hidden variables based on inaccurate and uncertain measurements
  2. The Kalman Filter provides a prediction of the future system state, based on the past estimations
* Some history:
  * The filter is named after Rudolf E. Kalman (May 19, 1930 – July 2, 2016)
  * In 1960, Kalman published his famous paper describing a recursive solution to the discrete-data linear filtering problem



## 1.2 Basic Notions

The motion of a moving object in 3D space according to Newton's law:
$$
\left\{\begin{matrix}
                                        x= x_{0} + v_{x0} \Delta t+ \frac{1}{2}a_{x} \Delta t^{2}\\ 
                                        y= y_{0} + v_{y0} \Delta t+ \frac{1}{2}a_{y} \Delta t^{2}\\
                                        z= z_{0} + v_{z0} \Delta t+ \frac{1}{2}a_{z} \Delta t^{2}
                                        \end{matrix}\right.
$$

* **System state**: parameters for describing the target object ($[x,y,z,v_x,v_y,v_z,a_x,a_y,a_z]$), Kalman filter use the current state as input, and predict the future states (outputs)
* **Dynamic model** (or **State-space model**): model that describes the relationship between inputs and outputs
* **Measurement noise**: in theory, given system state and dynamic model, the future states could be easily derived. But, all measurements (observed system state) incudes errors, which is called measurement noise.
* **Process noise**: the target motion would not strictly follow the Newton equations, as there are a number of other factors would affect the motion.

* Kalman Filter explicitly considers the measurement noise and the process noise to make better prediction.