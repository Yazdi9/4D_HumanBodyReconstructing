# 4D & 3D Human Body Reconstruction on Videos 

<div align="center">

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1g5qxi6Oibd6RtmCqaMlRa62FlJPJENFB#scrollTo=XoBvsEG9Xuub) 

</div>


<table class="center">

<tr>
  <td style="text-align:center;"><b>Source Video</b></td>
  <td style="text-align:center;"><b>Recounstruction Video</b></td>
  
</tr>  

<tr>
   <td>
    

https://github.com/saba99/4D_HumanBodyReconstructing/assets/33378412/3d278a29-a881-4036-a736-d1e75a42f657


   </td>
   <td>
 
https://github.com/saba99/4D_HumanBodyReconstructing/assets/33378412/bd958d64-44fe-4786-be67-0ec1b108dcc2

   </td>
</tr>
<tr>
   <td>
    

<img src="https://github.com/saba99/4D_HumanBodyReconstructing/assets/33378412/40eab1ad-9348-4831-801f-2a58842c4f95.png">




   </td>
   <td>



<img src="https://github.com/saba99/4D_HumanBodyReconstructing/assets/33378412/ce52e89b-ab7d-46c8-8994-81b312f07021.png" >




   </td>
</tr>


</table>

### You can Find More Outputs Here :[More Outputs](https://mega.nz/fm/FiwxhJxQ)



## Installation and Setup
First, clone the repo. Then, we recommend creating a clean [conda](https://docs.conda.io/) environment, installing all dependencies, and finally activating the environment, as follows:
```bash
git clone https://github.com/saba99/4D_HumanBodyReconstructing.git
cd  4D_HumanBodyReconstructing
```

```bash
pip install numpy==1.23.1 torch
pip install -e .[all]
```


## Run 

```bash
# Run on video file
python track.py video.source="example_data/videos/gymnasts.mp4"

# Run on extracted frames
python track.py video.source="/path/to/frames_folder/"

# Run on a youtube link (depends on pytube working properly)
python track.py video.source=\'"https://www.youtube.com/watch?v=xEH_5T9jMVU"\'
```

## Training
Download the [training data](https://www.dropbox.com/sh/mjdwu59fxuhls5h/AACQ6FCGSrggUXmRzuubRHXIa) to `./hmr2_training_data/`, then start training using the following command:
```
bash fetch_training_data.sh
python train.py exp_name=hmr2 data=mix_all experiment=hmr_vit_transformer trainer=gpu launcher=local
```

## Evaluation
Download the [evaluation metadata](https://www.dropbox.com/scl/fi/kl79djemdgqcl6d691er7/hmr2_evaluation_data.tar.gz?rlkey=ttmbdu3x5etxwqqyzwk581zjl) to `./hmr2_evaluation_data/`. Additionally, download the Human3.6M, 3DPW, LSP-Extended, COCO, and PoseTrack dataset images and update the corresponding paths in  `hmr2/configs/datasets_eval.yaml`.

Run evaluation on multiple datasets as follows, results are stored in `results/eval_regression.csv`. 
```bash
python eval.py --dataset 'H36M-VAL-P2,3DPW-TEST,LSP-EXTENDED,POSETRACK-VAL,COCO-VAL' 
```

 

 

 
