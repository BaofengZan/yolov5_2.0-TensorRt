# yolov5

The Pytorch implementation is [ultralytics/yolov5](https://github.com/ultralytics/yolov5).

I was using [ultralytics/yolov5](https://github.com/ultralytics/yolov5)(The latest version). Just in case the yolov5 model updated.

## How to Run

```
1. generate yolov5l.wts from pytorch implementation with yolov5.pt

git clone https://github.com/AIpakchoi/yolov5_tensorrt.git
git clone https://github.com/ultralytics/yolov5.git
// download its weights 'yolov5l.pt'
cd yolov5
cp ../yolov5_tensorrt/yolov5l/gen_wts.py .
python gen_wts.py
// a file 'yolov5l.wts' will be generated.

2. put yolov5l.wts into yolov5l, build and run

mv yolov5l.wts ../yolov5_tensorrt/yolov5l/
cd ../yolov5_tensorrt/yolov5l
mkdir build
cd build
cmake ..
make
sudo ./yolov5l -s             // serialize model to plan file i.e. 'yolov5l.engine'
sudo ./yolov5l -d  ../samples // deserialize plan file and run inference, the images in samples will be processed.

3. check the images generated, as follows. _zidane.jpg and _bus.jpg
```

<p align="center">
<img src="https://user-images.githubusercontent.com/15235574/78247927-4d9fac00-751e-11ea-8b1b-704a0aeb3fcf.jpg">
</p>

<p align="center">
<img src="https://user-images.githubusercontent.com/15235574/78247970-60b27c00-751e-11ea-88df-41473fed4823.jpg">
</p>

## Config

- Input shape defined in yololayer.h
- Number of classes defined in yololayer.h
- FP16/FP32 can be selected by the macro in yolov5l.cpp
- GPU id can be selected by the macro in yolov5l.cpp
- NMS thresh in yolov5l.cpp
- BBox confidence thresh in yolov5l.cpp
- Batch size in yolov5l.cpp
