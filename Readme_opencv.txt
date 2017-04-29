Readme_opencv.txt for attempt to install OpenCV with Python 3
Repository: https://github.com/shantnu/PyEng
29-Apr-2017
David Dorff
davidd639@yahoo.com

Environment:  Ubuntu 16.04.2; installed in AWS EC2 (Free tier)

Summary: Ultimately, I was not able to get the full installation completed such that I could verify that I was using OpenCV with FFMPEG. I was able to successfully install OpenCV and was also able to build it successfully, which I will review below.

But here is what I used to determine if all was working.  URL:
http://stackoverflow.com/questions/42191058/opencv-python-installation-missing-ffmpeg-windows
This page made reference to a more detailed StackOverflow discussion, from which I used a Python snippet to test.
http://stackoverflow.com/questions/23119413/how-to-install-python-opencv-through-conda/30281466#30281466

The code:

    import cv2
    print( cv2.__version__ )

    cap = cv2.VideoCapture("test.mp4")
    print ( cap.isOpened() ) # True = read video successfully. False - fail to read video.

    fourcc = cv2.VideoWriter_fourcc(*'XVID')
    out = cv2.VideoWriter("output_video.avi", fourcc, 20.0, (640, 360))
    print ( out.isOpened() ) # True = write out video successfully. False - fail to write out video.

    cap.release()
    out.release()

With the print statements returning False, that's how I know it wasn't working.  :-(


Here are many of the steps in the attempts.
First, here is what was done to install ffmpeg.

# instructions site
#    http://ubuntuhandbook.org/index.php/2016/09/install-ffmpeg-3-1-ubuntu-16-04-ppa/

#command
sudo add-apt-repository ppa:jonathonf/ffmpeg-3

#More info: https://launchpad.net/~jonathonf/+archive/ubuntu/ffmpeg-3
#Output:
    #Press [ENTER] to continue or ctrl-c to cancel adding it
    #
    #gpg: keyring `/tmp/tmpemm67fq1/secring.gpg' created
    #gpg: keyring `/tmp/tmpemm67fq1/pubring.gpg' created
    #gpg: requesting key F06FC659 from hkp server keyserver.ubuntu.com
    #gpg: /tmp/tmpemm67fq1/trustdb.gpg: trustdb created
    #gpg: key F06FC659: public key "Launchpad PPA for J Fernyhough" imported
    #gpg: Total number processed: 1
    #gpg:               imported: 1  (RSA: 1)
    #OK

# NEXT, RUN:
sudo apt update && sudo apt install ffmpeg libav-tools x264 x265

#CONFIRMED by running ffmpeg in terminal to get version info and build details

--------------------------------

OpenCV

Unfortunately, my experience with installation packages has been limited and so I went down different paths, using apt-get, pip, and conda.   I can provide more information on sites visited and dead-end paths, but I think that would obfuscate matters.

As had been inferred, installing OpenCV generally comes without FFMPEG enabled.  I confirmed that and this was a good instructional link:
https://askubuntu.com/questions/783956/how-to-install-opencv-3-1-for-python-3-5-on-ubuntu-16-04-lts
The comments there indicated that all went well except for the FFMPEG portion.  The last comment indicated some success using homebrew.
I didn't try this, as I hadn't used it before and hoped to have some success trying to build OpenCV myself.  But here'w what they suggested, for reference:

    brew install ffmpeg
    brew install opencv3 --with-ffmpeg -v (Python 2.7)
    brew install opencv3 --with-python3 --with-ffmpeg -v (Python 3.6)

I used the same page to try building it and also this other link which that page references:
http://cyaninfinite.com/tutorials/installing-opencv-in-ubuntu-for-python-3/

I was ultimately able to get OpenCV to build, but as I indicated earlier, I hadn't worked out getting it all pulled together so that my test Python program would confirm success.
There was also an extremely frustrating complication:  I ran out of disk space on the AWS EC2 Free Tier instance of Linux.  I'm still not sure if I could get everything done without this happening.  Of course, expanding the volume size is another option I could investigate, but it may be that I could reduce the footprint if some of the steps I took were unnecessarily using up space.

Here are some of the key steps:

    sudo apt-get update
    sudo apt-get install build-essential cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
    sudo apt-get install python3.5-dev
    python3.5-config --includes
    sudo cp /usr/include/x86_64-linux-gnu/python3.5m/pyconfig.h /usr/include/python3.5m/

    # From /home/ubuntu/anaconda3:
    mkdir OpenCV-tmp
    cd OpenCV-tmp
    git clone https://github.com/Itseez/opencv.git
    # that created directory opencv
    mv opencv opencv-3

    mkdir build
    cd build

    cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local ../opencv-3
    make -j $(nproc --all)

Here are my notes after running out of space and working around it (by clearing what I could).  I was trying to figure out what wasn't working!

    #checking what I have in Python
    >>> import site
    >>> site.getsitepackages()
    ['/home/ubuntu/anaconda3/lib/python3.6/site-packages']


    #shows that I'm looking at python3.6, but I installed OpenCV for python3.5
    # also found this when googling for:  import opencv from python3.5 when using python3.6
    #http://stackoverflow.com/questions/37188623/ubuntu-how-to-install-opencv-for-python3
    #it had hints about symbolically linking 

    #Meanwhile, trying to get the right version, I moved the old one out of the way:
    # From /home/ubuntu/anaconda3/lib/python3.6/site-packages/
    mkdir cv.bak
    mv cv2 opencv_python-3.2.0.7.dist-info cv.bak

    # In /home/ubuntu/.local/lib/python3.5/site-packages/cv2, I copied the directories over
    # Python was able to import cv2 again, but then the test_video.py script still failed to acknowledge opening the test.mp4 file
-----

So, that's where I gave up on that attempt.  I started over and completely spun up a new instance of Ubuntu on AWS EC2 and found a site referencing using Conda to do the install.  It seemed like that would be simpler.

Here are my notes from that effort.  Lines not preceded with '#', indicate instructions from this page:
http://dhaneshr.net/2016/06/03/installing-opencv-2-4-x-with-ffmpeg-python-on-anaconda/

conda install conda-build
conda install cmake

# Output
#The following NEW packages will be INSTALLED:

#    bzip2:   1.0.6-3
#    cmake:   3.6.3-0
#    ncurses: 5.9-10

git clone https://github.com/menpo/conda-opencv

At this point, go to the conda-opencv/conda folder and edit the build.sh file. Modify the following cmake flag in that file:

-DWITH_FFMPEG = 1 
Depending upon the version of cmake installed by Anaconda, edit the meta.yaml as follows:

...

requirements:
   build:
   - cmake 3.3.x  # change x to whatever version is installed
If you want to know which version of cmake is installed, you can issue:

$ conda list 

# I found that cmake is 3.6.3, so I changed meta.yaml from 3.3.0 to 3.6.3


conda build conda/

# CMake Error: CMake was unable to find a build program corresponding to "Unix Makefiles".  CMAKE_MAKE_PROGRAM is not set.  You probably need to select a different build tool.
# etc., etc.

# After more googling, I recalled having installed these in my other more direct attempt, so I ran:
# sudo apt-get install build-essential

# Then, I wound up with this error, which indicates, I probably was closer in my initial attempt!

    # + source /home/ubuntu/anaconda3/bin/activate /home/ubuntu/anaconda3/conda-bld/opencv_1493495917442/_t_env
    # + /home/ubuntu/anaconda3/conda-bld/opencv_1493495917442/_t_env/bin/python -s /home/ubuntu/anaconda3/conda-bld/opencv_1493495917442/test_tmp/run_test.py
    # import: 'cv2'
    # Traceback (most recent call last):
    #   File "/home/ubuntu/anaconda3/conda-bld/opencv_1493495917442/test_tmp/run_test.py", line 2, in <module>
    #     import cv2
    # ModuleNotFoundError: No module named 'cv2'
    # TESTS FAILED: opencv-2.4.11-py36_1

