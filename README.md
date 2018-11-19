### Robot Motion tracking using INRIA VISP framework ontop of OpenCV

This repo is a configuration of the VISP hybrid tracker setup.

#### SETUP

**Use software:**

 * [VISP](http://visp-doc.inria.fr 3.1.0_1)
 * [OpenCV](https://docs.opencv.org/3.4/d9/df8/tutorial_root.html)
 * [Subversion](https://www.tutorialspoint.com/svn/)
 * [Git](https://git-scm.com/downloads)
 * cmake


Installing OpenCV and all required packages is straight forward in Ubuntu. The setup should work on all systems with correctly installed VISP 3.1.0_1 and OpenCV 3.x.x

`$ sudo apt get install libvisp-dev cmake`

add the basic files from VISP which we are using:

`$ svn export https://github.com/lagadic/visp.git/trunk/tutorial/tracking/model-based/generic`

Next, pull this repo into a preffered workspace:

`$ git clone https://github.com/suegy/motion-tracking.git`

 * navigate into the generic folder
 * download the [Robbox.mpg](https://www.dropbox.com/s/ks61s38g8j4syx7/Robbox.mpg?dl=0) video from dropbox and place it in the same folder
 * use cmake to build the project: `cmake .`
 * `make` to build the tracker
 * use the `run.sh` script to start the tracker with the Robbox.mpg video

### Configuration

 `run.sh` calls `tutorial-mb-generic-tracker.full` in hybrid mode using the Robbox mpg, init & cao file for specifying the object to track

The cao and init file are faily simple for the box and contain measurements in meters
The tracker module contains the parameters for the video and the camera (gopro).
`px` and `py` need to be adjusted as well as the lens deformation.

In the while loop the cMo matrix will be written to a CSV file one tranformation per frame

