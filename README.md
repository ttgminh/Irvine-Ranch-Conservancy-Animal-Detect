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
2. Define Image size and train/test split ratio by editing the values. Default is 300 for image size and 70/30 for train/test ratio. Size is determined by the efficient net model type.

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
This folder includes the api script (`Inaturalist_API_Step1.ipynb`) and the image processing script (`Inaturalist_Data_Preprocessing_Step2.ipynb`). The two scripts will gather images from [Inaturalist](https://www.inaturalist.org/observations) and process the image for ML training ready like the step above. The process can be broken into 3 steps:

### Step 1: Inatualist API (`Inaturalist_API_Step1.ipynb`)

1. Gather the taxon ID and username from the site. The information can be found via the url of the site once you filter out the animal. An example can be found like below for mule deer(taxon_id=42220) from user sec_research.
   ```
   https://www.inaturalist.org/lifelists/sec_research?details_view=observations&taxon_id=42220

2. Input the given values according to the prompt of the script.
3. Image will begin downloading, repeat the step again for other species.

### Step 2: EcoAssist MegaDetector
In order for the image to be cropped, we need to identify where the animal is on the images. We can utilize the MegaDetector model in EcoAssist to identify the animals in the images. After processing, EcoAssist will generate a (`image_recognition_file.json`) file for us to use in further processing.

### Step 3: Inaturalist Image Processing (`Inaturalist_Data_Preprocessing_Step2.ipynb`)

1. Define the Image Size, Confidence Level, and split train/test ratio accordingly.
2. After running the script, two folders test and train will be created with corresponding processed images of the animals, you can now copy paste the images into the main train and test folder.


## Folder 3 - Model Training
We will be utilizing the [MEWC Training Pipeline](https://github.com/zaandahl/mewc-train/tree/main) for the training process. The pipline utilize a docker image for training a model. You can visit the github repo for more detailed information.

Prerequisites: This assumes you have all the processed images into a train folder and a test folder. After that is ready, here are the steps to train:

1. Create an (`ENV.txt`) file similar to the one given, specific environmenet variables are listed [here](https://github.com/zaandahl/mewc-train/tree/main).
2. Start Docker Engine.
3. Open Windows Powershell.
4. Run the following commands.
   ```
   docker pull zaandahl/mewc-train
   docker docker run --gpus all --env-file "path\\to\\your\\ENV\\file\\ENV.txt" --interactive --tty --rm --volume "path\\to\\your\\data\\folder:/data" zaandahl/mewc-train

## Folder 4 - Model Deployment
This folder contains a basic set up for a local deployment of the model we developed from the MEWC Pipeline. We will leverage the EcoAssist GUI for using our model. More detailed instructions of MEWC Model deployment can be found [here](https://github.com/PetervanLunteren/EcoAssist/blob/main/markdown/MEWC_integration.md).

Here are the general steps to deploy:

1. Locate the (`class_list.yaml`) and the (`mewc_model_300px_best.h5`) file from the output folder of MEWC training pipeline.
2. Create a (`variables.json`) file, this tells EcoAssist to grab our model for use.
3. Navigate to the EcoAssist backend (EcoAssist_files -> Models -> cls).
4. Create a new folder and name it appropriately.
5. Copy and paste all three files into the newly created folder.


## Your model is now be ready to use within EcoAssist, happy classifying!


   
