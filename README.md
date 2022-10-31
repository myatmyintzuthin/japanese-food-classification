# Japanese Food Classification

This repository contains training, evaluation and testing of classification models implementated from stratch using PyTorch.
## Classes
Ramen :ramen: , Sashimi :fish: , Sushi :sushi: , Takoyaki :dango:

## Available Models
| Model       | Variants |
| ----------- | ----------- |
| VGG         | 11, 13, 16, 19 |
| Resnet      | 18, 34, 50, 101, 152 |
| Mobilenet   | v2 |

## 1. Dependencies

Please install essential dependencies (see  `requirements.txt`)

### 1.1. Create conda virtual environment
```bash
conda create -n jpfood python==3.8
```

### 1.2. Activate environment
```bash
conda activate jpfood
```

### 1.3. Install dependencies
```bash
pip install -r requirements.txt
```
## 2. Dataset
The dataset used in this repository is a subset of [Food-101 dataset](https://data.vision.ee.ethz.ch/cvl/datasets_extra/food-101/).\
The original dataset contains 1000 images for each class. \
In this repository, train - 200, validation - 100 and test - 100 images are used.\
Japanese food dataset can be downloaded from [link](https://github.com/myatmyintzuthin/models-in-pytorch/releases/download/v.1.0/japanese_food.zip)

## 3. Prepare pretrained models
Model implementations are available in `models/{model}.py` folder. \
To initialize PyTorch's pretrained model weights to our model architecture, run:
```bash
python convert.py --model resnet --variant 50 

options:
    --model : Model name {vgg, resnet, mobilenet}
    --variant : Model variant 
    --width_mulit : channel width ratio for mobilenet
    --num_class : 1000 default for ImageNet classes
```
Pretrained models will be saved as `pretrained/{model}.pt`
## 4. Prepare Config
Change model and variant of desired model before training and testing in `config.yaml`.
```
model:
    name: 'resnet'
    variant: '50'
```
## 5. Training and evaluation
For training, run:
```bash
python train.py

options:
    --eval : To evaluate the model without training again
    --eval_model : model path for evaluation
```
## 6. Inference
For inference, run:
```bash
python inference.py --image {image_path} --viz

options:
    --image : Folder path to inference images
    --viz   : Whether to visualize inferece results
```

## Reference
- [Torch Vision](https://github.com/pytorch/vision/tree/main/torchvision/models)
- [Zero to Mastery Learn PyTorch for Deep Learning](https://www.learnpytorch.io/)
