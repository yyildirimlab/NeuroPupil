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

**Video Part 1 Summary - Concatenation**

1. Open the Downloaded **mediaGUI**
 
2. Select the **Add Video** button to add a video

3. Repeat this step for all of the data intended for analysis.
   
4. Choose the specific number of frames needed to be extracted. Total number of frames that can be concatenated is 30k.
   Note: In the video, 5 videos were used to create a custom model. 30k frames / 5 videos = 6k frames per video was extracted evenly.
         Adjust the specific number of evenly extracted frames to how many videos you want to analyze.
   
5. Make the output fps match that of the frame speed of the raw video.
   Note: In the video, the data's frame rate was 30 fps. Adjust the frame rate depending on your experimental video acquistion speed.


6. Click **Process Videos** and save the output to the desired location


**Video Part 2 Summary - Pupil Model Creation**

1. Open Anaconda Prompt

2. Activate SLEAP enviornment

<pre>
<code>conda activate sleap</code>
</pre>


3. Open default SLEAP GUI for Labeling
  
<pre>
<code>sleap-label</code>
</pre>


4. Insert the Concatenated Video, which was created in Video Part 1

5. Go to the **Skeleton** Tab on the Bottom Right, and add 4 nodes/keypoints
6. Name the points the following: Top, Bottom, Right, Left
7. Click the **Edges** Tab on the Top Right, and add 2 edges from the keypoints by selecting the desired edge pairs below, then click the button **Add Edge**.

   Top - Bottom

   
   Right - Left

8. Next, go to **Labeling Suggestions** to extract the images needed to label. Use the default **sample** method so that it extracts the desired frame number evenly.

Note: In the tutorial, 5 videos were used to make the concatenated video. Therefore, 10 images are needed to be labeled (2 images per video, shown in the paper). So in the GUI, specify 9 frames (10 - 1 frames) to pick the first 9 frames, then scroll to the very last frame in the concatenated video, and select **Add current frame** to add the last frame. Total images labeled will be 10 for this case.

In the paper, 200 videos were used to create a concatenated video for NeuroPupil Animal data, therefore 400 images were used to label. 

9. Go to the fist blue box on the bottom left part of the GUI, which selects the first image that is needed to be labeled. Click **New Instance** on the bottom right, then it will show the points that have the edge connections. Drag the points to the desired location of the pupil.

10. Click the next blue box and select **New Instance**, it will generate the keypoints that were used in the previous frame. Just drag them to the new pupil location, and continue this process until all of the blue boxes have the labeled images.

11. Once all of the frames are finished, save the SLEAP .slp file to the desired location.

12. Click **Predict**, then **Run Training**

13. Go to **Single Instance Model Configuration**, and select **baseline_large_rf.single(baseline_large_rf.single.json)** file on the top.

14. In the Model section on the Top Right, set the **Max Stride** and **Filters** to **64**

15. Once the model parameters are set, click **Run** on the Bottom Right.


**Video Part 3 Summary - Large Scale Pupil Data Analysis**

1. Open Anaconda Prompt

2. Activate SLEAP enviornment

<pre>
<code>conda activate sleap</code>
</pre>


3. Open Custom GUI for Large Scale Pupil Data Analysis
  
<pre>
<code>sleapgui pupil</code>
</pre>


4. Go to **Model Directory** to select the trained pupil model (Refer to Part 2 Video on how to create the pupil model)

5. Click **Add Videos** to add the pupil video data (avi or mp4 video input) for anlaysis. Mutiple videos can be added for analysis. 

6. Once the video analysis is ready, click **Run All** to do the data analysis.

7. The output will be the following: SLEAP (.slp) file, Pupil Keypoint CSV file for further processing, and labeled video.

## HPC Code
Attached here is the SLEAP based command lines that was used to do high performance computing analysis at Cleveland Clinic Research using its avaliable GPU Type (A100) and Node Number (n = 2). 

## Troubleshoot
If you have a technical question with either [`mediaGUI`](https://github.com/khicken/mediaGUI) or [`sleapGUI`](https://github.com/khicken/sleapGUI), then feel free to request a "New Issue" in the "Issues" section for the respective GUI.

## Citation
If you use any components from this repository in your research, please cite the relevant publications associated with each module as specified in their respective README files.
