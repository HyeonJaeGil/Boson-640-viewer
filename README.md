FLIR SYSTEMS, INC <BR>
2018-Nov <BR>
MIT License <BR>

# Boson 640 USB Viewer (Linux, support only 640x512)

## Description:

This is an example of capturing Boson Video (USB) using V4L2 (Video for Linux 2)
and OpenCV to display the video. Boson USB has two modes, AGC-8 bits and
RAW-16bits.

Video in 16 bits is not paintable so a linear transformation needs to happen
before displaying the image. We call this process AGC, and in this example we
use the most basic one (LINEAR). Then we use stardard call to paint in GREY.
Video is 8 bits is directly paintable, linear transformation happens inside the
 camera, not further actions need to happen in SW.

## How to use it:
```
 BosonUSB [t/f] [0..9]
        f<name> : record TIFFS in Folder <NAME>
        t<number> : number of frames to record
        [0..9]  : linux video port

./BosonUSB         ->  opens Boson640 /dev/video0  in RAW16 mode
./BosonUSB 1       ->  opens Boson640 /dev/video1  in RAW16 mode
./BosonUSB fcap -> creates a folder named 'cap' and inside TIFF files (raw16, agc) will be
located.
./BosonUSB fcap s10 -> creates a folder named 'cap' and inside TIFF files (raw16, agc) will be saved at 10 FPS.
./BosonUSB fcap t100 -> creates a folder named 'cap' and stores them as TIFF files (only captures 100 frames)		
```
## To compile

This SW uses some libraries as v4l2 and OpenCV, they need to be installed first in the PC.
They are not part of this package
```
mkdir build && cd build
cmake ..
make
```

## References and Credits (other than FLIR)

- http://jwhsmith.net/2014/12/capturing-a-webcam-stream-using-v4l2
- https://opencv.org
- https://en.wikipedia.org/wiki/Video4Linux
