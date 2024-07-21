# Irvine Ranch Conservancy Animal Detection

This repository contains the code and resources for the Irvine Ranch Conservancy Animal Detection project. Follow the instructions below to clone the repository and get started.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Cloning the Repository](#cloning-the-repository)
- [Usage](#usage)
- [Folder 1 - IRC Images](#folder-1---irc-images)
- [Folder 2 - Inaturalist Images](#folder-2---inaturalist-images)
- [Folder 3 - Model Training](#folder-3---model-training)
- [Folder 4 - Model Deployment](#folder-4---model-deployment)

## Prerequisites

Before you begin, ensure you have met the following requirements:
- You have installed [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
- You have a [GitHub](https://github.com) account.

## Cloning the Repository

To clone the repository, follow these steps:

1. **Open Terminal**

   Open your terminal (Linux, macOS) or Command Prompt (Windows).

2. **Navigate to Your Desired Directory**

   Use the `cd` command to change to the directory where you want to clone the repository. For example:
   ```sh
   cd /path/to/your/directory
3. **Clone Repository**

   Run the following command to clone the repository:
   ```sh
   git clone https://github.com/ttgminh/Irvine-Ranch-Conservancy-Animal-Detect.git
4. **Navigate into the repository directory**

   Change into the newly created repository:
   ```sh
   cd Irvine-Ranch-Conservancy-Animal-Detect

## Usage

Once you have cloned the repository, you can start using the code and resources for the project. Make sure to read any additional documentation or instructions provided in the repository for specific usage details.
   
## Folder 1 - IRC Images

The folder contains the script to process labeled images from Irvine Ranch Conservancy for ML ready training. Each image is corresponded with a txt file of the animal label and the bounding box coordinates. 

To run the script follow these steps:

1. Replace the input and output path in the script
2. Define Image size and ratio by editing the values. Default is 300 for image size and 70/30 for train/test ratio. Size is determined by the efficient net model type.

1. **Replace Paths**:
   - Update the script to include the correct input and output paths.

2. **Define Image Size and Ratio**:
   - Edit the script to set the desired image size and train/test ratio.
   - The default image size is 300.
   - The default train/test ratio is 70/30.
   - Note: The image size is determined by the EfficientNet model type.

| Model       | Image Size (px) |
|-------------|-----------------|
| EN-B0       | 224             |
| EN-B1       | 240             |
| EN-B2       | 260             |
| EN-B3       | 300             |
| EN-B4       | 380             |
| EN-B5       | 456             |
| EN-B6       | 528             |
| EN-B7       | 600             |
| EN-V2S      | 300             |
| EN-V2M      | 384             |
| EN-V2L      | 480             |
| MN-V3-S     | 224             |

After running the script, the images should be cropped, resized, squared accordingly.

## Folder 2 - Inaturalist Images


## Folder 3 - Model Training

## Folder 4 - Model Deployment


| Folder    | Description                              |
|:----------|:-----------------------------------------|
| `folder1` | Contains the main source code files.     |
| `folder2` | Contains image resources.                |
| `folder3` | Contains documentation and manuals.      |
| `folder4` | Contains test cases and test data.       |

   
