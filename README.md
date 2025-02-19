# VidCapBench: A Comprehensive Benchmark of Video Captioning for Controllable Text-to-Video Generation

## 🚀 Overview
VidCapBench is the first evaluation benchmark designed to assess the quality of video captions for controllable text-to-video (T2V) generation. Our goal is to provide a robust and diverse benchmark to evaluate captioning models and guide the development of high-quality T2V systems.

To achieve this, we have made the following endeavers in data curation:

* ***Diverse videos.*** Besides collecting videos from open-source datasets, we also use videos from YouTube and user-generated content (UGC) platforms to ensure a portion of our data remains unexposed to prior training or processing. When collecting videos, we pay much attention to the diversity, resulting in various subject categories, art styles, subjects amounts, video length, and so on.

<p align="center">
    <img src="./assets/video_distribution.png" width="94%" height="100%">
</p>

* ***Diverse QA pairs aligned with T2V evaluation.*** VidCapBench evaluate captioning models across four critical dimensions: Video Aesthetics, Video Content, Video Motion, and Physical Laws, which align with the key metrics of T2V generation. The QA pairs are initially generated by GPT-4o and expert classifiers, followed by manual revision to the unsuitable pairs and additional annotation to address any imbalances in dimensions.

    Through analysis, we find that in the predefined-QA evaluation paradigm, there exists a subset of QA pairs that cannot be reliably evaluated through automated methods due to inconsistencies in repetitive machine evaluations. To address this, we split the QA pairs in VidCapBench into two subsets:
  * **VidCapBench-AE** <img src="./assets/AE.png" width="20" height="20">, QA pairs that receive consistent machine evaluations and can be assessed automatically.
  * **VidCapBench-HE** <img src="./assets/HE.png" width="18" height="18">, More challenging QA pairs that require human intervention for nuanced differentiation.

<p align="center">
    <img src="./assets/demo_qa_distribution.png" width="94%" height="100%">
</p>

* ***Training-free T2V verification.*** We have conducted training-free T2V verification to demonstrate the significant positive correlation between scores on VidCapBench and T2V quality metrics, highlighting that VidCapBench can provide valuable guidance for training T2V models. We provide a qualitive illustration below. In this case, the video is associated with nine QA pairs in VidCapBench-AE <img src="./assets/AE.png" width="20" height="20"> and four QA pairs in VidCapBench-HE <img src="./assets/HE.png" width="18" height="18">. The similarity between the generated video and the original video, as well as the overall generation quality, are strongly correlated with the evaluation results in VidCapBench. Among the captioning models compared, Gemini exhibits the best performance. 
<p align="center">
    <img src="./assets/casestudy.png" width="94%" height="100%">
</p>

## 🛠️ Evaluation Pipeline
To evaluate your captioning models on VidCapBench, please follow these steps:
1. Clone this repo.
```
git clone https://github.com/VidCapBench/VidCapBench.git
cd ./VidCapBench
```

2. Download the videos and QA files at TODO

3. Use your captioning model to generate captions for the videos in VidCapBench, and save the generated captions in JSONL format, adhering to the following structure:
```
{"question": "Describe the video in detail.", "video": "videos_qa_80.mp4", "model_generation": Caption}
```
4. execute the evaluation script with the path to your generated captions:
```
python eval.py --caption_path /path_to/caption.jsonl --qa_path /path_to/VidCapBench-AE.jsonl
```
You can use your own API key for GPT-4o evaluation by editing the code [here](./eval.py#L24).

## 📈 Experimental Results

<p align="center">
    <img src="./assets/main_results.png" width="100%" >
</p>


## 🪪 License
```
VidCapBench is intended solely for academic research purposes, and any form of commercial use is strictly prohibited. 
The copyright of all videos belongs to the video owners.
If there is any infringement in VidCapBench, please email vidcapbench@gmail.com and we will remove it immediately.
Without prior authorization, you are not permitted to distribute, publish, copy, disseminate, or modify any part of VidCapBench. 
Compliance with these restrictions is mandatory.
```

## 📜 Citation

If you find our work helpful for your research, please consider citing our work.   

```bibtex
TODO
```
