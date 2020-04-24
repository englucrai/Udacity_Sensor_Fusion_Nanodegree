# Udacity Sensor Fusion Nanodegree Course

This contains my homework assignments and quiz solutions for the programming portions of this nanodegree. They will be partitioned into separate directories, one for each course. Each course will have separate build instructions. Please note that I have also included the YOLOv3 weights from the Camera course as part of this repo. You will need Git LFS to download the weights. Please visit <https://github.com/git-lfs/git-lfs/wiki/Installation> to install Git LFS. Once you do, clone the repo and in the repo directory please use the following to download the YOLOv3 weights.

Also note that the Radar section of this course uses MATLAB so you will need to have this software available to run the code for this part of the course.  This was not explicitly mentioned in the official overview of the course which alludes to only knowing C++.

```
$ cd <path to this repo>
$ git lfs fetch
```

The weights will appear in `SFND_Camera/detect_objects/dat/yolo/yolov3.weights`

# Instructions for building and running

## LiDAR Obstacle Detection Course

This can be found in the `SFND_Lidar_Obstacle_Detection` directory in this repo. This was initially a fork from <https://github.com/udacity/SFND_Lidar_Obstacle_Detection>, but I made significant changes to the formatting, fixed some bugs that were seen on the Issues page of the original repo and diverged away a bit from the original specifications for submitting the project. However, the directory essentially contains the completed project and does fulfill the guidelines required to gain a successful pass.

If you'd like to see the commit history of how the project progressed from the beginning until completion, please see my fork: <https://github.com/rayryeng/SFND_Lidar_Obstacle_Detection>

Please note that it is assumed that you have all of the dependencies installed for this to build successfully. For instructions on getting these dependencies, please refer to the original repo or my fork from the links above. However, you should only need to install PCL as the extra dependency, which will tie in all of the other dependencies required upon installation (Boost in particular).

To build this project, there are three submodules.

### Main environment

The main environment for the detection is for taking in a stream of PCD files and showing the object detection for cars / obstacles in 3D in real-time. This can be built navigating to the `SFND_Lidar_Obstacle_Detection` directory and using the `CMakeLists.txt` file in that directory:

```
$ cd SFND_Lidar_Obstacle_Detection
$ mkdir build && cd build
$ cmake ..
$ make
```

You can then run the environment by just doing:

```
$ ./environment
```

### RANSAC quiz

The portion of the course that tests the implementation of 3D plane estimation using RANSAC can be built navigating to the `SFND_Lidar_Obstacle_Detection/src/quiz/ransac` directory and using the `CMakeLists.txt` file in that directory:

```
$ cd SFND_Lidar_Obstacle_Detection/src/quiz/ransac
$ mkdir build && cd build
$ cmake ..
$ make
```

You can then run the clustering quiz by:

```
$ ./quizRansac
```

### Cluster quiz

The portion of the course that tests the implementation of Euclidean clustering can be built navigating to the `SFND_Lidar_Obstacle_Detection/src/quiz/cluster` directory and using the `CMakeLists.txt` file in that directory:

```
$ cd SFND_Lidar_Obstacle_Detection/src/quiz/cluster
$ mkdir build && cd build
$ cmake ..
$ make
```

You can then run the clustering quiz by:

```
$ ./quizCluster
```

## Camera Course

OpenCV must be installed on your system prior to building. On Linux, you can simply follow: <https://www.learnopencv.com/install-opencv-4-on-ubuntu-16-04/>. On Mac OS, you can install OpenCV through Homebrew <https://formulae.brew.sh/formula/opencv>, specifically with `brew install opencv`. On Windows, you can download pre-compiled binaries from the official website: <https://opencv.org/releases/>

Navigate to the `SFND_Camera/` directory to access the exercises and projects for this course.

### Intro to OpenCV Exercises

Navigate to the `SFND_Camera/intro_to_opencv_exercises/OpenCV_exercises` directory, then build it:

```
$ cd SFND_Camera/intro_to_opencv_exercises/OpenCV_exercises
$ mkdir build && cd build
$ cmake ..
$ make
```

This will create five executables that reflect the different tutorials exercises. Additionally, there are solutions from the instructor in `SFND_Camera/intro_to_opencv_exercises/solutions` that can be accessed.

### Intro to Time to Collision (TTC) Exercises

For the camera-based solution, navigate to the `SFND_Camera/TTC_Camera/TTC_camera` directory, then build it:

```
$ cd SFND_Camera/TTC_Camera/TTC_camera
$ mkdir build && cd build
$ cmake ..
$ make
```

This will create an executable for you to run. Additionally, there are solutions from the instructor in `SFND_Camera/TTC_Camera/solution` that can be accessed.

**Note:** My solution and the provided solution crash due to out of bounds errors. This is because the provided source code to parse the data files to get the keypoints does not function properly, thus resulting in negative indices for accessing a `std::vector` thus causing the crash.

For the LiDAR-based solution, navigate to the `SFND_Camera/TTC_lidar` directory, then build it:

```
$ cd SFND_Camera/TTC_lidar
$ mkdir build && cd build
$ cmake ..
$ make
```

### Intensity Gradient and Filtering Exercise

Navigate to the `SFND_Camera/intensity_gradient_filtering/gradient_filtering` directory, then build it:

```
$ cd SFND_Camera/intensity_gradient_filtering/gradient_filtering
$ mkdir build && cd build
$ cmake ..
$ make
```

This will create three executables for you to run. Additionally, there are solutions from the instructor in `SFND_Camera/intensity_gradient_filtering/solutions` that can be accessed.

**Note:** The instructor used double `for` loops for some of the solutions where I opted to use built-in OpenCV methods and operations (such as computing the gradient magnitude). Built-in operations using the `cv::Mat` class are faster as they are designed to operate on these datatypes and are multi-threaded when applicable.

### Harris Corner Detector Exercise

Navigate to the `SFND_Camera/harris_corner_nms/cornerness_harris` directory then build it:

```
$ cd SFND_Camera/harris_corner_nms/cornerness_harris
$ mkdir build && cd build
$ cmake ..
$ make
```

This will create an executable for you to run. Additionally, there are solutions from the instructor in `SFND_Camera/harris_corner_nms/cornerness_harris/solution` that can be accessed.

**Note:** The instructor's solution use the `cv::KeyPoint::overlap()` method to perform non-maximum suppression. In particular, keypoints can only exist if the particular keypoint within a finite window have the strongest response over all points that overlap with said keypoint. I approached this differently where within a finite window, we search for the largest response and the centre of the window should have this response. If and only if the largest response in the centre of this window is the largest do we keep this keypoint. This amounts to the same principle, but I felt that I approached it more sanely.

### Detect Keypoints Exercise

Navigate to the `SFND_Camera/detect_keypoints/detect_keypoints` directory then build it:

```
$ cd SFND_Camera/detect_keypoints/detect_keypoints
$ mkdir build && cd build
$ cmake ..
$ make
```

This will create an executable for you to run. Additionally, there are solutions from the instructor in `SFND_Camera/detect_keypoints/detect_keypoints/solution` that can be accessed.

### Describe Keypoints Exercise

Navigate to the `SFND_Camera/describe_keypoints/describe_keypoints` directory then build it:

```
$ cd SFND_Camera/describe_keypoints/describe_keypoints
$ mkdir build && cd build
$ cmake ..
$ make
```

This will create an executable for you to run. Additionally, there are solutions from the instructor in `SFND_Camera/describe_keypoints/describe_keypoints/solution` that can be accessed.

### Descriptor Keypoint Matching Exercise

Navigate to the `SFND_Camera/descriptor_matching/descriptor_matching` directory then build it:

```
$ cd SFND_Camera/descriptor_matching/descriptor_matching
$ mkdir build && cd build
$ cmake ..
$ make
```

This will create an executable for you to run. Additionally, there are solutions from the instructor in `SFND_Camera/descriptor_matching/descriptor_matching/solution` that can be accessed.

### Midterm Project

In order to track commits (unlike the first project where I forked the project and just put everything in as one commit), I've cloned the original midterm project repo from here: <https://github.com/udacity/SFND_2D_Feature_Tracking>. Please ensure that you have the right dependencies installed by looking at this repo prior to building. Navigate to the `SFND_Camera/SFND_2D_Feature_Matching` directory then build it:

```
$ cd SFND_Camera/SFND_2D_Feature_Matching
$ mkdir build && cd build
$ cmake ..
$ make
```

This will create an executable for you to run. This executable takes in command-line arguments. Please review the midterm report README for more details in `SFND_Camera/SFND_2D_Feature_Matching/README_Midterm_Report.md`.

### LiDAR to Camera Exercise

Navigate to the `SFND_Camera/lidar_to_camera/lidar_to_camera` directory then build it:

```
$ cd SFND_Camera/lidar_to_camera/lidar_to_camera
$ mkdir build && cd build
$ cmake ..
$ make
```

This will create an executable for you to run. Additionally, there are solutions from the instructor in `SFND_Camera/lidar_to_camera/solution` that can be accessed.

### Detect Objects Exercise

Navigate to the `SFND_Camera/detect_objects` directory then build it:

```
$ cd SFND_Camera/detect_objects
$ mkdir build && cd build
$ cmake ..
$ make
```

This will create an executable for you to run.

### Cluster with ROI Exercise

Navigate to the `SFND_Camera/cluster_with_roi` directory then build it:

```
$ cd SFND_Camera/cluster_with_roi
$ mkdir build && cd build
$ cmake ..
$ make
```

This will create an executable for you to run.

### Final Project

In order to track commits, I've cloned the original final project repo from here: <https://github.com/udacity/SFND_3D_Object_Tracking>. Please ensure that you have the right dependencies installed by looking at this repo prior to building. Navigate to the `SFND_Camera/SFND_3D_Object_Tracking/` directory then build it:

```
$ cd SFND_Camera/SFND_3D_Object_Tracking
$ mkdir build && cd build
$ cmake ..
$ make
```

This will create an executable for you to run. This executable takes in command-line arguments. Please review the final project report README for more details in `SFND_Camera/SFND_3D_Object_Tracking/README_Final_Report.md`. You can also have a look at the Jupyter Notebook located in `SFND_Camera/SFND_3D_Object_Tracking/TTC_Camera_Plots.ipynb` to take a look at the TTC performance graphs for different combinations of detectors and descriptors, but they're included in the final report for self-completeness.

## Radar Course

### Lesson 2 - Radar Principles

This section of the course talks about the maximum range a Radar can have for detecting objects.  In `SFND_Radar/Lesson2_Radar_Range_Equation`, a MATLAB exercise is provided to calculate this quantity given the requirements of the Radar device in question.  Just run the script in this directory to see the final output value.

### Lesson 3 - Range-Doppler Estimation

This section of the course discusses the Doppler effect and how to simultaneously estimate the velocity and position of an object.  In `SFND_Radar/Lesson3` are various exercises to estimate the range (distance from the ego vehicle), the velocity (via the Doppler effect) and understanding how the Fast Fourier Transform (FFT) works, specifically on how it applies to simultaneous range and velocity estimation of objects with respect to the ego vehicle.  Just run each script individually to see what the relevant outputs are.

### Lesson 4 - Constant False Alarm Rate (CFAR)

This section of the course studies the Constant False Alarm Rate (CFAR) technique on how to adaptively threshold the frequency spectrum obtained by a radar signal to detect obstacles in the environment.  I have implemented both the original non-efficient version using loops and one using convolution.  In `SFND_Radar/Lesson4`, a MATLAB exercise is provided to demonstrate how to find peaks in a frequency spectrum.  Just run the script to see what the relevant outputs are.