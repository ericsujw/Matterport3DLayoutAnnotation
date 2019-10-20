# Matterport3D Layout Annotation

This is the layout annotation dataset of the Matterport3D used in our paper "[3D Manhattan Room Layout Reconstruction from a Single 360 Image](http://arxiv.org/abs/1910.04099)".

## Pre-processing
We would not provide the panorama images in this repo but you could follow the steps below to get the same panorama as ours.
* **Panorama Image Generation**: Please follow the instruction of the [PanoBasic](https://github.com/yindaz/PanoBasic) to stitch the skybox images of the Matterport3D into the equirectangular panorama.
* **Manhattan Alignment**: The panorama should be already aligned with the Manhattan World, then our annotation could perfectly algin with the images. We recommand you using the [alignment tool](https://github.com/SunDaDenny/PanoAnnotator#pre-process) provided by [PanoBasic](https://github.com/yindaz/PanoBasic).

## Data
* **Data List**: We select out 2295 panoramas form original Matterport3D dataset and split out the [train](data_list/mp3d_train.txt)/[val](data_list/mp3d_val.txt)/[test](data_list/mp3d_test.txt) lists used in our paper.
* **Data Structure**: We follow the data structure using in the [DuLa-Net](https://github.com/SunDaDenny/DuLa-Net) and [PanoAnnotator](https://github.com/SunDaDenny/PanoAnnotator). You could refer to these two repo to get more information.
* **File Name**: We zip all the annotation file in the [label_data.zip](label_data.zip). The labeling files' naming rule is following the `<dir1>_<dir2>_label.json` format that is same to the Matterport3D's folder structure.

## License

The data is released under the [Matterport3D Terms of Use](http://kaldir.vc.in.tum.de/matterport/MP_TOS.pdf), and the code is released under the MIT license.
