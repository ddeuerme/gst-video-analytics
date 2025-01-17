# GStreamer Video Analytics Plugin

## Overview
<div align="center"><img src="intro.gif" width=900/></div>

This repository contains a collection of GStreamer elements to enable CNN model based video analytics capabilities (such as object detection, classification, recognition) in GStreamer framework. Example above shows concise GStreamer pipeline that runs detection & emotion classification with given models on given videofile:
```sh
gst-launch-1.0 filesrc location=cut.mp4 ! decodebin ! videoconvert ! gvadetect model=face-detection-adas-0001.xml ! gvaclassify model=emotions-recognition-retail-0003.xml model-proc=emotions-recognition-retail-0003.json ! gvawatermark ! ximagesink sync=false
```

The complete solution leverages
* Open source GStreamer framework for pipeline management
* GStreamer plugins for input and output such as media files and real-time streaming from camera or network
* Video decode and encode plugins, either CPU optimized plugins or GPU-accelerated plugins [based on VAAPI](https://github.com/GStreamer/gstreamer-vaapi)

and additionally installs the following Deep Learning specific elements from this repository
* Inference plugins leveraging [Intel OpenVINO](https://software.intel.com/en-us/openvino-toolkit) for high performance inference using CNN models
* Visualization of computer vision results (such as bounding boxes and labels of detected objects) on top of video stream

Here is a diagram how GVA plugin fits into common software stack:
<div align="center"><img src="https://user-images.githubusercontent.com/26006277/58497636-11285480-8185-11e9-80da-b812877bc898.png" width=900/></div>
In this diagram GVA plugin components are shown as light blue, the other Intel components are shown as dark blue,
standard GStreamer components are shown as grey, while Linux kernel is shown as green

## License
GStreamer Video Analytics Plugin is licensed under [MIT license](LICENSE).

## Prerequisites
### Hardware
* Refer to OpenVINO SDK for [hardware requirements for inference elements](https://software.intel.com/en-us/openvino-toolkit/hardware);
* On platforms with Intel Gen graphics, refer to gstreamer-vaapi for [HW accelerated video decode and encode requirements](https://github.com/GStreamer/gstreamer-vaapi).

### Software
* OpenVINO >= 2019 R1 (InferenceEngine 1.6.0)
* Linux* system with kernel >= 4.15
* GStreamer framework >= 1.14

## Getting Started
Links you may find useful:
* Extensive [Getting Started Guide](https://github.com/opencv/gst-video-analytics/wiki/Getting-Started-Guide-%5BR1.2%5D) (start here)
* [API reference](https://opencv.github.io/gst-video-analytics/)

## Samples
See [command-line examples](samples/shell) and [C++ example](samples/cpp/face_attributes)

## Reporting Bugs and Feature Requests
Bugs and requests can be reported [on Issues page](https://github.com/opencv/gst-video-analytics/issues)

## Usage and integration into application
### Pipelining and data flow
[More details](https://github.com/opencv/gst-video-analytics/wiki/Data-flow) about pipeline construction and data flow between pipeline elements

### Metadata
[More details](https://github.com/opencv/gst-video-analytics/wiki/Metadata) about metadata generated by inference plugins and attached to video frames

### Model preparation
[More details](https://github.com/opencv/gst-video-analytics/wiki/Model-preparation) how to prepare Tensorflow/Caffe and other models for usage in the inference plugins

### Plugins parameters
[Elements list](https://github.com/opencv/gst-video-analytics/wiki/Elements) and properties list per each element

## How to Contribute
If you have bug fix or an idea to improve the project, please first let us know and submit proposal description to [Issues page](https://github.com/opencv/gst-video-analytics/issues)
as at this stage of the project pull requests not monitored.

---
\* Other names and brands may be claimed as the property of others.
