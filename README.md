# Matterport3D Layout Annotation

This is the layout annotation dataset of the Matterport3D used in our paper "[3D Manhattan Room Layout Reconstruction from a Single 360 Image](http://arxiv.org/abs/1910.04099)".

## Pre-processing
You could follow the steps below to get the same panorama as ours.
1. **Matterport3D**: Download all the data from [Matterport3D](https://github.com/niessner/Matterport).
2. **Panorama Image Generation**: Please follow the instruction of the [PanoBasic](https://github.com/yindaz/PanoBasic/blob/master/demo_matterport.m#L44) to stitch the skybox images of the Matterport3D into the equirectangular panorama.
3. **Manhattan Alignment**: The panorama should be already aligned with the Manhattan World, then our annotation could perfectly algin with the images. We recommand you using the [alignment tool](https://github.com/SunDaDenny/PanoAnnotator#pre-process) provided by [PanoBasic](https://github.com/yindaz/PanoBasic).

## Data
* **Data List**: We select out 2295 panoramas form original Matterport3D dataset and split out the [train](data_list/mp3d_train.txt)/[val](data_list/mp3d_val.txt)/[test](data_list/mp3d_test.txt) lists used in our paper.
* **Data Structure**: We follow the data structure using in the [DuLa-Net](https://github.com/SunDaDenny/DuLa-Net) and [PanoAnnotator](https://github.com/SunDaDenny/PanoAnnotator). You could refer to these two repo to get more information. We've aligned all the label to camera height is equal to 1.6m and json file structure should be similar as follow:
```javascript
{
    "cameraHeight": 1.6, // distance between camera and floor
    "layoutHeight": 2.9809624004364013, // distance between floor and ceiling
    "layoutObj2ds": { // door or window labeling block
        "num": 0,
        "obj2ds": []
    },
    "layoutPoints": { // corner labeling block, we only annotate the corner in the horizontal direction because you can easily get the corner in the vertical direction from cameraHeight and layoutHeight.
        "num": 6, // corner number in the horizontal direction
        "points": [ // List of the corner
            {
                "coords": [ // uv coordintate of the corner on the panorama
                    0.7081447345651483, // u coordintate of the corner on the panorama
                    0.5 // v coordintate of the corner on the panorama. We annotate on horizon line, then calculate the vertical position by cameraHeight and layoutHeight.
                ],
                "id": 0, // id number
                "xyz": [ // project the corner on to the 3D coordinate 
                    3.0078125, // x value
                    0.0, // y value
                    -0.8097623087756155 // z value
                ]
            },
            {...}
        ]
    },
    "layoutWalls": { // layout walls represented by plane equation
        "num": 6, // wall number
        "walls": [ // list of wall
            {
                "id": 0, // id number
                "normal": [ // plane equation's normal
                    1.0,
                    0.0,
                    -0.0
                ],
                "planeEquation": [ // plane equation
                    1.0, // a
                    0.0, // b
                    -0.0, // c
                    -3.0078125 // d
                ],
                "pointsIdx": [ // which two points construct this wall
                    0,
                    1
                ],
                "width": 2.8476272687756152 // the wall width
            },
            {...}
        ]
    },
    "panoId": "nothing" // a simple ID of panorama
}
```
* **File Name**: We zip all the annotation file in the [label_data.zip](label_data.zip). The labeling files' naming rule is following the `<dir1>_<dir2>_label.json` format that is same to the Matterport3D's folder structure.

## Citation
If you use this dataset for your research, please cite our paper.

## License

The data is released under the [Matterport3D Terms of Use](http://kaldir.vc.in.tum.de/matterport/MP_TOS.pdf), and the code is released under the MIT license. By using this dataset, you agree to all the terms in the [Matterport3D Terms of Use](http://kaldir.vc.in.tum.de/matterport/MP_TOS.pdf).
