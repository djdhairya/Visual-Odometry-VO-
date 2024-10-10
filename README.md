# Visual-Odometry-VO-


Visual Odometry (VO) is a technique used to estimate a vehicle's trajectory by analyzing the motion between consecutive images captured from a camera. It is widely applied in fields like autonomous driving, robotics, and augmented reality. The process involves identifying key points in sequential images, calculating their movement, and then estimating the vehicle’s position and orientation over time.

### Key Steps in Visual Odometry:

1. **Image Acquisition**: The system captures grayscale images from a camera mounted on the vehicle or robot.
   
2. **Feature Detection**: Features (keypoints) are detected in the image using an ORB (Oriented FAST and Rotated BRIEF) detector. These keypoints represent significant image regions such as corners and edges.

3. **Feature Matching**: The keypoints detected in two consecutive frames are matched using a feature-matching algorithm, such as the FLANN (Fast Library for Approximate Nearest Neighbors). Lowe's ratio test is used to retain only the best matches between frames.

4. **Essential Matrix Calculation**: From the matched keypoints, the essential matrix is computed, which encodes the relative rotation and translation between the two camera frames.

5. **Decomposition of Essential Matrix**: The essential matrix is decomposed into a rotation matrix and a translation vector, which provide information about the camera’s movement between frames.

6. **Triangulation**: Using the computed transformation matrix, points are triangulated between the two camera views, allowing estimation of the 3D positions of these points in space.

7. **Pose Estimation**: The transformation matrix is used to update the vehicle’s current pose (position and orientation) relative to its previous pose. The estimated path is iteratively refined as new images are processed.

8. **Visualization**: The ground truth path (based on external sensors) and the estimated path (from visual odometry) are plotted for comparison. This allows for a visual understanding of the accuracy of the VO system.

In this implementation, the system reads calibration data, ground truth poses, and images from the KITTI dataset, detects and matches features using ORB and FLANN, computes the essential matrix, and estimates the vehicle’s motion through multiple frames. The final output is a plot comparing the ground truth trajectory with the estimated path based on visual odometry.
