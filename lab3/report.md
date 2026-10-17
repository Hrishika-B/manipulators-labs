# Lab 3 Report — RRT Narrow-Gap Tuning

**Name:**

## Task 1 — Two-joint narrow gap (plots only)

1. Briefly explain each parameter below. Feel free to use external resources to help you understand the parameters.
- `RRT2D_STEP_SIZE` RRT2D_STEP_SIZE is what finds the distance between the current and previous itteration.
- `RRT2D_GOAL_BIAS` RRT2D_GOAL_BIAS is the parameter that finds the balance between random sampling so that the trajectory is able to reach the final destination and is what influences the magnetiude of the goal bias.
- `RRT2D_VALIDATION_DISTANCE` RRT2D_VALIDATION_DISTANCE is the resolution of the step size that is between collision checks.
- `RRT2D_MAX_ITERATIONS` RRT2D_MAX_ITERATIONS is the maximum amount of samples that the RRT performs with given parameters.
- `RRT2D_SEED` RRT2D_SEED is the random sampling path that is followed by the program when exploring various different paths.

2. Which settings solved the gap and passed the fine check? Explain what you changed and why.
The settings that solved the gap and passed the fine check were the step size, goal bias, validation distance, and max iterations. Reducing the step size from the default settings was beneficial as the original distance was less than the established value, because of this, the program for the arm was not able to take smaller steps to navigate it through a tight setting. Due to that the max iterations needed to be increased in order to account for the decrease in the step size. The second parameter that was changed was the goal bias. The goal bias was changed so that the probability that the random samples would find the correct configured goal. The last parameter that I changed was the validation distance. I reduced this parameter so that each increment would be thoroughly checked in order to ensure that there were no collisions.


## Task 2 — UR5 narrow gap (Swift)


| Parameter changed | Value | Complete RRT path found? | Fine check passed? | Planning time (s) | What did you observe? |
|-------------------|------:|:------------------------:|:------------------:|------------------:|-----------------------|
| Starter settings  |       |                          |                    |                   |                       |
|                   |       |                          |                    |                   |                       |
|                   |       |                          |                    |                   |                       |

1. Briefly explain the parameter(s) you changed and why. 
The parameters I changed were the validation distance and the planning timeout. Prior to adjusting the parameters, the planner was not checking collisions thoroughly. This caused the robot arm to cut through the narrow wall. Because this was computationally intensive, the program continuously kept timing out. In order to fix this issue, I increased the time out parameter so that all calculations could be made. 

2. How did the lessons from Task 1 transfer to the UR5? 
The lessons from Task 1 transfer to the UR5, as in Task 1, it was shown that parameters such as validation distance had a large influence on the final path. In task 1, multiple iterations were not able to succeed due to the step sizes not being able to check through all collisions. In the same way, multiple iterations of Task 2 were unable to succeed, therefore, validation distance had to be reduced in order for the program to catch collision checks. In order to match this, the planning time out had to be adjusted in order for the program to not time out. 


3. What trade-offs did you observe between planning time and path quality? 
The trade-offs that I observed between planning time and path quality was that with an increase in planning time, the path quality was more refined. With a lower planning time, the planner program continually timed out, as there was no time for the computer to complete the computations. However, it is important to note that planning time is not a direct parameter that influences the path. Therefore, if all parameters are established correctly, the final path will be of better quality and will have less of a chance to fail calculations. 
