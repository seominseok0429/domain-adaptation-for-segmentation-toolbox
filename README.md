# domain-adaptation-for-segmentation-toolbox

domain adaptation for segmentation toolbox(Pytorch) - deeplabev2, adaptsegnet...etc

This code is heavily borrowed from [Pytorch-Deeplab](https://github.com/speedinghzl/Pytorch-Deeplab).

This code is heavily borrowed from [Adaptsegnet](https://github.com/wasidennis/AdaptSegNet).

## Dataset

* Download the [GTA5 Dataset](https://download.visinf.tu-darmstadt.de/data/from_games/) as the source domain.
* Download the [Cityscapes Dataset](https://www.cityscapes-dataset.com/) as the target domain.

```
Data\
    Cityscapes\
        gtFine\
        gtFine_trainvaltest\
        leftImg8bit\
        meta\
    GTA5\
        images\
        labels\
``` 
## Training and Testing script

### GTA Only
```
python train_GTA_only.py --snapshot-dir ./snapshots/GTA2Cityscapes_single \
                                     --lambda-seg 0.0 \
                                     --lambda-adv-target1 0.0 --lambda-adv-target2 0.001


python evaluate_cityscapes.py --restore-from ./snapshots/GTA2Cityscapes_single/GTA5_95000.pth


python compute_iou.py ./data/Cityscapes/gtFine/val result/cityscapes
```

### AdaptSegNet
```
python train_gta2cityscapes_multi.py --snapshot-dir ./snapshots/GTA2Cityscapes_single \
                                     --lambda-seg 0.0 \
                                     --lambda-adv-target1 0.0 --lambda-adv-target2 0.001


python evaluate_cityscapes.py --restore-from ./snapshots/GTA2Cityscapes_single/GTA5_115000.pth


python compute_iou.py ./data/Cityscapes/gtFine/val result/cityscapes
```

### Cityscapes Only
```
python train_cityscapes_only.py

python evaluate_cityscapes.py --restore-from ./snapshots/GTA2Cityscapes_single/Cityscapes_95000.pth

python compute_iou.py ./data/Cityscapes/gtFine/val result/cityscapes
```


## Reslut

| Method | road | sidewalk | building | wall | fence | pole | light | sign | vegetation | terrain | sky | person | rider | car | truck | bus | train | motocycle | bicycle | mIoU |
|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|
| DeepLabV2-GTA5 | 85.28 | 20.23 | 69.0 | 21.0 | 14.13 | 22.36 | 31.83 | 15.74 | 65.21 | 19.79 | 68.5 | 55.28 | 26.24 | 72.13 | 25.74 | 32.48 | 1.34 | 29.35 | 38.11 | 37.57 |
| AdaptSegNet | 86.49 | 24.52 | 81.14 | 24.59 | 23.74 | 29.02 | 35.7 | 25.43 | 83.46 | 33.03 | 76.06 | 57.88 | 29.41 | 78.87 | 30.45 | 26.57 | 2.74 | 28.89 | 19.08 | 41.95 |
| DeepLabV2-cityscapes | 96.29 | 75.58 | 87.79 | 38.07 | 39.63 | 43.46 | 46.63 | 62.81 | 88.24 | 52.41 | 89.53 | 69.73 | 49.5 | 91.49 | 66.23 | 69.76 | 45.01 | 49.08 | 65.16 | 64.55 |


