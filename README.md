<h1 align="center">Project Title</h1>

## :star: Introduction
X application is an intelligent video analytics pipeline powered by DeepStream and Nvidia jetson nano. This application aims to help those who work day in and day out to save animals from being poached. Poaching is increasing everyday and it's getting worse with time. Very soon more animals will come under the endagered list! This app help rescuers monitor movement of the animals at night and detect poachers or their vehicle.

## :framed_picture: Screenshots

<center>
    <h3>Jetson Nano's resource utilization while running DeepStream</h2>
    <img src="https://github.com/SahilChachra/Wildlife-rescuer/blob/main/assests/jtop_ss_1.png" style="width:90%;height:90%;">
    <h3>FPS while running DeepStream with 4 input streams</h3>
    <img src="https://github.com/SahilChachra/Wildlife-rescuer/blob/main/assests/deepstream_fps.jpg" style="width:70%;height:70%;">
</center>

## :hammer_and_wrench: Installing requirements and running the repo
We will be using Jetpack 4.5 and <b>NOT</b> Jetpack 4.6 (has TensorRT 7) as 4.5 comes with TensorRT 6 which is supported by current implementation of YoloV5 models.
<ol>
    <li>Set up your Jetson by following the steps here :  <a href="https://developer.nvidia.com/jetpack-sdk-451-archive">Installing Jetpack</a></li>
    <li>Increase swap size : <a href="https://www.youtube.com/watch?v=uvU8AXY1170">Video</a></li>
    <li>To install DeepStream, follow this <a href="https://docs.nvidia.com/metropolis/deepstream/5.1/dev-guide/text/DS_Quickstart.html#jetson-setup">documentation</a></li>
    <li>Now, clone this repo and paste it in deepstream/sources : <b><i>cp -r ./deepstream_yolo_wildlife /opt/nvidia/deepstream/deepstream-5.1/sources/</b></i></li>
    <li>Run this to compile the lib : <b><i>CUDA_VER=10.2 make -C nvdsinfer_custom_impl_Yolo</b></i></li>
    <li>Now, inside deepstream_yolo_wildlife, run this command <b><i>deepstream-app -c deepstream_app_config.txt</b></i>
</ol>

If you are interested in converting your custom trained YoloV5 model to TensorRT and run it using DeepStream, follow [this](https://sahilchachra.medium.com/run-yolov5s-with-tensorrt-and-deepstream-on-nvidia-jetson-nano-8c888a2f0eae) blog to DIY.

## :dizzy: References
Dataset : [Lila - Conservation Drones](https://lila.science/datasets/conservationdrones) <br>
Object detection model : [YoloV5](https://github.com/ultralytics/yolov5) <br>
TensorRT : [YoloV5](https://github.com/wang-xinyu/tensorrtx/tree/master/yolov5) <br>
DeepStream : [5.1](https://docs.nvidia.com/metropolis/deepstream/5.1/dev-guide/index.html) <br>

## :hammer_and_wrench: Extras

This work can be extended by adding more classes to detect. One can also add tracking mechanism to help track the objects across multiple videos. Further more, a Jetson nano can be mounted on the drone and can help perform video analytics live!
