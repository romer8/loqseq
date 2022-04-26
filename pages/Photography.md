---
title: Photography
tags: Python, Cameras, gPhoto
---

- How to Use Your DSLR Camera as a Webcam in Linux
	- Reference: [How to Use Your DSLR Camera as a Webcam in Linux](https://www.crackedthecode.co/how-to-use-your-dslr-as-a-webcam-in-linux/)
	- Install the Software needed
		- Install the kernel headers
			- `sudo pacman -S "linux$(uname -r | awk -F. '{print $1$2}')-headers"`
		- Install the actual software
			- `pacman -S gphoto2 v4l-utils v4l2loopback-dkms ffmpeg`
		- Once you’ve installed the required packages, connect your camera to your PC via USB and power on the camera. You can safely ignore any OS popup message which may appear.
		- Open your Terminal application, and enter the following command:
			- `sudo modprobe v4l2loopback exclusive_caps=1 max_buffers=2`
	- Test
		- List auto-detected cameras and the ports to which they are connected. `gphoto2 --auto-detect`
		- Summary of camera status. `gphoto2 --summary`
		- Display the camera and driver abilities specified in the libgphoto2 database. Use --summary to query an overview of the camera. `gphoto2 --abilities`