# MEGA for Video Object Detection

[![License](https://img.shields.io/badge/license-BSD-blue.svg)](LICENSE)
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/memory-enhanced-global-local-aggregation-for/video-object-detection-on-imagenet-vid)](https://paperswithcode.com/sota/video-object-detection-on-imagenet-vid?p=memory-enhanced-global-local-aggregation-for)

By [Yihong Chen](https://scalsol.github.io), [Yue Cao](http://yue-cao.me), [Han Hu](https://ancientmooner.github.io/), [Liwei Wang](http://www.liweiwang-pku.com/).

This repo is an official implementation of ["Memory Enhanced Global-Local Aggregation for Video Object Detection"](https://arxiv.org/abs/2003.12063), accepted by CVPR 2020. This repository contains a PyTorch implementation of our approach MEGA based on [maskrcnn_benchmark](https://github.com/facebookresearch/maskrcnn-benchmark), as well as some training scripts to reproduce the results on ImageNet VID reported in our paper. 

Besides, this repository also implements several other algorithms like [FGFA](http://openaccess.thecvf.com/content_iccv_2017/html/Zhu_Flow-Guided_Feature_Aggregation_ICCV_2017_paper.html) and [RDN](https://arxiv.org/abs/1908.09511). Any new methods are welcomed. Hoping for your pull request! We hope this repository would help further research in the field of video object detection and beyond. :)

## Citing MEGA
Please cite our paper in your publications if it helps your research:
```
@inproceedings{chen20mega,
    Author = {Chen, Yihong and Cao, Yue and Hu, Han and Wang, Liwei},
    Title = {Memory Enhanced Global-Local Aggregation for Video Object Detection},
    Conference = {CVPR},
    Year = {2020}
}
```

## Updates

- Add motion-IoU specific AP evaluation code. Only available for ImageNet VID dataset. (19/06/2020)
- Demo for visualization added (Support image folder and video). (17/06/2020)
- Results of ResNet-50 backbone added. (13/04/2020)
- Code and pretrained weights for [Deep Feature Flow](https://arxiv.org/abs/1611.07715) released. (30/03/2020)

## Main Results

Pretrained models are now available at [Baidu](https://pan.baidu.com/s/1qjIAD3ohaJO8EF1mZ4nLEg) (code: neck) and Google Drive.

Model | Backbone | AP50 | AP (fast) | AP (med) | AP (slow) | Link
:---: | :---: | :---: | :---: | :---: | :---: |:---:
single frame baseline | ResNet-101 | 76.7 | 52.3 | 74.1 | 84.9 | [Google](https://drive.google.com/file/d/1W17f9GC60rHU47lUeOEfU--Ra-LTw3Tq/view?usp=sharing)
DFF | ResNet-101 | 75.0 | 48.3 | 73.5 | 84.5 | [Google](https://drive.google.com/file/d/1Dn_RQRlA7z2XkRRS4XERUW_UH9jlNvMo/view?usp=sharing)
FGFA | ResNet-101 | 78.0 | 55.3 | 76.9 | 85.6 | [Google](https://drive.google.com/file/d/1yVgy7_ff1xVD1SooqbcK-OzKMgPpUcg4/view?usp=sharing)
RDN-base | ResNet-101 | 81.1 | 60.2 | 79.4 | 87.7 | [Google](https://drive.google.com/file/d/1jM5LqlVtCGjKH-MocTCjzFIVjqCyng8M/view?usp=sharing)
RDN | ResNet-101 | 81.7 | 59.5 | 80.0 | 89.0| [Google](https://drive.google.com/file/d/1FgoOwj-GFAMVn2hkSFKnxn5fKWPSxlUF/view?usp=sharing)
**MEGA** | ResNet-101 | 82.9 | 62.7| 81.6 | 89.4 | [Google](https://drive.google.com/file/d/1ZnAdFafF1vW9Lnpw-RPF1AD_csw61lBY/view?usp=sharing)

Model | Backbone | AP50 | AP (fast) | AP (med) | AP (slow) | Link
:---: | :---: | :---: | :---: | :---: | :---: |:---:
single frame baseline | ResNet-50 | 71.8 | 47.2 | 69.2 | 80.6| [Google](https://drive.google.com/file/d/1i39MwpP46x61eHLkRXMzcKhpeKZhkgA6/view?usp=sharing)
DFF | ResNet-50 | 70.4 | 43.6 | 68.9 | 80.8 | [Google](https://drive.google.com/file/d/1wl9Sheg46ecJOWzl1Uy4BWaCDRtSt51_/view?usp=sharing)
FGFA | ResNet-50 | 74.3 | 50.6 | 72.3 | 84.0|  [Google](https://drive.google.com/file/d/1nJ6CbUG_wW_gvMs193b7f0c1QLnXqAzO/view?usp=sharing)
RDN-base | ResNet-50 | 76.7 | 53.8 | 74.8 | 85.4 | [Google](https://drive.google.com/file/d/10k70lzSrxXiLWYx8tmX3RNuOQ2x1X0k8/view?usp=sharing)
**MEGA** | ResNet-50 | 77.3 | 56.5 | 75.7 | 85.2 | [Google](https://drive.google.com/file/d/1EZzpBuCfI75bsd_gxK1495tXlh0K_34H/view?usp=sharing)

**Note**: The performance of ResNet-50 backbone are not so stable.

**Note**: The motion-IoU specific AP evaluation code is a bit different from the original implementation in FGFA. I think the original implementation is really weird so I modify it. So the results may not be directly comparable with the results provided in FGFA and other methods that use MXNet version evaluation code. But we could tell which method is relatively better under the same evaluation protocol. 

## Installation

Please follow [INSTALL.md](INSTALL.md) for installation instructions.

## Data preparation

Please download LAB2-Session1-Additional material from Moodle. Then unzip the file in dataset folder. The path should look like this : 

    ./mega.pytorch/datasets/image_folder

### Demo Usage
Please follow [demo/README.md](demo/README.md) to see how to visualize your own images or video.
