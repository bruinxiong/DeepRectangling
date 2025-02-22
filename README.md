# Deep Rectangling for Image stitching: A Learning Baseline ([paper](https://arxiv.org/abs/2203.03831))
<p align="center">Lang Nie<sup>1</sup>, Chunyu Lin<sup>1 *</sup>, Kang Liao<sup>1</sup>, Shuaicheng Liu<sup>2</sup>, Yao Zhao<sup>1</sup></p>
<p align="center"><sup>1</sup>Institute of Information Science, Beijing Jiaotong University</p>
<p align="center"><sup>2</sup>School of Information and Communication Engineering, University of Electronic Science and Technology of China</p>
<p align="center"><sup>{nielang, cylin, kang_liao, yzhao}@bjtu.edu.cn, liushuaicheng@uestc.edu.cn</sup></p>

<div align=center>
<img src="https://github.com/nie-lang/DeepRectangling/blob/main/rectangling.jpg"/>
</div>

## Dataset (DIR-D)
The details of the dataset can be found in our paper. 

We release our testing results with the proposed dataset together. One can download it in in [Google Drive](https://drive.google.com/file/d/1KR5DtekPJin3bmQPlTGP4wbM1zFR80ak/view?usp=sharing) or [Baidu Cloud](https://pan.baidu.com/s/1aNpHwT8JIAfX_0GtsxsWyQ)(Extraction code: 1234).

## Requirement
* python 3.6
* numpy 1.18.1
* tensorflow 1.13.1

<sup>We only test it in Ubuntu OS with RXT 2080Ti.</sup>

## For windows system
For windows OS users, you have to change '/' to '\\\\' in 'line 52 of Codes/utils.py'.

## Training
#### Step 1: Download the pretrained vgg19 model
Download [VGG-19](https://www.vlfeat.org/matconvnet/pretrained/#downloading-the-pre-trained-models). Search imagenet-vgg-verydeep-19 in this page and download imagenet-vgg-verydeep-19.mat. 

#### Step 2: Train the network
Modidy the 'Codes/constant.py' to set the 'TRAIN_FOLDER'/'ITERATIONS'/'GPU'. In our experiment, we set 'ITERATIONS' to 100,000.

```
cd Codes/
python train.py
```

## Testing
#### Pretrained model for deep rectangling
Our pretrained rectangling model can be available at [Google Drive](https://drive.google.com/drive/folders/1gEsE-7QBPcbH-kfHqYYR67C-va7vztxO?usp=sharing) or [Baidu Cloud](https://pan.baidu.com/s/19jRzz_1E97X35j6qmWm_kg)(Extraction code: 1234). And place the four files to 'Codes/checkpoints/Ptrained_model/' folder.
#### Testing 
Modidy the 'Codes/constant.py'to set the 'TEST_FOLDER'/'GPU'. The path for the checkpoint file can be modified in 'Codes/inference.py'.

```
cd Codes/
python inference.py
```
#### Testing with arbitrary resolution images
Modidy the 'Codes_for_Arbitrary_Resolution/constant.py'to set the 'TEST_FOLDER'/'GPU'. The path for the checkpoint file can be modified in 'Codes_for_Arbitrary_Resolution/inference.py'. 
Then, put the testing images into the folder 'Codes_for_Arbitrary_Resolution/other_dataset/' (including input and mask) and run:

```
cd Codes_for_Arbitrary_Resolution/
python inference.py
```
The rectangling results can be found in Codes_for_Arbitrary_Resolution/rectangling/.


## Citation
This paper has been accepted by CVPR2022 as oral presentation. If you have any questions, please feel free to contact me.


NIE Lang -- nielang@bjtu.edu.cn
```
@article{nie2022deep,
      title={Deep Rectangling for Image Stitching: A Learning Baseline}, 
      author={Lang Nie and Chunyu Lin and Kang Liao and Shuaicheng Liu and Yao Zhao},
      journal={arXiv preprint arXiv:2203.03831},
      year={2022},
}
```

## Reference
Lang Nie, Chunyu Lin, Kang Liao, Shuaicheng Liu, and Yao Zhao. Depth-aware multi-grid deep homography estimation with contextual correlation. IEEE Trans. on Circuits and Systems for Video Technology, 2021.
