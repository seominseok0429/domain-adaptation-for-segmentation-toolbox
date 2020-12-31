# domain-adaptation-for-segmentation-toolbox

domain adaptation for segmentation toolbox(Pytorch) - deeplabev2, adaptsegnet...etc

This code is heavily borrowed from [Pytorch-Deeplab](https://github.com/speedinghzl/Pytorch-Deeplab).

This code is heavily borrowed from [Adaptsegnet](https://github.com/wasidennis/AdaptSegNet).


## Training and Testing script

```
python train_gta2cityscapes_multi.py --snapshot-dir ./snapshots/GTA2Cityscapes_single \
                                     --lambda-seg 0.0 \
                                     --lambda-adv-target1 0.0 --lambda-adv-target2 0.001


python evaluate_cityscapes.py --restore-from ./snapshots/GTA2Cityscapes_single/GTA5_95000.pth


python compute_iou.py ./data/Cityscapes/gtFine/val result/cityscapes
```

===>road:	85.28
===>sidewalk:	20.23
===>building:	69.0
===>wall:	21.0
===>fence:	14.13
===>pole:	22.36
===>light:	31.83
===>sign:	15.74
===>vegetation:	65.21
===>terrain:	19.79
===>sky:	68.5
===>person:	55.28
===>rider:	26.24
===>car:	72.13
===>truck:	25.74
===>bus:	32.48
===>train:	1.34
===>motocycle:	29.35
===>bicycle:	38.11
===> mIoU: 37.57

## Reslut

| Method | road | sidewalk | building | wall | fence | pole | light | sign | vegetation | terrain | sky | person | rider | car | truck | bus | train | motocycle | bicycle | mIoU |
|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|
| 내용 11 | 내용 12 | 내용 13 | 내용 11 | 내용 12 | 내용 13 | 내용 11 | 내용 12 | 내용 13 | 내용 11 | 내용 12 | 내용 13 | 내용 11 | 내용 12 | 내용 13 | 내용 11 | 내용 12 | 내용 13 | 내용 11 | 내용 12 | 내용 13 |
