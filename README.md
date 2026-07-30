# DRTV30K Dataset

<div align="center">

## DRTV30K: A Large-Scale RGBT UAV Object Detection Dataset

**Associated work:**  
**Generative Alignment Network for Multimodal UAV Object Detection**

Wentao Wu, Chenglong Li*, Ziwen Wang, Zhaodong Ding, Xiao Wang, and Bin Luo

Anhui University

</div>

---

## Introduction

DRTV30K is a large-scale multimodal UAV object detection dataset containing paired visible and thermal infrared images.

The dataset was collected from UAV top-view perspectives under diverse scenes, illumination conditions, and flight altitudes. It contains substantial cross-modal appearance differences and local spatial discrepancies caused by different imaging mechanisms, camera configurations, UAV attitude variations, and camera distortion.

DRTV30K is designed to support research on:

- RGB-thermal multimodal object detection
- UAV-based vehicle detection
- Cross-modal alignment and fusion
- Small and oriented object detection
- Detection under low-light and adverse conditions
- Long-tailed and few-shot object detection

The dataset provides oriented bounding box annotations for nine vehicle categories.

---

## News

- **2026-XX-XX:** DRTV30K is publicly released.
- The associated paper and source code will be updated after they become publicly available.

---

## Dataset Overview

| Attribute | Description |
|---|---:|
| Paired RGBT images | 30,640 pairs |
| Total images | 61,280 |
| Annotated objects | 224,619 |
| Object categories | 9 |
| Annotation type | Oriented Bounding Box |
| Stored image resolution | 820 × 580 |
| Flight altitude | 50–180 m |
| Training set | 20,453 pairs |
| Validation set | 2,037 pairs |
| Test set | 8,150 pairs |

Each sample contains a visible image and its corresponding thermal infrared image.

Although the paired videos were manually pre-aligned during preprocessing, local pixel-level discrepancies between the two modalities were intentionally retained. These discrepancies reflect practical challenges in real-world RGBT UAV perception.

---

## Dataset Visualization

<p align="center">
  <img src="assets/drtv30k_overview.png" width="95%">
</p>

<p align="center">
  <em>Examples of paired visible-thermal images, oriented bounding box annotations, and representative instances from the nine object categories.</em>
</p>

> The visualization image will be added soon.

---

## Object Categories

DRTV30K contains the following nine vehicle categories:

1. Car
2. Freight Car
3. Truck
4. Van
5. Tricycle
6. Bus
7. Construction Vehicle
8. Pickup
9. Emergency Vehicle

The number of oriented bounding box annotations for each category is shown below.

| Category | Number of Instances |
|---|---:|
| Car | 194,514 |
| Freight Car | 10,397 |
| Truck | 8,161 |
| Van | 6,938 |
| Tricycle | 2,029 |
| Bus | 1,176 |
| Construction Vehicle | 955 |
| Pickup | 395 |
| Emergency Vehicle | 54 |
| **Total** | **224,619** |

The Pickup and Emergency Vehicle categories contain relatively few samples and can also support research on long-tailed recognition, few-shot detection, and small-sample learning.

---

## Data Split

The dataset is divided into training, validation, and test sets.

| Split | Number of RGBT Pairs | Number of Images |
|---|---:|---:|
| Training | 20,453 | 40,906 |
| Validation | 2,037 | 4,074 |
| Test | 8,150 | 16,300 |
| **Total** | **30,640** | **61,280** |

The official split files are included in the released dataset.

---

## Data Collection

DRTV30K was collected using a **DJI Matrice 4T** UAV equipped with visible and thermal infrared cameras.

A total of 232 paired visible-thermal videos were collected from different regions. The visible camera records videos at 30 frames per second. The thermal camera has a pixel pitch of 12 μm and operates within an infrared wavelength range of 8–14 μm.

The data cover a wide range of practical UAV observation conditions, including:

- Urban roads
- Highways
- Suburban areas
- Parking lots
- Overpasses
- Bridges
- Daytime scenes
- Nighttime scenes
- Extremely dark nighttime scenes
- Foggy weather
- Multiple UAV flight altitudes

---

## Data Preprocessing

The visible and thermal cameras have different native spatial resolutions because of their distinct imaging mechanisms and sensor configurations.

The preprocessing procedure is summarized as follows:

1. Visible and thermal videos were paired according to their collection sequences.
2. Each video pair was manually center-aligned.
3. The paired videos were resized to a unified resolution of 720 × 480.
4. One frame pair was sampled every 100 frames to reduce scene redundancy.
5. Image pairs with poor imaging quality were manually removed.
6. A 50-pixel white border was added to each side of the images.
7. The final images were stored at a resolution of 820 × 580.

We did not perform additional pixel-level registration after center alignment. Therefore, the dataset retains realistic local misalignment caused by UAV attitude changes, camera distortion, viewpoint differences, and heterogeneous imaging mechanisms.

---

## Scene Distribution

DRTV30K covers six representative scene types.

| Scene | Number of Image Pairs |
|---|---:|
| Urban roads | 13,906 |
| Highways | 11,305 |
| Suburban areas | 2,996 |
| Parking lots | 1,137 |
| Overpasses | 1,062 |
| Bridges | 234 |
| **Total** | **30,640** |

---

## Illumination Conditions

The dataset contains four major illumination and weather conditions.

| Condition | Number of Image Pairs |
|---|---:|
| Daytime | 13,570 |
| Night | 13,104 |
| Dark night | 3,425 |
| Foggy | 541 |
| **Total** | **30,640** |

The large number of nighttime and dark-night samples makes DRTV30K suitable for evaluating multimodal detection under visible-modality degradation.

---

## Flight Altitude Distribution

The images were collected at flight altitudes ranging from 50 to 180 meters.

| Flight Altitude | Number of Image Pairs |
|---|---:|
| 50–70 m | 10,048 |
| 70–100 m | 4,896 |
| 100–150 m | 12,185 |
| 150–180 m | 3,511 |
| **Total** | **30,640** |

The altitude diversity introduces substantial variations in object scale and appearance.

---

## Dataset Statistics

<p align="center">
  <img src="assets/drtv30k_statistics.png" width="90%">
</p>

<p align="center">
  <em>Distribution of scene types, illumination conditions, and UAV flight altitudes in DRTV30K.</em>
</p>

> The statistical visualization will be added soon.

---

## Annotation

Objects are annotated using **Oriented Bounding Boxes (OBBs)**.

Compared with conventional horizontal bounding boxes, oriented bounding boxes provide more accurate localization for vehicles with arbitrary orientations in UAV imagery.

An oriented bounding box can be represented as:

```text
(x_center, y_center, width, height, angle)
