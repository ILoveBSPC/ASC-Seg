<div align="center">
<h1> ASC-Seg: Adaptive Structure Alignment and Cross-scale Decoding for Medical Image Segmentation </h1>
</div>

## 🎈 News

- [2025.4.18] Training and inference code released

⭐ Abstract

Medical image segmentation plays a vital role in clinical workflows and treatment plans.
However, it faces two challenges:
First, the contour structures of salient objects and background details vary significantly in medical images of different modalities.
Second, the salient and non-salient objects often exhibit misleading co-occurrence phenomena and noise interference often exists at the segmentation boundaries.
To overcome these challenges, we propose ASC-Seg, a network designed to enhance medical image segmentation.
ASC-Seg adopts the Adaptive Structure Encoder (ASE) to capture the global structure and context of salient objects via parallel Mamba, and uses deformable learning to adaptively locate fine-grained contour details in complex backgrounds in medical images of different modalities.
Plus, our Cross-scale Noise Suppression Decoder (CNSD) uses noise suppression strategy and efficient attention mechanism to suppress noise introduced by non-salient regions and highlight critical salient regions, thereby enhancing the model's accuracy to distinguishing salient and non-salient objects.
Extensive experiments of ASC-Seg on 5 medical image datasets verify its superior performance and versatility, demonstrating its potential in the field of medical image segmentation.

## 🚀 The challenges

<div align="center">
    <img width="400" alt="image1" src="asserts/cha1.png?raw=true" style="display: inline-block; margin-right: 10px;">
    <img width="400" alt="image2" src="asserts/cha2.png?raw=true" style="display: inline-block;">
</div>

## 📻 Overview

<div align="center">
<img width="800" alt="image" src="asserts/ASC-Seg.png?raw=true">
</div>


Illustration of the overall architecture of ASC-Seg. (II) ASE is Adaptive Structural Encoder, (III) CNSD is Cross-scale Noise Suppression Decoder, (IV) FAC is Feature Alignment Connector, (II.a) IPCB is Inverted Pyramid Convolution Block, (II.b) DCB is Deformable Convolution Block, (II.c) PMB is Parallel Mamba Block, (III.a) MSFA is Multi-Scale Feature Aggregation Module, (III.b) SFM is Salient Focus Module, (III.b) DFB is Denoising Focus Block, (III.b) SAB is Spatial Attention Block, and (III.c) CAB is Channel Attention Block.


## 📆 TODO

- [x] Release code

## 🎮 Getting Started

### 1. Install Environment

```
conda create -n ASCSeg python=3.8
conda activate ASCSeg
pip install torch==1.13.0 torchvision==0.14.0 torchaudio==0.13.0 --extra-index-url https://download.pytorch.org/whl/cu117
pip install packaging
pip install timm==0.4.12
pip install pytest chardet yacs termcolor
pip install submitit tensorboardX
pip install triton==2.0.0
pip install causal_conv1d==1.0.0  # causal_conv1d-1.0.0+cu118torch1.13cxx11abiFALSE-cp38-cp38-linux_x86_64.whl
pip install mamba_ssm==1.0.1  # mmamba_ssm-1.0.1+cu118torch1.13cxx11abiFALSE-cp38-cp38-linux_x86_64.whl
pip install scikit-learn matplotlib thop h5py SimpleITK scikit-image medpy yacs
```

### 2. Prepare Datasets

- Download datasets: ISIC2017 from this [link](https://challenge.isic-archive.com/data/#2017), ISIC2018 from this [link](https://challenge.isic-archive.com/data/#2018), and PH2 from this [link](https://www.dropbox.com/scl/fi/epzcoqeyr1v9qlv/PH2Dataset.rar?rlkey=6mt2jlvwfkditkyg12xdei6ux&e=1), Kvasir from this[link](https://link.zhihu.com/?target=https%3A//datasets.simula.no/downloads/kvasir-seg.zip), and BUSI from this [link](https://scholar.cu.edu.eg/?q=afahmy/pages/dataset).
- Folder organization: put ISIC2017 datasets into ./data/ISIC2017 folder, ISIC2018 datasets into ./data/ISIC2018 folder, and PH2 datasets into ./data/PH2 folder, Kvasir datasets into ./data/Kvasir folder, and BUSI datasets into ./data/BUSI folder.

### 3. Train the ASC-Seg

```
python train.py --datasets ISIC2018
training records is saved to ./log folder
pre-training file is saved to ./checkpoints/ISIC2018/best.pth
concrete information see train.py, please
```

### 3. Test the ASC-Seg

```
python test.py --datasets ISIC2018
testing records is saved to ./log folder
testing results are saved to ./Test/ISIC2018/images folder
concrete information see test.py, please
```


## 🖼️ Visualization

<div align="center">
<img width="800" alt="image" src="asserts/Visualization.png?raw=true">
</div>



## 🎫 License

The content of this project itself is licensed under [LICENSE](LICENSE).

## 💡 Acknowledgement

- [VM-UNet](https://github.com/JCruan519/VM-UNet)

