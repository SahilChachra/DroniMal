<h1 align="center">DroniMal</h1>

## :star: Introduction
DroniMal is an intelligent video analytics pipeline powered by Nvidia's Jetson nano and DeepStream. This application aims to help those who work day in and day out to save animals from being poached. Every year, on an average, 38 million animals are being poached resulting in many species almost near to extinction or they now come under endangered species.<br><br>
African elephants are few such animals which are being poached the most and hence fall under Endangered species as per IUCN (International Union for Conservation of Nature) Red List. Even giraffes have become vulnerable and come under high risk of extinction by IUCN. Hence, DroniMal helps keep an eye on elephants and giraffes, help monitor their movement in the wild and also monitor their migration to protect them in every way possible. DroniMal would be best fit when used in wild where we would expect only animals and no human/human object. Hence, DroniMal can detect vehicles too, indicating danger to the wild animals.<br><br>
Such applications can help all the wildlife enthusiasts to keep an eye and protect their lovely animals in the wild. <br><br>
Currently the demo shown, fetches 4 input streams locally and performs detection parallely. On an average, we get 4 FPS per stream. The model used is YoloV5s V6 which was then converted to TensorRT engine. Then the TensorRT engine was used to perform inference using Nvidia's DeepStream. The device used for the demos is Nvidia's Jetson Nano B01.<br><br>
Please checkout references for link of the dataset.

## :framed_picture: Screenshots

<center>
    <h3>Jetson Nano's resource utilization while running DeepStream</h2>
    <img src="https://github.com/SahilChachra/Wildlife-rescuer/blob/main/assets/jtop_ss_1.png" style="width:90%;height:90%;">
    <h3>FPS while running DeepStream with 4 input streams</h3>
    <img src="https://github.com/SahilChachra/Wildlife-rescuer/blob/main/assets/deepstream_fps.jpg" style="width:70%;height:70%;">
</center>

Demo Link : [YouTube](https://youtu.be/Q_W8RClvQXg)

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

<center>
    <img src="https://github.com/SahilChachra/Wildlife-rescuer/blob/main/assets/nano.jpeg" style="width:70%;height:70%;">
</center>

## :dizzy: References
Dataset : [Lila - Conservation Drones](https://lila.science/datasets/conservationdrones) <br>
Object detection model : [YoloV5](https://github.com/ultralytics/yolov5) <br>
TensorRT : [YoloV5](https://github.com/wang-xinyu/tensorrtx/tree/master/yolov5) <br>
DeepStream : [5.1](https://docs.nvidia.com/metropolis/deepstream/5.1/dev-guide/index.html) <br>

## :fireworks: Extras

This work can be extended by adding more classes to detect. One can also add tracking mechanism to help track the objects across multiple videos. Further more, a Jetson nano can be mounted on the drone and can help perform video analytics live!
