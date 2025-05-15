# fishconLC

![image](https://user-images.githubusercontent.com/1620953/126903606-7388236b-1886-4949-999b-d94ad566ea13.png)

Fisheye to equirectangular converter written in RealBasic/XOJO

This is an experimental program (or if you prefer, a pre-alpha release), so use it at your own risk.

This program takes as input 1 or 2 images in fisheye/square/circular format and reproject them into equirectangular projection.

![Fisheye](https://github.com/jumpjack/fishconLC/blob/main/001-mini.jpg)

![Equirect](https://github.com/jumpjack/fishconLC/blob/main/001-pano1.jpg)
          
A "fisheye/square/circular" is an image with same width and height, containing the circular image representing the field of fiew of a fisheye lens.

FishconLC  relies on an external program called "FFMPEG", and makes use of its V360 filter to perform all calculations, being as a matter of fact just an interface to produce the needed parameters to use FFMPEG to convert from fisheye to equirectangular, using this command:

    ffmpeg -i input.jpg -y output.jpg -vf v360=fisheye:equirectangular:ih_fov=235:iv_fov=235:yaw=0:pitch=90:roll=0

 - h_fov and i_fov define the horizontal and vertical FOV of thew fisheye image;
 - yow, pitch and roll define the orientation of the camera

For double fisheye input (only horizontal) just change "fisheye" to "fisheye".

Experiment here:

https://ffmpeg.lav.io/


# Installation

- Download thw whole repo and unpack the zip file.
- Find the folder Builds\Fisheye2Equi.xml\Windows\Fisheye2Equi
- Copy [ffmpeg.exe](https://www.ffmpeg.org/) executable in the folder
- Launch Fisheye2Equi.exe executable
