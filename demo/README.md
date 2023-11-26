# Demo Usage

Currently the demo supports visualization for:
- Image Folder: A set of frames that were decoded from a given video.
- Video: I only tested `.mp4`, but other video format should be OK.

## Inference on a image folder

The command line should be like this:
```shell
    python demo/demo.py ${METHOD} ${CONFIG_FILE} ${CHECKPOINT_FILE} [--visualize-path ${IMAGE-FOLDER}] [--suffix ${IMAGE_SUFFIX}][--output-folder ${FOLDER}] [--output-video]
``` 
Example BASE Approach:
```shell
    python demo/demo.py base configs/vid_R_101_C4_1x.yaml R_101.pth --suffix ".JPEG"\
        --visualize-path datasets/image_folder \
        --output-folder visualization --output-video
```
Example MEGA Approach:
```shell
    python demo/demo.py mega configs/MEGA/vid_R_101_C4_MEGA_1x.yaml MEGA_R_101.pth --suffix ".JPEG"\
        --visualize-path datasets/image_folder \
        --output-folder visualization --output-video
```
This will generate visualization result using single frame baseline or MEGA method with ResNet-101 backbone. And the results, images with generated bboxes, are saved in folder `visualization`. 

Please note that:
1) If your want to use other methods like MEGA, FGFA, please change METHOD `base` to `mega` or `fgfa`. Currently all methods support visualization, see [`demo.py`](demo.py) for more information about using other methods.
2) Don't forget to modify CONFIG_FILE and CHECKPOINT_FILE accordingly!
3) Add `--output-video` to generate video instead of set of images, the video is encoded at `25` fps by default.
4) If you want to visualize your own image folder, please make sure that the name of your images is like `XXXXXX.jpg`. `XXXXXX` is the frame number of current frame, e.g., `000000` is the first frame. `.jpg` could be replaced by other common image suffix like `.png`, which could be specified by `--suffix.`

## Inference on a video

The command line should be like this:
```shell
    python demo/demo.py ${METHOD} ${CONFIG_FILE} ${CHECKPOINT_FILE} --video [--visualize-path ${VIDEO-NAME}] [--output-folder ${FOLDER}] [--output-video]
``` 
Example:
```shell
    python demo/demo.py mega configs/MEGA/vid_R_101_C4_MEGA_1x.yaml MEGA_R_101.pth --video \
        --visualize-path datasets/v_WalkingWithDog_g10_c03.avi --output-folder visualization/videos/WalkingDog_g10/mega --output-video\
```
This will generate visualization result using MEGA method with ResNet-101 backbone. And the results, images with generated bboxes, are saved in folder `visualization`. 

Please note that:
1) Among the pre-trained models, in addition to changing the model type, you can also use a different backbone type, as shown in the Main Results table in the README.md.
