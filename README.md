# DRTV30K Dataset

<div align="center">

## DRTV30K: A Large-Scale Multimodal UAV Object Detection Dataset

**Associated work:**  
**Generative Alignment Network for Multimodal UAV Object Detection**

Wentao Wu, Chenglong Li<sup>*</sup>, Ziwen Wang, Zhaodong Ding, Xiao Wang, and Bin Luo

Anhui University

<sup>*</sup>Corresponding author

</div>

---

> **Benchmark Setting:** DRTV30K provides oriented bounding box annotations for
> nine vehicle categories. Seven categories are used for the standard object
> detection benchmark, while **Pickup** and **Emergency Vehicle** are retained
> as rare categories for few-shot, long-tailed, and small-sample detection
> research.

## Introduction

DRTV30K is a large-scale multimodal UAV object detection dataset containing
paired visible and thermal infrared images captured from UAV top-view
perspectives.

The dataset contains **30,640 paired RGB-T images**, corresponding to
**61,280 individual images**, with **224,619 oriented bounding box
annotations** across nine vehicle categories.

DRTV30K covers diverse scenes, illumination conditions, flight altitudes, and
object scales. It also retains realistic local spatial discrepancies between
the visible and thermal infrared modalities, making it suitable for studying
multimodal detection, cross-modal alignment, feature fusion, small-object
recognition, and detection under adverse environmental conditions.

Among the nine annotated categories, seven categories form the standard
DRTV30K object detection benchmark. The remaining two categories, Pickup and
Emergency Vehicle, contain relatively few instances and are additionally
released to support few-shot and long-tailed object detection research.

DRTV30K can support research on:

- RGB-thermal multimodal object detection
- UAV-based vehicle detection
- Oriented object detection
- Cross-modal alignment and fusion
- Small-object detection
- Detection under nighttime and adverse conditions
- Long-tailed object detection
- Few-shot and rare-category detection

---

## News

- **2026-XX-XX:** DRTV30K is publicly released.
- Dataset documentation and evaluation tools will be continuously updated.
- The associated paper and source code will be released after they become
  publicly available.

---

## Dataset Overview

| Attribute | Description |
|---|---:|
| Paired RGB-T images | 30,640 pairs |
| Total individual images | 61,280 |
| Total annotations | 224,619 |
| Total annotated categories | 9 |
| Standard benchmark categories | 7 |
| Rare/few-shot categories | 2 |
| Annotation type | Oriented Bounding Box |
| Stored image resolution | 820 × 580 |
| Flight altitude | 50–180 m |
| Training set | 20,453 pairs |
| Validation set | 2,037 pairs |
| Test set | 8,150 pairs |

Each sample contains one visible image and its corresponding thermal infrared
image.

Although the paired videos were manually center-aligned during preprocessing,
additional pixel-level registration was not performed. Therefore, the dataset
retains realistic local cross-modal discrepancies caused by differences in
imaging mechanisms, camera configurations, UAV attitude, camera distortion,
and viewpoint changes.

---

## Dataset Visualization

<p align="center">
  <img src="assets/drtv30k_overview.png" width="95%">
</p>

<p align="center">
  <em>
    Examples of paired visible and thermal infrared images, oriented bounding
    box annotations, and representative samples from the nine object
    categories.
  </em>
</p>

> The dataset visualization will be added soon.

---

## Category Setting

DRTV30K provides oriented bounding box annotations for nine vehicle
categories. The categories are divided into a standard benchmark group and a
rare-category group.

### Standard Benchmark Categories

The following seven categories are used in the standard DRTV30K object
detection benchmark:

1. Car
2. Freight Car
3. Truck
4. Van
5. Tricycle
6. Bus
7. Construction Vehicle

### Rare and Few-Shot Categories

The following two categories contain substantially fewer annotated instances:

1. Pickup
2. Emergency Vehicle

These two categories are not included in the standard seven-category benchmark
evaluation. Their annotations are retained and released to support research
on:

- Few-shot object detection
- Long-tailed object detection
- Rare-category recognition
- Small-sample learning
- Category-incremental object detection
- Imbalanced multimodal learning

---

## Category Statistics

The number of oriented bounding box annotations for each category is shown
below.

| Category | Number of Instances | Usage |
|---|---:|---|
| Car | 194,514 | Standard benchmark |
| Freight Car | 10,397 | Standard benchmark |
| Truck | 8,161 | Standard benchmark |
| Van | 6,938 | Standard benchmark |
| Tricycle | 2,029 | Standard benchmark |
| Bus | 1,176 | Standard benchmark |
| Construction Vehicle | 955 | Standard benchmark |
| Pickup | 395 | Few-shot research |
| Emergency Vehicle | 54 | Few-shot research |
| **Total** | **224,619** | — |

The considerable differences in category frequency also make DRTV30K useful
for evaluating detection algorithms under class imbalance and long-tailed
data distributions.

---

## Dataset Split

DRTV30K is divided into training, validation, and test sets.

| Split | Number of RGB-T Pairs | Number of Individual Images |
|---|---:|---:|
| Training | 20,453 | 40,906 |
| Validation | 2,037 | 4,074 |
| Test | 8,150 | 16,300 |
| **Total** | **30,640** | **61,280** |

The official split files are provided with the released dataset. Researchers
are encouraged to use the official splits to ensure fair and reproducible
comparisons.

---

## Data Collection

DRTV30K was collected using a **DJI Matrice 4T** UAV equipped with visible and
thermal infrared cameras.

A total of **232 paired visible-thermal videos** were collected from different
regions. Due to the different imaging mechanisms and sensor configurations,
the visible and thermal cameras have different native spatial resolutions.

The visible camera records videos at 30 frames per second. The thermal camera
has a pixel pitch of 12 μm and operates in an infrared wavelength range of
8–14 μm. The thermal camera also supports a super-resolution imaging mode.

The dataset was collected under diverse real-world UAV observation
conditions, including:

- Urban roads
- Highways
- Suburban areas
- Parking lots
- Overpasses
- Bridges
- Daytime
- Nighttime
- Dark-night conditions
- Foggy conditions
- Different UAV flight altitudes

---

## Data Preprocessing

The visible and thermal infrared videos have different native resolutions
because of their distinct imaging mechanisms and camera configurations.

The main preprocessing steps are summarized as follows:

1. Visible and thermal infrared videos were paired according to their
   collection sequences.
2. Each video pair was processed and manually center-aligned.
3. The paired videos were resized to a unified spatial resolution of
   720 × 480.
4. One paired frame was extracted every 100 frames to reduce scene redundancy.
5. Image pairs with poor imaging quality were removed through manual
   inspection.
6. A 50-pixel white border was added to each side of the paired images.
7. The final images were stored at a resolution of 820 × 580.

Variations in UAV attitude, camera distortion, viewpoint, and heterogeneous
imaging mechanisms inevitably introduce local pixel-level spatial
discrepancies between the two modalities.

Since these discrepancies represent a practical challenge in RGB-T UAV object
detection, they are intentionally retained in DRTV30K. No further pixel-level
calibration is performed after center alignment.

---

## Annotation

Objects in DRTV30K are annotated using **Oriented Bounding Boxes (OBBs)**.

In UAV imagery, vehicles may appear at arbitrary orientations because of
different flight directions, camera angles, road layouts, and object poses.
Conventional horizontal bounding boxes often include substantial background
areas and cannot accurately describe the object orientation.

Therefore, oriented bounding boxes are adopted to provide tighter and more
accurate object localization.

An oriented bounding box can generally be represented as:

```text
(x_center, y_center, width, height, angle)
```

where:

- `x_center` and `y_center` denote the center coordinates of the object;
- `width` and `height` denote the dimensions of the bounding box;
- `angle` denotes the orientation of the object.

Please refer to the annotation-format documentation provided in this
repository for the exact coordinate representation and normalization rules
used in the released labels.

---

## Scene Distribution

DRTV30K covers six representative UAV observation environments.

| Scene Type | Number of Image Pairs |
|---|---:|
| Urban roads | 13,906 |
| Highways | 11,305 |
| Suburban areas | 2,996 |
| Parking lots | 1,137 |
| Overpasses | 1,062 |
| Bridges | 234 |
| **Total** | **30,640** |

The diversity of scenes introduces variations in background appearance,
traffic density, object distribution, road structure, and spatial layout.

---

## Illumination and Weather Conditions

The dataset contains four major illumination and weather conditions.

| Condition | Number of Image Pairs |
|---|---:|
| Daytime | 13,570 |
| Night | 13,104 |
| Dark night | 3,425 |
| Foggy | 541 |
| **Total** | **30,640** |

Daytime and nighttime samples account for comparable portions of the dataset.
Dark-night and foggy images provide more challenging conditions in which the
visible modality may contain weak, incomplete, or degraded object information.

These data are particularly useful for studying the complementary properties
of visible and thermal infrared modalities.

---

## Flight Altitude Distribution

DRTV30K was collected at UAV flight altitudes ranging from 50 to 180 meters.

| Flight Altitude | Number of Image Pairs |
|---|---:|
| 50–70 m | 10,048 |
| 70–100 m | 4,896 |
| 100–150 m | 12,185 |
| 150–180 m | 3,511 |
| **Total** | **30,640** |

The wide altitude range introduces substantial variations in object scale,
appearance details, target density, and background coverage.

---

## Dataset Statistics

<p align="center">
  <img src="assets/drtv30k_statistics.png" width="90%">
</p>

<p align="center">
  <em>
    Distribution of scene types, illumination conditions, and UAV flight
    altitudes in DRTV30K.
  </em>
</p>

> The statistical visualization will be added soon.

---

## Recommended Dataset Organization

The exact directory names should follow the released archive. A recommended
organization is shown below:

```text
DRTV30K/
├── train/
│   ├── rgb/
│   │   ├── images/
│   │   └── labels/
│   └── thermal/
│       ├── images/
│       └── labels/
├── val/
│   ├── rgb/
│   │   ├── images/
│   │   └── labels/
│   └── thermal/
│       ├── images/
│       └── labels/
├── test/
│   ├── rgb/
│   │   ├── images/
│   │   └── labels/
│   └── thermal/
│       ├── images/
│       └── labels/
├── split_files/
├── class_names.txt
└── README.md
```

Each visible image should have a corresponding thermal infrared image with the
same sample identifier.

> Please revise this example if the directory structure of the final released
> archive is different.

---

## Standard Benchmark Protocol

The standard DRTV30K benchmark evaluates oriented object detection using the
following seven categories:

```text
0: Car
1: Freight Car
2: Truck
3: Van
4: Tricycle
5: Bus
6: Construction Vehicle
```

The standard benchmark does not include:

```text
7: Pickup
8: Emergency Vehicle
```

Pickup and Emergency Vehicle are released as rare categories for few-shot,
long-tailed, and small-sample detection research.

The recommended standard evaluation setting includes:

- Oriented bounding box detection
- Category-wise Average Precision
- Mean Average Precision
- Intersection over Union threshold of 0.5
- Official training, validation, and test splits
- Seven standard benchmark categories

Researchers should clearly state whether their results are based on:

- The standard seven-category benchmark;
- A nine-category long-tailed setting;
- A few-shot setting involving Pickup and Emergency Vehicle;
- Another customized evaluation protocol.

This distinction is important for ensuring fair comparison between different
methods.

---

## Few-Shot Evaluation

DRTV30K additionally provides two rare categories:

| Category | Number of Instances |
|---|---:|
| Pickup | 395 |
| Emergency Vehicle | 54 |

These categories can be used to construct different few-shot or long-tailed
evaluation protocols.

Possible research settings include:

- Base-to-novel category transfer
- Few-shot fine-tuning
- Rare-category detection
- Long-tailed multimodal detection
- Category-incremental detection
- Cross-modal few-shot learning

Since no single few-shot protocol is currently enforced, researchers should
report their data split, number of shots, sampling strategy, and evaluation
metrics when using these two categories.

Official few-shot evaluation protocols may be added in future updates.

---

## Download

DRTV30K can be downloaded from Baidu Netdisk:

### Baidu Netdisk

[Download DRTV30K](https://pan.baidu.com/s/1Jpj87JUGjJPDQNpt798jog?pwd=d884)

```text
Extraction code: d884
```

Please verify the integrity of the downloaded files before use.

Additional download mirrors may be added in future updates.

---

## Usage Notes

Before training or evaluating a model on DRTV30K, please note the following:

1. Visible and thermal infrared images are paired by sample identifier.
2. Local spatial discrepancies between modalities are intentionally retained.
3. The standard benchmark contains seven categories.
4. Pickup and Emergency Vehicle are excluded from standard benchmark
   evaluation.
5. Pickup and Emergency Vehicle remain available for few-shot and long-tailed
   learning.
6. The annotations use oriented bounding boxes.
7. The official dataset split should be used for standard comparisons.
8. Researchers should clearly state their category setting and evaluation
   protocol when reporting results.

---

## Associated Paper

The dataset is introduced in the following work:

**Generative Alignment Network for Multimodal UAV Object Detection**

Wentao Wu, Chenglong Li*, Ziwen Wang, Zhaodong Ding, Xiao Wang, and Bin Luo

The formal publication information will be updated after the paper becomes
publicly available.

This repository currently focuses on the public release and documentation of
the DRTV30K dataset. Experimental results from the associated paper are not
included at this stage.

---

## Citation

The formal citation will be updated after the associated paper is published.

Before publication, please cite the dataset repository using the following
entry:

```bibtex
@misc{wu2026drtv30k,
  title        = {DRTV30K: A Large-Scale Multimodal UAV Object Detection Dataset},
  author       = {Wentao Wu and Chenglong Li and Ziwen Wang and
                  Zhaodong Ding and Xiao Wang and Bin Luo},
  year         = {2026},
  howpublished = {\url{https://github.com/Vehicle-AHU/DRTV30K}},
  note         = {RGB-T UAV object detection dataset}
}
```

After the associated paper is published, please use the official paper
citation provided in this repository.

---

## License and Terms of Use

DRTV30K is released for academic research and educational purposes.

By downloading or using the dataset, users should:

- Use the dataset only for lawful research and educational purposes;
- Follow the license and usage terms provided in this repository;
- Properly cite the dataset and associated publication;
- Avoid redistributing the dataset without permission;
- Avoid using the dataset in ways that violate privacy, legal, or ethical
  requirements;
- Clearly state any modifications made to the original dataset or annotations.

The final license file will be provided in this repository.

> Please replace this section with the final approved dataset license before
> the official release.

---

## Contact

For questions about the dataset, annotations, or evaluation protocol, please
contact:

**Wentao Wu**

**Chenglong Li**  
Corresponding author  
Email: `lcl1314@foxmail.com`

You may also submit an issue through this GitHub repository.

---

## Acknowledgements

We thank all contributors involved in UAV data collection, multimodal video
preprocessing, data screening, oriented bounding box annotation, and dataset
quality inspection.
