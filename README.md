# domain-adaptation-for-segmentation-toolbox

domain adaptation for segmentation toolbox(Pytorch) - deeplabev2, adaptsegnet...etc

This code is heavily borrowed from [Pytorch-Deeplab](https://github.com/speedinghzl/Pytorch-Deeplab).

This code is heavily borrowed from [Adaptsegnet](https://github.com/wasidennis/AdaptSegNet).

# Dataset path

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

## Reslut

| Method | road | sidewalk | building | wall | fence | pole | light | sign | vegetation | terrain | sky | person | rider | car | truck | bus | train | motocycle | bicycle | mIoU |
|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|
| DeepLabV2-baseline | 85.28 | 20.23 | 69.0 | 21.0 | 14.13 | 22.36 | 31.83 | 15.74 | 65.21 | 19.79 | 68.5 | 55.28 | 26.24 | 72.13 | 25.74 | 32.48 | 1.34 | 29.35 | 38.11 | 37.57 |
