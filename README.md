Darkernel-Proyect
=================

ICS kernel para LG Optimus 3D

How to build

1. Android build

(1) Get the android base source code. 
  - Download the original android source code ICS 4.0.4 (android-4.0.4_r1.1) from http://source.android.com/source/downloading.html

(2) Overwrite modules that you want to build. 
  - Untar opensource packages of LGSU760_ICS_Android.tar.gz into downloaded android source directory 
  - And, merge the source into the android source code
  
(3) Run the build scripts. 
  - You have to add google original prebuilt source(toolchain) before running build scripts. 
  - Run the following scripts to build android
  
	a) source build/envsetup.sh
	b) lunch full-user
	c) make -j4          

	* When you compile the android source code, you have to add google original prebuilt source(toolchain) into the android folder 
	* "-j4" : The number, 4, is the number of multiple jobs to be invoked simultaneously. 

2. Kernel Build
  - Untar using following command at the android folder:
	tar xvfj LGSU760_ICS_Kernel.tar.gz
	
  - change directory to kernel root
	cd kernel

  - make configuration:
	make cosmo_su760_defconfig ARCH=arm  
	
  - make kernel zImage:
	make ARCH=arm CROSS_COMPILE=../prebuilt/linux-x86/toolchain/arm-linux-androideabi-4.4.x/bin/arm-linux-androideabi- zImage

3. You can download TI omx open source from TI web site (http://omapzoom.org). 
   The location of TI omx open source is android/hardware/omx directory in android source.   