# Euler's Angles

## Finding the Overall Angle of An Object using Pitch, Roll, and Yaw
$$\cos^{-1} \begin{pmatrix}
    \vec{n_1} \begin{bmatrix}
    \cos \psi & -\sin \psi & 0 \\
    \sin \psi & \cos \psi & 0 \\
    0 & 0 & 1
    \end{bmatrix} \begin{bmatrix}
    \cos \theta & 0 & \sin \theta  \\ 
    0 & 1 & 0 \\
    -\sin \theta & 0 & \cos \theta
    \end{bmatrix} \begin{bmatrix}
    1 & 0 & 0 \\
    0 & \cos \phi & -\sin \phi \\
    0 & \sin \phi & \cos \phi
    \end{bmatrix} 
    \vec{n_2} \end{pmatrix}$$


where $\vec{n_1}$ is the normal vector of the ground plane, $\vec{n_2}$ is the normal vector of the rotated plane, and $\phi$, $\theta$, and $\psi$ are the roll, pitch, and yaw angles, respectively.

This equation represents the calculation of the overall angle of rotation of an object in 3D space based on its yaw, pitch, and roll angles. Let's break down each part of the equation:

- $\cos^{-1}$ is the inverse cosine function, which is used to calculate the angle of rotation in radians.
- $\vec{n_1}$ and $\vec{n_2}$ are vectors representing the normal vectors of two planes. In this case, $\vec{n_1}$ represents the normal vector of the ground plane (i.e., the plane with z-axis as its normal), while $\vec{n_2}$ represents the normal vector of the rotated ground plane.
- The three matrices inside the parentheses represent the three rotations needed to transform $\vec{n_1}$ into $\vec{n_2}$. These rotations are yaw ($\psi$), pitch ($\theta$), and roll ($\phi$), applied in that order. Each of these matrices represents a rotation around one of the axes of the 3D coordinate system.

To understand how these matrices work together to calculate the overall rotation angle, it's helpful to consider a simplified example. Let's say we have an object in 3D space with its normal vector aligned with the z-axis (i.e., its yaw, pitch, and roll angles are all zero). If we rotate the object around the x-axis (i.e., apply a pitch angle), the normal vector will no longer be aligned with the z-axis. We can represent this new normal vector as a combination of the original z-axis and a new y-axis that is perpendicular to both the x and z axes. This new y-axis can be obtained by rotating the original y-axis (which is perpendicular to both the x and z axes) around the x-axis by the pitch angle.

Similarly, if we then rotate the object around the y-axis (i.e., apply a roll angle), the normal vector will be further rotated away from the z-axis. We can represent this new normal vector as a combination of the original z-axis and a new x-axis that is perpendicular to both the y and z axes. This new x-axis can be obtained by rotating the original x-axis (which is perpendicular to both the y and z axes) around the y-axis by the roll angle.

Finally, if we then rotate the object around the z-axis (i.e., apply a yaw angle), the normal vector will be rotated even further away from the z-axis. We can represent this new normal vector as a combination of the original x, y, and z axes, rotated around the z-axis by the yaw angle.

The matrices inside the parentheses in the equation represent these three rotations, applied in reverse order. By multiplying these matrices together and then multiplying the result by $\vec{n_1}$, we get the rotated normal vector $\vec{n_2}$. The dot product of $\vec{n_1}$ and $\vec{n_2}$ is then taken and passed through the inverse cosine function to obtain the overall angle of rotation.

!!! warning
    Please do not try to make sense of this. It is just a waste of time... Pretty cool though.

```java title="Code Form" linenums="1"
/**
    * Uses bigsad Euler Angles math to get the overall angle of the robot.
    * @param yaw the yaw angle in radians - Rotation about the Z axis
    * @param pitch the pitch angle in radians - Rotation about the X axis
    * @param roll the roll angle in radians - Rotation about the Y axis
    * @return the overall angle of the robot in radians
    */
    public static double getOverallAngle(double yaw, double pitch, double roll) {

    // Set the ground plane normal vector
    double[] n1 = {0.0, 0.0, 1.0};

    // Calculate the rotation matrices
    double[][] Rx = {{1.0, 0.0, 0.0},
            {0.0, Math.cos(pitch), -Math.sin(pitch)},
            {0.0, Math.sin(pitch), Math.cos(pitch)}};

    double[][] Ry = {{Math.cos(roll), 0.0, Math.sin(roll)},
            {0.0, 1.0, 0.0},
            {-Math.sin(roll), 0.0, Math.cos(roll)}};

    double[][] Rz = {{Math.cos(yaw), -Math.sin(yaw), 0.0},
            {Math.sin(yaw), Math.cos(yaw), 0.0},
            {0.0, 0.0, 1.0}};

    // Calculate the normal vector of the rotated plane
    double[] n2 = new double[3];
    for (int i = 0; i < 3; i++) {
        n2[i] = 0.0;
        for (int j = 0; j < 3; j++) {
            n2[i] += Rz[i][j] * Ry[j][i] * Rx[j][i] * n1[j];
        }
    }

    // Calculate the dot product of the two normal vectors
    double dotProduct = 0.0;
    for (int i = 0; i < 3; i++) {
        dotProduct += n1[i] * n2[i];
    }

    // Calculate the overall tilt angle in degrees
    return Math.acos(dotProduct);

}
```