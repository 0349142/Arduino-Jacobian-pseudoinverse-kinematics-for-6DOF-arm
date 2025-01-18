# Arduino-Jacobian-pseudoinverse-kinematics-for-6DOF-arm
A Jacobian pseudoinverse method at iteratively arriving to the correct end effector positions for a 6DOF arm. This code is for controlling a 6-DOF robotic arm using stepper motors driven by the AccelStepper library. It implements both forward kinematics and inverse kinematics (IK), enabling precise movement of the end-effector to specified target positions and orientations in 3D space.

# includes:

IK Solver:
Uses the pseudoinverse Jacobian to compute joint angle corrections based on the error between the target and current position.
Includes a convergence threshold and limits iterations to ensure stability.


Safety Mechanisms:
Joint angles are constrained to stay within predefined limits.
Prevents invalid configurations that could damage the hardware.

Motion Control:
Combines acceleration/deceleration (via AccelStepper) with smooth interpolation for precise and realistic movements.

Feedback and Debugging:
Prints messages to the serial monitor for errors (e.g., "IK solution not found") and current states (e.g., joint angles and positions).
Enables easy monitoring and troubleshooting.

# How the Code Works

Initialization:
Sets motor speed and acceleration parameters in setup().
Waits for serial input in loop().

Input Handling:
Reads a 6D target (position and orientation) from the serial monitor.
Converts it into joint angles using the IK solver.

Movement:
Smoothly interpolates between the current and target joint angles using moveToTargetSmoothly.
Ensures all motors move synchronously to achieve the desired end-effector pose.

Feedback:
Provides real-time feedback on errors, joint states, and actions through the serial monitor.
