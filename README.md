# Clone YOLOv5 repository

!rm -rf yolov5

!git clone https://github.com/ultralytics/yolov5

%cd yolov5

Note:

!git reset --hard 886f1c03d839575afecb059accf74296fad395b6

Patched to work in CNN Mosquito Detection, 
Notebook adapted from "C:\Repositories\CNN-Mosquito-Detection\CNN Training\YOLOV5(Version-2)-YOLOv5.ipynb"

Temporarily public so I can clone from a Google Colab notebook.

If you are looking here, you probably <b>should</b> be looking at the original at https://github.com/ultralytics/yolov5

<hr></hr>

<a href="https://apps.apple.com/app/id1452689527" target="_blank">
<img src="https://user-images.githubusercontent.com/26833433/98699617-a1595a00-2377-11eb-8145-fc674eb9b1a7.jpg" width="1000"></a>
&nbsp

<a href="https://github.com/ultralytics/yolov5/actions"><img src="https://github.com/ultralytics/yolov5/workflows/CI%20CPU%20testing/badge.svg" alt="CI CPU testing"></a>

This repository represents Ultralytics open-source research into future object detection methods, and incorporates lessons learned and best practices evolved over thousands of hours of training and evolution on anonymized client datasets. **All code and models are under active development, and are subject to modification or deletion without notice.** Use at your own risk.

<img src="https://user-images.githubusercontent.com/26833433/103594689-455e0e00-4eae-11eb-9cdf-7d753e2ceeeb.png" width="1000">\*\* GPU Speed measures end-to-end time per image averaged over 5000 COCO val2017 images using a V100 GPU with batch size 32, and includes image preprocessing, PyTorch FP16 inference, postprocessing and NMS. EfficientDet data from [google/automl][1] at batch size 8.

- **January 5, 2021**: [v4.0 release][2]: nn.SiLU() activations, [Weights & Biases][3] logging, [PyTorch Hub][4] integration.
- **August 13, 2020**: [v3.0 release][5]: nn.Hardswish() activations, data autodownload, native AMP.
- **July 23, 2020**: [v2.0 release][6]: improved model definition, training and mAP.
- **June 22, 2020**: [PANet][7] updates: new heads, reduced parameters, improved speed and mAP [364fcfd][8].
- **June 19, 2020**: [FP16][9] as new default for smaller checkpoints and faster inference [d4c6674][10].


## Pretrained Checkpoints

| Model               | size | AP<sup>val</sup> | AP<sup>test</sup> | AP<sub>50</sub> | Speed<sub>V100</sub> | FPS<sub>V100</sub> || params | GFLOPS |
| ------------------- | ---- | ---------------- | ----------------- | --------------- | -------------------- | -------- | -------- | ------ | :----: |
| [YOLOv5s][11]       | 640  | 36.8             | 36.8              | 55.6            | **2.2ms**            | **455**            || 7.3M   | 17.0   |
| [YOLOv5m][12]       | 640  | 44.5             | 44.5              | 63.1            | 2.9ms                | 345                || 21.4M  | 51.3   |
| [YOLOv5l][13]       | 640  | 48.1             | 48.1              | 66.4            | 3.8ms                | 264                || 47.0M  | 115.4  |
| [YOLOv5x][14]       | 640  | **50.1**         | **50.1**          | **68.7**        | 6.0ms                | 167                || 87.7M  | 218.8  |
|                     |      |                  |                   |                 |                      |                    ||        |        |
| [YOLOv5x][15] + TTA | 832  | **51.9**         | **51.9**          | **69.6**        | 24.9ms               | 40                 || 87.7M  | 1005.3 |

\- 
| [YOLOv5l6][16]   |640 |49.0     |49.0     |67.4     |4.1ms     |244     ||77.2M  |117.7
| [YOLOv5l6][17]   |1280 |53.0     |53.0     |70.8     |12.3ms     |81     ||77.2M  |117.7
-

\*\* AP<sup>test</sup> denotes COCO [test-dev2017][18] server results, all other AP results denote val2017 accuracy.  
\*\* All AP numbers are for single-model single-scale without ensemble or TTA. **Reproduce mAP** by `python test.py --data coco.yaml --img 640 --conf 0.001 --iou 0.65`  
\*\* Speed<sub>GPU</sub> averaged over 5000 COCO val2017 images using a GCP [n1-standard-16][19] V100 instance, and includes image preprocessing, FP16 inference, postprocessing and NMS. NMS is 1-2ms/img.  **Reproduce speed** by `python test.py --data coco.yaml --img 640 --conf 0.25 --iou 0.45`  
\*\* All checkpoints are trained to 300 epochs with default settings and hyperparameters (no autoaugmentation). 
\*\* Test Time Augmentation ([TTA][20]) runs at 3 image sizes. **Reproduce TTA** by `python test.py --data coco.yaml --img 832 --iou 0.65 --augment` 


## Requirements

Python 3.8 or later with all [requirements.txt][21] dependencies installed, including `torch>=1.7`. To install run:
```bash
$ pip install -r requirements.txt
```


## Tutorials

* [Train Custom Data][22]&nbsp; 🚀 RECOMMENDED
* [Weights & Biases Logging][23]&nbsp; 🌟 NEW
* [Multi-GPU Training][24]
* [PyTorch Hub][25]&nbsp; ⭐ NEW
* [ONNX and TorchScript Export][26]
* [Test-Time Augmentation (TTA)][27]
* [Model Ensembling][28]
* [Model Pruning/Sparsity][29]
* [Hyperparameter Evolution][30]
* [Transfer Learning with Frozen Layers][31]&nbsp; ⭐ NEW
* [TensorRT Deployment][32]


## Environments

YOLOv5 may be run in any of the following up-to-date verified environments (with all dependencies including [CUDA][33]/[CUDNN][34], [Python][35] and [PyTorch][36] preinstalled):

- **Google Colab and Kaggle** notebooks with free GPU: <a href="https://colab.research.google.com/github/ultralytics/yolov5/blob/master/tutorial.ipynb"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a> <a href="https://www.kaggle.com/ultralytics/yolov5"><img src="https://kaggle.com/static/images/open-in-kaggle.svg" alt="Open In Kaggle"></a>
- **Google Cloud** Deep Learning VM. See [GCP Quickstart Guide][37]
- **Amazon** Deep Learning AMI. See [AWS Quickstart Guide][38]
- **Docker Image**. See [Docker Quickstart Guide][39] <a href="https://hub.docker.com/r/ultralytics/yolov5"><img src="https://img.shields.io/docker/pulls/ultralytics/yolov5?logo=docker" alt="Docker Pulls"></a>


## Inference

detect.py runs inference on a variety of sources, downloading models automatically from the [latest YOLOv5 release][40] and saving results to `runs/detect`.
```bash
$ python detect.py --source 0  # webcam
                            file.jpg  # image 
                            file.mp4  # video
                            path/  # directory
                            path/*.jpg  # glob
                            rtsp://170.93.143.139/rtplive/470011e600ef003a004ee33696235daa  # rtsp stream
                            rtmp://192.168.1.105/live/test  # rtmp stream
                            http://112.50.243.8/PLTV/88888888/224/3221225900/1.m3u8  # http stream
```

To run inference on example images in `data/images`:
```bash
$ python detect.py --source data/images --weights yolov5s.pt --conf 0.25

Namespace(agnostic_nms=False, augment=False, classes=None, conf_thres=0.25, device='', exist_ok=False, img_size=640, iou_thres=0.45, name='exp', project='runs/detect', save_conf=False, save_txt=False, source='data/images/', update=False, view_img=False, weights=['yolov5s.pt'])
YOLOv5 v4.0-96-g83dc1b4 torch 1.7.0+cu101 CUDA:0 (Tesla V100-SXM2-16GB, 16160.5MB)

Fusing layers... 
Model Summary: 224 layers, 7266973 parameters, 0 gradients, 17.0 GFLOPS
image 1/2 /content/yolov5/data/images/bus.jpg: 640x480 4 persons, 1 bus, Done. (0.010s)
image 2/2 /content/yolov5/data/images/zidane.jpg: 384x640 2 persons, 1 tie, Done. (0.011s)
Results saved to runs/detect/exp2
Done. (0.103s)
```
<img src="https://user-images.githubusercontent.com/26833433/97107365-685a8d80-16c7-11eb-8c2e-83aac701d8b9.jpeg" width="500">  

### PyTorch Hub

To run **batched inference** with YOLOv5 and [PyTorch Hub][41]:
```python
import torch

# Model
model = torch.hub.load('ultralytics/yolov5', 'yolov5s', pretrained=True)

# Images
dir = 'https://github.com/ultralytics/yolov5/raw/master/data/images/'
imgs = [dir + f for f in ('zidane.jpg', 'bus.jpg')]  # batched list of images

# Inference
results = model(imgs)
results.print()  # or .show(), .save()
```


## Training

Run commands below to reproduce results on [COCO][42] dataset (dataset auto-downloads on first use). Training times for YOLOv5s/m/l/x are 2/4/6/8 days on a single V100 (multi-GPU times faster). Use the largest `--batch-size` your GPU allows (batch sizes shown for 16 GB devices).
```bash
$ python train.py --data coco.yaml --cfg yolov5s.yaml --weights '' --batch-size 64
                                         yolov5m                                40
                                         yolov5l                                24
                                         yolov5x                                16
```
<img src="https://user-images.githubusercontent.com/26833433/90222759-949d8800-ddc1-11ea-9fa1-1c97eed2b963.png" width="900">


## Citation

[![DOI][image-1]][43]


## About Us

Ultralytics is a U.S.-based particle physics and AI startup with over 6 years of expertise supporting government, academic and business clients. We offer a wide range of vision AI services, spanning from simple expert advice up to delivery of fully customized, end-to-end production solutions, including:
- **Cloud-based AI** systems operating on **hundreds of HD video streams in realtime.**
- **Edge AI** integrated into custom iOS and Android apps for realtime **30 FPS video inference.**
- **Custom data training**, hyperparameter evolution, and model exportation to any destination.

For business inquiries and professional support requests please visit us at https://www.ultralytics.com. 


## Contact

**Issues should be raised directly in the repository.** For business inquiries or professional support requests please visit https://www.ultralytics.com or email Glenn Jocher at glenn.jocher@ultralytics.com. 

[1]:	https://github.com/google/automl
[2]:	https://github.com/ultralytics/yolov5/releases/tag/v4.0
[3]:	https://wandb.ai/
[4]:	https://pytorch.org/hub/ultralytics_yolov5/
[5]:	https://github.com/ultralytics/yolov5/releases/tag/v3.0
[6]:	https://github.com/ultralytics/yolov5/releases/tag/v2.0
[7]:	https://arxiv.org/abs/1803.01534
[8]:	https://github.com/ultralytics/yolov5/commit/364fcfd7dba53f46edd4f04c037a039c0a287972
[9]:	https://pytorch.org/docs/stable/nn.html#torch.nn.Module.half
[10]:	https://github.com/ultralytics/yolov5/commit/d4c6674c98e19df4c40e33a777610a18d1961145
[11]:	https://github.com/ultralytics/yolov5/releases
[12]:	https://github.com/ultralytics/yolov5/releases
[13]:	https://github.com/ultralytics/yolov5/releases
[14]:	https://github.com/ultralytics/yolov5/releases
[15]:	https://github.com/ultralytics/yolov5/releases
[16]:	https://github.com/ultralytics/yolov5/releases
[17]:	https://github.com/ultralytics/yolov5/releases
[18]:	http://cocodataset.org/#upload
[19]:	https://cloud.google.com/compute/docs/machine-types#n1_standard_machine_types
[20]:	https://github.com/ultralytics/yolov5/issues/303
[21]:	https://github.com/ultralytics/yolov5/blob/master/requirements.txt
[22]:	https://github.com/ultralytics/yolov5/wiki/Train-Custom-Data
[23]:	https://github.com/ultralytics/yolov5/issues/1289
[24]:	https://github.com/ultralytics/yolov5/issues/475
[25]:	https://github.com/ultralytics/yolov5/issues/36
[26]:	https://github.com/ultralytics/yolov5/issues/251
[27]:	https://github.com/ultralytics/yolov5/issues/303
[28]:	https://github.com/ultralytics/yolov5/issues/318
[29]:	https://github.com/ultralytics/yolov5/issues/304
[30]:	https://github.com/ultralytics/yolov5/issues/607
[31]:	https://github.com/ultralytics/yolov5/issues/1314
[32]:	https://github.com/wang-xinyu/tensorrtx
[33]:	https://developer.nvidia.com/cuda
[34]:	https://developer.nvidia.com/cudnn
[35]:	https://www.python.org/
[36]:	https://pytorch.org/
[37]:	https://github.com/ultralytics/yolov5/wiki/GCP-Quickstart
[38]:	https://github.com/ultralytics/yolov5/wiki/AWS-Quickstart
[39]:	https://github.com/ultralytics/yolov5/wiki/Docker-Quickstart
[40]:	https://github.com/ultralytics/yolov5/releases
[41]:	https://github.com/ultralytics/yolov5/issues/36
[42]:	https://github.com/ultralytics/yolov5/blob/master/data/scripts/get_coco.sh
[43]:	https://zenodo.org/badge/latestdoi/264818686

[image-1]:	https://zenodo.org/badge/264818686.svg