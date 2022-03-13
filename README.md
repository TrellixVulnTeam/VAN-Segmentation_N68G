# Visual Attention Network (VAN) for Segmentaion
This repo is a PyTorch implementation of applying **VAN** (**Visual Attention Network**) to semantic segmentation.
The code is based on [mmsegmentaion](https://github.com/open-mmlab/mmsegmentation/tree/v0.12.0).

More detailes can be found in [**Visual Attention Network**](https://arxiv.org/abs/2202.09741).

### Citation:
```
@article{guo2022visual,
  title={Visual Attention Network},
  author={Guo, Meng-Hao and Lu, Cheng-Ze and Liu, Zheng-Ning and Cheng, Ming-Ming and Hu, Shi-Min},
  journal={arXiv preprint arXiv:2202.09741},
  year={2022}
}
```

### Results
**Notes**: Pre-trained models can be found in [Visual Attention Network for Classification](https://github.com/Visual-Attention-Network/VAN-Classification).
#### VAN + UperNet
|    Backbone     | Iters | mIoU | Config | Download  |
| :-------------: | :-----: | :------: | :------------: | :----: |
|    VAN-Tiny     | 160K | 41.1 |  [config](https://github.com/Visual-Attention-Network/VAN-Segmentation/blob/main/configs/upernet/VAN/upernet_van_tiny_512x512_160k_ade20k.py)  |  |
|    VAN-Small    | 160K |  44.9  |  [config](https://github.com/Visual-Attention-Network/VAN-Segmentation/blob/main/configs/upernet/VAN/upernet_van_small_512x512_160k_ade20k.py)  |  |
|    VAN-Base     | 160K | 48.3   |  [config](https://github.com/Visual-Attention-Network/VAN-Segmentation/blob/main/configs/upernet/VAN/upernet_van_base_512x512_160k_ade20k.py)  |  |
|    VAN-Large    | 160K |  50.1  |  [config](https://github.com/Visual-Attention-Network/VAN-Segmentation/blob/main/configs/upernet/VAN/upernet_van_large_512x512_160k_ade20k.py)  |  |


**Notes**: In this scheme, we use multi-scale validation following Swin-Transformer.

#### VAN + Semantic FPN
|    Backbone     | Iters | mIoU | Config | Download  |
| :-------------: | :-----: | :------: | :------------: | :----: |
|    VAN-Tiny     | 40K | 38.5 |  [config](https://github.com/Visual-Attention-Network/VAN-Segmentation/blob/main/configs/sem_fpn/VAN/fpn_van_tiny_ade20k_40k.py)  | [Google Drive](https://drive.google.com/file/d/1Jl8LtyvOl6xeNMKCjpK2Rp_tGRfua8LJ/view?usp=sharing) |
|    VAN-Small    | 40K |  42.9  |  [config](https://github.com/Visual-Attention-Network/VAN-Segmentation/blob/main/configs/sem_fpn/VAN/fpn_van_small_ade20k_40k.py)  | [Google Drive](https://drive.google.com/file/d/1Xfuo9D3Fo7b6zSCLTWE77k2jgYSHVSb8/view?usp=sharing) |
|    VAN-Base     | 40K | 46.7   |  [config](https://github.com/Visual-Attention-Network/VAN-Segmentation/blob/main/configs/sem_fpn/VAN/fpn_van_base_ade20k_40k.py)  | [Google Drive](https://drive.google.com/file/d/1Ar4Hq9DjgaULQKfwM-jJvSO-D6gendpf/view?usp=sharing) |
|    VAN-Large    | 40K |  48.1  |  [config](https://github.com/Visual-Attention-Network/VAN-Segmentation/blob/main/configs/sem_fpn/VAN/fpn_van_large_ade20k_40k.py)  | [Google Drive](https://drive.google.com/file/d/1v61uCi07IC6eyVHn3xbJqz4nOiGa1POY/view?usp=sharing) |


### Preparation
Install MMSegmentation and download ADE20K according to the guidelines in MMSegmentation.

### Requirement

```
Pytorch >= 1.7
MMSegmentation == v0.12.0 (https://github.com/open-mmlab/mmsegmentation/tree/v0.12.0)
```

### Training
We use 8 GPUs for training by default. Run:
```bash
dist_train.sh /path/to/config 8
```
### Evaluation
To evaluate the model, run:
```bash
dist_test.sh /path/to/config /path/to/checkpoint_file 8 --out results.pkl --eval mIoU
```

## Acknowledgment

Our implementation is mainly based on [mmsegmentaion](https://github.com/open-mmlab/mmsegmentation/tree/v0.12.0), [Swin-Transformer](https://github.com/SwinTransformer/Swin-Transformer-Semantic-Segmentation), and [PoolFormer](https://github.com/sail-sg/poolformer). Thanks for their authors. 

## LICENSE

This repo is under the Apache-2.0 license. For commercial use, please contact the authors.


