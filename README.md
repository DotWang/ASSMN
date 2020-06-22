# Adaptive Spectral-Spatial Multiscale Network for Hyperspectral Image Classification

![](https://github.com/DotWang/ASSMN/blob/master/model.png)

## Usage

1. Install Pytorch 1.1 with Python 3.5.

2. Clone this repo

```
git clone https://github.com/DotWang/ASSMN.git
```

3. Training and evaluation with ***trainval.py***

```
CUDA_VISIBLE_DEVICES=0 python trainval.py \
	--dataset 'ksc' \
	--dr-num 4 --dr-method 'pca' \
	--mi -1 --ma 1 \
	--half-size 13 --rsz 27 \
	--experiment-num 10 \
	--lr 1e-2 --epochs 200 --batch-size 16 \
	--scheme 2 --strategy 's2' \
	--spec-time-steps 2 \
	--group 'alternate' --seq 'cascade' \
	--npi-num 2
```
Then the assessment results are memoried in the corresponding ***\*.mat*** file and the generated model is saved.

4. Predicting with ***infer.py***

```
CUDA_VISIBLE_DEVICES=0 python infer.py \
      --dataset 'ksc' \
      --mi -1 --ma 1 \
      --half-size 13 --rsz 27 \
      --bz 50000 \
      --scheme 2 --strategy 's2' 
```
And then producing the final classification map.

## Paper and Citation

If this repo is useful for your research, please cite our [paper](https://doi.org/10.1109/TGRS.2020.2999957).

```
@ARTICLE{2020ASSMN,
  author={D. {Wang} and B. {Du} and L. {Zhang} and Y. {Xu}},
  journal={IEEE Transactions on Geoscience and Remote Sensing}, 
  title={Adaptive Spectral-Spatial Multiscale Contextual Feature Extraction for Hyperspectral Image Classification}, 
  year={2020},
  pages={1-17},
  doi={10.1109/TGRS.2020.2999957},
  url={https://doi.org/10.1109/TGRS.2020.2999957},
}
```

## Acknowledgement
Thanks [Andrea Palazzi](https://github.com/ndrplz/ConvLSTM_pytorch) for providing the Pytorch implementation of Convolutional LSTM!


