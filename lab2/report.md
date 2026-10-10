# Lab 2 Report — Forward and Inverse Kinematics

**Name:**

## Task 1 — Cartesian trajectory (`moveL`)

1. Describe your trajectory. State the number of waypoints and the intended shape.
When inputted with the parameters of the waypoints, the intented trajectory was a downward paht, which then went back up. The number of waypoints for the robotic arm was three. The intended shape was meant to replicate a typical "pick and place" task for robotic manipulators. 

2. Did the TCP visit the requested points? Briefly describe the path between points.
While the TCP was able to visit the requested points on the cartesian scale, it was unable to replicate the rotational values of rx, ry, and rz that were inputted. This was the trend for all three waypoints. For the three waypoints, the rotational parameters of the end effector were vastly different than the intended values. For instance, the largest visible difference was in the rz values for waypoint three, where the intended rotational value was 3.7, but the actual pose was -2.58.

## Task 2 — Numerical inverse kinematics

1. In your own words, distinguish forward kinematics from inverse kinematics. What are the input and output of each for the UR5?
The most distinguishable factor between forward kinematics and inverse kinematics is that in inverse kinematics, the end position of the end effector is known and calculations need to be made to reach that position and joint angles will be output, whereas in forward kinematics, each joint is calculated using angles to reach a desired end effector position. For forward kinematics on UR5, the inputs are the joint angles and the outputs are the joint positions (x,y,z,rx,ry,rz). For inverse kinematics in UR5, the inputs are the joint positions (x,y,z,rx,ry,rz) and the outputs are the joint angles.

2. Compare `task1_joint_q.csv` with `task2_joint_q.csv`. Are the joint vectors identical? If not, give a reason why different joint configurations can still be reasonable for the same requested TCP pose.
The joint vectors are nearly identical, with slight differences in the precision of each parameter. The largest difference between the two methods is found in the x direction on waypoint three, with a difference of around -1.3. Some joint configurations in inverse kinematics can fail while some configurations can pass when given the same TCP pose due to the mathmatics behind each method. While forward kinematics outputs its joint position using valid joint angles, inverse kinematics has to calculate valid joint angles using an end effector position. While certain poses might be possible in inverse kinematics, there can be differences in the calculation as desired positions could result in joints colliding with the workspace or its own joint. Because forward kinematics is joint-by-joint based, it does not have these problems. 

## Task 3 — Joint-space test (`moveJ`)

1. Compare the target and measured final TCP poses in `task3_results.csv`. Did the end effector reach each requested position and orientation closely enough? Identify the largest position discrepancy you observed and give a plausible explanation for it.
While most of the targeted positions were reached within a small margin, there were slight discrepencies in the end effectors actual position vs its requested position. The largest discrepency that I observed was in waypoint three in the shoulder lift, where the difference between task 1 and task 3 was about 1.5. I believe this could have occured due to the requested value of ry causing a collision to another joint, therefore the actual value of ry was the closest value possible to the desired end effector position while also not colliding with objects. 

2. Did the robot follow the same *path* as in Task 1? Explain your observation using the difference between `moveL` (Cartesian-space interpolation) and `moveJ` (joint-space interpolation).
The robot did not follow the same path as in Task 1. When observing moveL, the movement was smooth and the path trajectory seemed to move intutively from one waypoint to another. However, for moveJ, the path trajectory was shakey when moving to waypoint one. When moving to waypoint two, the waypoint arm took a longer route to the desired end effector position than the moveL path.

3. Suppose two different joint vectors produce the same TCP pose. What additional criterion might a real robot application use to choose between them? Give an example.
An additional criterion a real robot application may use to choose between two joint vectors in the same TCP pose may be the vector that avoids as many collisions as possible. It is also possible that a real robot application will choose the vector that avoids having the joints be at their maximum rotational movement limit.
