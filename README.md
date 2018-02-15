# Implementation

---

## The Model

* state
The vehicle is located at a position with x and y;The vehicle also has an orientation with psy;It also have a velocity with v ; CTE is Cross Track Error,it can express the error between the center of the road and vehicle's position.Epsi is the desired orientation subtracted from the current orientation.

* actuators
We'll consider the throttle and brake pedals as a single actuator,with negative values signifying braking and positive values signifying accelerating.Another actuator is the steering wheel.

* update equations
after we begin to state feedback loop,first we pass the current state to the model predictive controller,next the optimization solver is called.The solver uses the initial state, the model constraints and cost function to return a vector of control inputs that minimize the cost function.The solver we'll use is called IPOPT.We apply the first control input to the vehicle and repeat the loop.
   

## Timestep Length and Elapsed Duration (N & dt)
N is the number of timesteps in the horizon.dt is how much time elapses between actuations. 


## Polynomial Fitting and MPC preprocessing

* polyfit
Use polyfit to fit a 3rd order polynomial to the given x and y coordinates representing waypoints.
* polyeval
Use polyeval to evaluate y values of given x coordinates.



## Model Predictive Control with Latency

A contributing factor to latency is actuator dynamics. The approach is running a simulation using the vehicle model starting from the current state for the duration of the latency. The resulting state from the simulation is the new initial state for MPC.



