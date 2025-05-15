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
 - yaw, pitch and roll define the orientation of the camera

For double fisheye input (only horizontal) just change "fisheye" to "dfisheye".

Experiment here:

https://ffmpeg.lav.io/


# Installation

- Download thw whole repo and unpack the zip file.
- Find the folder Builds\Fisheye2Equi.xml\Windows\Fisheye2Equi
- Copy [ffmpeg.exe](https://www.ffmpeg.org/) executable in the folder
- Launch Fisheye2Equi.exe executable

# Viewing results

Once you get an equirectangular image, you can view it as a spherical panorama using one of these sites:
- [https://renderstuff.com/tools/360-panorama-web-viewer/](https://renderstuff.com/tools/360-panorama-web-viewer/)
- [https://akokubo.github.io/ThetaViewer/demo2.html](https://akokubo.github.io/ThetaViewer/demo2.html)

# Further resources
- [My blog page about 360° photos, panoramas, fisheye,...](https://jumpjack.wordpress.com/2021/07/03/foto-3d-a-180-o-360-vr180-o-vr360/)

# Examples

Commandline for converting horizontal doble fisheye to equirectangular full sphere: 

- ffmpeg -i input.jpg -vf v360=dfisheye:e:ih_fov=210:iv_fov=210:pitch=5 -y output.jpg

Above command assumes the FOV of the two images is 210° horizontally and vertically, and that the camera was slightly pointing dowupn (5°) while taking the shot.
