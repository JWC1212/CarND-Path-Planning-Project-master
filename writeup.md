**Path  Planning Project**

The goals / steps of this project are the following:

* In this project a Path Planner is implemented in C++ to safely navigate a car in a virtual highway at as close as possible 50 MPH.
Selected states in the finite state machine(if FSM is used).
Trajectory generation strategy.
Speed, maximum acceleration, and jerk avoidance strategy.
Collision avoidance strategy.
Explanation of lane change decisions.

---

#  Selected states
## Although finite state machine is not used three states are considered: constant speed at limit speed, keep lane and change lane.

#  Lane Change decision
## If there is no vehicle in front of ego car out of 30 meters constant speed at limit speed.
## If there is vehicle in front of ego car in range of 30 meters and both left lane and right lane are occupied ego car keeps lane and follows at decreasing velocity to the minimum of the front car's velocity.
## If there is vehicle in front of ego car  and either right lane or left lane is available ego car will change lane.
## Decision is not based on the rear car in the same lane as ego car.

#  Trajectory generation strategy
## 50 points are used to make up a path with each time interval between two points 20ms.
## previous path is re-used as most of part of new path.
## generating three waypoints at 30m apart for the spline to use as template points. New way points are generated based on ego car's speed and 20ms interval from last point of previous path with spline's extrapolation.

#  Speed, maximum acceleration, and jerk avoidance strategy
## cost functions are not used in this project.
## ego car's velocity will change up to maximum speed.
## Because acceleration is change rate of velocity I use velocity change of 0.1 or 0.2 at 0.02s to make acceleration being less than max acceleration.
## Jerk can be avoided by small change of acceleration as acceleration avoidance strategy.

#  Collision avoidance strategy
## Front vehicle in the same lane will have a 30m safe distance from ego car.
## When considering lane change front vehicle in prospective lane at least needs 35m safe distance and behind car 15m with velocity less than ego's speed.



