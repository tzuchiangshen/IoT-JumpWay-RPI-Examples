# Installation Of OpenCV 3.1.0 On Raspberry Pi

![TechBubble IoT JumpWay Docs](../images/main/Raspberry-Pi-Documentation.png)

## Introduction

The following information will help you install OpenCV3.1.0 on your Raspberry Pi. This installation includes the additional modules required for facial identification.

## Hardware Requirements

1. Raspberry Pi.
2. 16 GB Card

## Software Requirements

1. Jessie

## Guide

1. Update apt-get:

    ```
    $ sudo apt-get update
    $ sudo apt-get upgrade
    ```

2. Install developer tools:

    ```
    $ sudo apt-get install build-essential cmake git pkg-config
    ```

3. Install image I/O packages:

    ```
    $ sudo apt-get install libjpeg-dev libtiff5-dev libjasper-dev libpng12-dev
    ```

4. Install GTK development library:

    ```
    $ sudo apt-get install libgtk2.0-dev
    ```

5. Install video processing software:

    ```
    $ sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
    ```

6. Install libraries used to optimize OpenCV:

    ```
    $ sudo apt-get install libatlas-base-dev gfortran
    ```

6. Install Python 2.7 development libraries:

    ```
    $ sudo apt-get install python2.7-dev
    ```

7. Install Numpy:

    ```
    $ pip install numpy
    ```

8. Checkout current OpenCV 3.1.0:

    ```
    $ cd ~
    $ git clone https://github.com/Itseez/opencv.git
    $ cd opencv
    $ git checkout 3.1.0
    ```

9. Checkout OpenCV Modules  3.1.0:

    ```
    $ cd ~
    $ git clone https://github.com/Itseez/opencv_contrib.git
    $ cd opencv_contrib
    $ git checkout 3.1.0
    ```

9. There is an issue with some of the code that needs to be fixed before you can build:

    ```
    $ nano ~/opencv_contrib/blob/master/modules/face/include/opencv2/face.hpp
    ```

    Change line 259 to: 

    ```
    CV_WRAP_AS(predict_label) int predict(InputArray src) const;
    ```

10. Setup the build:

    ```
    $ cd ~/opencv
    $ mkdir build
    $ cd build
    $ cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D INSTALL_C_EXAMPLES=OFF -D INSTALL_PYTHON_EXAMPLES=ON -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib/modules -D BUILD_EXAMPLES=ON ..
    ```

11. Make and make install the build:

    ```
    $ make -j4
    $ sudo make install
    $ sudo ldconfig
    ```

## IoT JumpWay Raspberry Pi Documentation & Tutorials Bugs/Issues

Please feel free to create issues for bugs and general issues you come across whilst using the IoT JumpWay Raspberry Pi Examples. You may also use the issues area to ask for general help whilst using the IoT JumpWay Raspberry Pi Examples in your IoT projects.

## IoT JumpWay Raspberry Pi Documentation & Tutorials Contributors

- [Adam Milton-Barker, TechBubble Technologies Founder](https://github.com/AdamMiltonBarker "Adam Milton-Barker, TechBubble Technologies Founder")

![Adam Milton-Barker,  Intel Software Innovator](../images/main/Intel-Software-Innovator.jpg)  