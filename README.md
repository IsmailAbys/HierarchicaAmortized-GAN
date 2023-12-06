# Hierarchical Amortized GAN (HA-GAN)


#### [[Paper & Supplementary Material]](https://ieeexplore.ieee.org/abstract/document/9770375)

You find in this repository the code of HA-GAN models for data augmentation.
Before the training, make sure that you have at least 3000 images for training. You can increase your database by using those [[thechnique]](https://github.com/IsmailAbys/DataPrecessing/tree/main/data_augmentation) for data augmentation.
```Python

```
### Requirements
- PyTorch
- scikit-image
- nibabel
- nilearn
- tensorboardX
- SimpleITK



### Data Preprocessing
The volume data need to be cropped or resized to 128<sup>3</sup> or 256<sup>3</sup>, and intensity value need to be scaled to [-1,1]. In addition, we would like to advise you to trim blank axial slices. More details can be found at
```bash
python preprocess.py
```

### Training
#### Unconditional HA-GAN
```bash
python train.py --workers 8 --img-size 256 --num-class 0 --exp-name 'HA_GAN_run1' --data-dir DATA_DIR
```
#### Conditional HA-GAN
```bash
python train.py --workers 8 --img-size 256 --num-class N --exp-name 'HA_GAN_cond_run1' --data-dir DATA_DIR
```

Track your training with Tensorboard:
<p align="center">
  <img width="75%" height="%75" src="https://github.com/batmanlab/HA-GAN/blob/master/figures/tensorboard.png">
</p>

It will take around 22 hours to train unconditional HA-GAN for 80000 iterations with two NVIDIA Tesla V100 GPU. It is suggested to have at least 3000 images for training to avoid mode collapse, or you may need to consider [data augmentation](https://docs.monai.io/en/stable/transforms.html#intensity-dict).

### Testing
```bash
visualization.ipynb
evaluation/visualize_feature_MDS.ipynb
python evaluation/fid_score.py
```

### Sample images
<p align="center">
  <img width="75%" height="%75" src="https://github.com/batmanlab/HA-GAN/blob/master/figures/sample_HA_GAN.png">
</p>

### Pretrained weights
<table><tbody>
<!-- START TABLE -->
<!-- TABLE HEADER -->
<th valign="bottom">Dataset</th>
<th valign="bottom">Anatomy</th>
<th valign="bottom">Iteration</th>
<th valign="bottom">Checkpoint</th>
<!-- TABLE BODY -->
<tr><td align="left"><a href="https://www.ncbi.nlm.nih.gov/projects/gap/cgi-bin/study.cgi?study_id=phs000179.v6.p2">COPDGene</a></td>
<td align="center">Lung</td>
<td align="center">80000</td>
<td align="center"><a href="https://drive.google.com/file/d/1orNvz7DLsCn5KWKjjVpEL4e5mO0akf6g/view?usp=sharing">Download</a></td>
</tr>
<tr><td align="left"><a href="https://dataverse.harvard.edu/dataverse/GSP">GSP</a></td>
<td align="center">Brain</td>
<td align="center">80000</td>
<td align="center"><a href="https://drive.google.com/file/d/10AcfBPB_Tnjgy9bSj1qcZTW1s7qTIWRM/view?usp=sharing">Download</a></td>
</tr>
  
</tbody></table>

### Citation
```
@ARTICLE{hagan2022,
  author={Sun, Li and Chen, Junxiang and Xu, Yanwu and Gong, Mingming and Yu, Ke and Batmanghelich, Kayhan},
  journal={IEEE Journal of Biomedical and Health Informatics}, 
  title={Hierarchical Amortized GAN for 3D High Resolution Medical Image Synthesis}, 
  year={2022},
  volume={26},
  number={8},
  pages={3966-3975},
  doi={10.1109/JBHI.2022.3172976}}
```
