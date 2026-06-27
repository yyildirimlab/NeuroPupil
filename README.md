# NeuroPupil
Directory to two software tools used in the "NeruoPupil Paper"

https://www.biorxiv.org/content/10.64898/2026.05.14.725098v1

This website accompanies a manuscript currently under peer review.

<img width="9600" height="4442" alt="DeepVision_Animal_GUI_Flow_Chart (3)" src="https://github.com/user-attachments/assets/25572b22-cbb6-4769-b341-99218e1895f7" />


## [`mediaGUI`](https://github.com/khicken/mediaGUI)
Use this tool to preprocess gigabytes of facial video data to a single concatenated video, which is used to train DeepFace.

**Please see [mediaGUI](https://github.com/khicken/mediaGUI) for installation instructions.**

## [`sleapGUI`](https://github.com/khicken/sleapGUI)
This tool incorporates the optimized parameter combination specifically identified for large scale facial video analysis, enabling accurate and efficient large-scale orofacial data processing beyond the default SLEAP GUI.

**Please see [sleapGUI](https://github.com/khicken/sleapGUI) for installation instructions.**

## Usage Demo

Tutorial Videos to Replicate DeepVision using your data:

[NeuroPupil Tutorial Playlist](https://www.youtube.com/playlist?list=PLdt5kwsCtktxSgYm0I6CQ1be1tvhi67qd)

Video Part 1 Summary - Concatenation
1. Open the Downloaded **mediaGUI**
2. Select the **Add Video** button to add a video
3. Repeat this step for all of the data intended for analysis.
4. Choose the specific number of frames needed to be extracted. Total number of frames that can be concatenated is 30k.
   Note: In the video, 5 videos were used to create a custom model. 30k frames / 5 videos = 6k frames per video was extracted evenly.
         Adjust the specific number of evenly extracted frames to how many videos you want to analyze.
5. Make the output fps match that of the frame speed of the raw video.
   Note: In the video, the data's frame rate was 30 fps. Adjust the frame rate depending on your experimental video acquistion speed.
6. Click **Process Videos** and save the output to the desired location

## HPC Code
Attached here is the SLEAP based command lines that was used to do high performance computing analysis at Cleveland Clinic Research using its avaliable GPU Type (A100) and Node Number (n = 2). 

## Troubleshoot
If you have a technical question with either [`mediaGUI`](https://github.com/khicken/mediaGUI) or [`sleapGUI`](https://github.com/khicken/sleapGUI), then feel free to request a "New Issue" in the "Issues" section for the respective GUI.

## Citation
If you use any components from this repository in your research, please cite the relevant publications associated with each module as specified in their respective README files.
