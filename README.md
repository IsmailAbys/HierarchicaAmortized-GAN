# Hierarchical Amortized GAN (HA-GAN)


#### [[Paper & Supplementary Material]](https://ieeexplore.ieee.org/abstract/document/9770375)

You find in this repository the code of HA-GAN models for data augmentation.
Before the training, make sure that you have at least 3000 images for training. You can increase your database by using those [techniques](https://github.com/IsmailAbys/DataPrecessing/tree/main/data_augmentation) for data augmentation.

Download the repository 
```Python
git clone https://github.com/IsmailAbys/HierarchicaAmortized-GAN.git
cd HierarchicaAmortized-GAN
```

### Requirements
- PyTorch
- scikit-image
- nibabel
- nilearn
- tensorboardX
- SimpleITK
To install those liberairies, excute 
```Python
pip install -r requirements.txt
```


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
In our context, we will use the unconditional HA-GAN
#### Conditional HA-GAN
```bash
python train.py --workers 8 --img-size 256 --num-class N --exp-name 'HA_GAN_cond_run1' --data-dir DATA_DIR
```
In this context, N means the number of classes 



Track your training with Tensorboard by executing:
```Python
tenorboard --loggir=checkpoint/HA_GAN_run1
```
In this case, our parameters are in the folder "HA_GAN_run1", you can change the folder that you save your parameters
<p align="center">
  <img width="75%" height="%75" src="https://github.com/IsmailAbys/HierarchicaAmortized-GAN/blob/main/figure/tensorboard.png">
</p>


### Testing
To visualise and save the results, you may employ the provided notebook.
```bash
visualization.ipynb
```

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
