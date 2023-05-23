## TVMCE Dataset
> TV shows MultiCamera Editing

It is the data used in [Temporal and Contextual Transformer for Multi-Camera Editing of TV Shows](https://arxiv.org/abs/2210.08737)

### Download
Check the project [website](https://virtualfilmstudio.github.io/projects/multicam/).

#### Folder structure
Notes: 
- For track selection, we only use frame that its boundary label is 1, since we care where the choice of camera tracks on the shot boundary.
- For data transfer efficiency, we compress the video file as a `.tar`, and it requires decompression to use, such as `tar -xvf video_0002.tar`.

```
├── TVMCE
│   ├── meta
│   │   ├── train.json         # Json file used with a sampling stride of 5 frames
│   │   ├── test.json          # The structure is the same as the meta/train folder
│   ├── train                  # Video frames file with a sampling stride of 5 frames
│   │   ├── video_0002         # Video TV Show id
│   │   │   ├── output         # Video frames from the final output
│   │   │   │   ├── 18362.jpg
│   │   │   │   ├── ...
│   │   │   ├── CAM1           # Video frames from different track
│   │   │   │   ├── 18460.jpg
│   │   │   │   ├── ...
│   │   │   ├── CAM2
│   │   │   │   ├── 18460.jpg
│   │   │   │   ├── ...
│   │   │   ├── ...
│   │   ├── video_0003         # Other TV Shows, and the structure is the same as the video_0002 folder
│   │   │   ├── ...  
│   │   ├── ...
│   ├── test                   # The structure is the same as the train folder
│   │   ├── video_0000
│   │   ├── ...
```

Details about the label file.
```
train.json
[
    {
    "videoID"               : program_name,
    "sampleInterval"        : int,              # Different sampling stride
    "startFrame"            : int,              # Start frame of sliding window
    "currentCam"            : camera_namm,      # Camera id of the historical information
    "outputList"            : [framid],         # Temporal frame ids 
    "selectCam"             : camera_namm,      # Camera id of selected
    "CAMFrame"              : int,              # Contextual frame id
    "label"                 : [...],            # Label for whether candidate cameras are selected
    "boundary"              : bool,             # Whether to switch cameras
    "CAMList"               : [...]             # List of candidate cameras
    },
    {...}
]
```

### Citation

```
@article{rao2022temporal,
  title={Temporal and Contextual Transformer for Multi-Camera Editing of TV Shows},
  author={Rao, Anyi and Jiang, Xuekun and Wang, Sichen and Guo, Yuwei and Liu, Zihao and Dai, Bo and Pang, Long and Wu, Xiaoyu and Lin, Dahua and Jin, Libiao},
  journal={arXiv preprint arXiv:2210.08737},
  year={2022}
}
```
