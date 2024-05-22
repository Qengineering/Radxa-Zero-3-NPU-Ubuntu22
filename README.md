# Radxa Zero 3 NPU with Ubuntu 22.04
![output image]( https://qengineering.eu/github/RadxaZero3_GitHub.webp)<br/><br>
[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)<br/>

------------

## Installation.

- Get a 16 GB (minimal) SD card holding the image. 
- Download the `Radxa_Zero3_NPU_Ubuntu22.img.xz` image (3.3 GByte) from our [Sync](https://ln5.sync.com/dl/9c6592390/rsr2pb66-93y5zph6-nryj9bdt-aju7pfwf) site.
- Flash the image on the SD card with the [Imager](https://www.raspberrypi.org/software/) or [balenaEtcher](https://www.balena.io/etcher/).
- Insert the SD card in your Rock 5 and enjoy.
- Username: ***radxa***
- no password: ***radxa***
#### Showstopper. 
- The NPU only works on the 2 and 4 GB models.

------------

## Model performance benchmark(FPS)

All models, with C++ examples, can be found on the SD image.<br>

| demo             | model_name                   | inputs_shape            | dtype | Radxa Zero3|
| ---------------- | ---------------------------- | ----------------------- | ----- | ------------- |
| yolov5           | yolov5s_relu                 | [1, 3, 640, 640]        | INT8  | 14.8          |
|                  | yolov5n                      | [1, 3, 640, 640]        | INT8  | 19.5          |
|                  | yolov5s                      | [1, 3, 640, 640]        | INT8  | 11.7          |
|                  | yolov5m                      | [1, 3, 640, 640]        | INT8  | 5.7           |
| yolov6           | yolov6n                      | [1, 3, 640, 640]        | INT8  | 18.0          |
|                  | yolov6s                      | [1, 3, 640, 640]        | INT8  | 8.1           |
|                  | yolov6m                      | [1, 3, 640, 640]        | INT8  | 4.5           |
| yolov7           | yolov7-tiny                  | [1, 3, 640, 640]        | INT8  | 16.1          |
|                  | yolov7                       | [1, 3, 640, 640]        | INT8  | 3.4           |
| yolov8           | yolov8n                      | [1, 3, 640, 640]        | INT8  | 18.2          |
|                  | yolov8s                      | [1, 3, 640, 640]        | INT8  | 8.9           |
|                  | yolov8m                      | [1, 3, 640, 640]        | INT8  | 4.4           |
| yolox            | yolox_s                      | [1, 3, 640, 640]        | INT8  | 10.0          |
|                  | yolox_m                      | [1, 3, 640, 640]        | INT8  | 4.8           |
| ppyoloe          | ppyoloe_s                    | [1, 3, 640, 640]        | INT8  | 9.2           |
|                  | ppyoloe_m                    | [1, 3, 640, 640]        | INT8  | 5.0           |
| yolov5_seg       | yolov5n-seg                  | [1, 3, 640, 640]        | INT8  | 1.04          |
|                  | yolov5s-seg                  | [1, 3, 640, 640]        | INT8  | 0.87          |
|                  | yolov5m-seg                  | [1, 3, 640, 640]        | INT8  | 0.71          |
| yolov8_seg       | yolov8n-seg                  | [1, 3, 640, 640]        | INT8  | 0.91          |
|                  | yolov8s-seg                  | [1, 3, 640, 640]        | INT8  | 0.87          |
|                  | yolov8m-seg                  | [1, 3, 640, 640]        | INT8  | 0.7           |
| RetinaFace       | RetinaFace_mobile320         | [1, 3, 320, 320]        | INT8  | 88.5          |
|                  | RetinaFace_resnet50_320      | [1, 3, 320, 320]        | INT8  | 11.8          |
| PPOCR-Det        | ppocrv4_det                  | [1, 3, 480, 480]        | INT8  | 15.1          |
| PPOCR-Rec        | ppocrv4_rec                  | [1, 3, 48, 320]         | FP16  | 17.3          |

* Due to the pixel-wise filling and drawing, segmentation models are relatively slow

------------

## Cooling.

You must cool your Zero3. It will get very hot without a heatsink.<br>
We used a heatsink with two fans designed for the Raspberry Pi Zero, and it works fine.<br>
Even with the NPU running 24/7 at 1.8 GHz, it never gets warmer than 42°C (107°F).<br>


![output image]( https://qengineering.eu/github/RadxaZero3_Fan3.webp)<br/><br/>

Use the thermal pad properly.<br>
It should fill the space between the chip and the cooling element effectively.<br>
If there is any gap, the heat flow will not be optimal, resulting in a much hotter CPU.<br>
The delivered pad will come with two plastic protective sheets. These must be removed before applying the pad.<br>
If there is still a small gap (the CPU of the Radxa is slightly thinner than the Raspberry Pi), cut some small slices from the pad and stack them.<br>
The actual CPU core is located at the centre of the chip, where the heat is generated.<br><br>

![output image]( https://qengineering.eu/github/RadxaZero3_FanPad.webp)<br/><br/>

------------

## Tips.

* If you need extra space delete the opencv and the opencv_contrib folder from the SD card. They are no longer needed since all libraries are stored in the /usr/ directory.
* Use a tool like [GParted](https://gparted.org/) `sudo apt-get install gparted` to expand the image to larger SD cards. We recommend a minimum of 64 GB. Deep learning requires a lot of space.<br/>


------------

## Pre-installed frameworks.

- [OpenCV](https://qengineering.eu/deep-learning-with-opencv-on-raspberry-pi-4.html) 4.9.0
- [ncnn](https://qengineering.eu/install-ncnn-on-raspberry-pi-4.html) 20240410
- NPU [rknpu2](https://github.com/airockchip/rknn-toolkit2/tree/master/rknpu2) 1.5.2
- NPU [model zoo](https://github.com/airockchip/rknn_model_zoo) 2.0.0
- NPU [model zoo models](https://github.com/Qengineering/rknn_model_zoo) 2.0.0

------------

### Thanks.
A more than special thanks to [***Joshua Riek***](https://github.com/Joshua-Riek) for all the hard work on the Ubuntu OS.

------------

[![paypal](https://qengineering.eu/images/TipJarSmall4.png)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=CPZTM5BB3FCYL) <br><br>
![output image]( https://qengineering.eu/github/RadxaCover.webp)<br/><br>

