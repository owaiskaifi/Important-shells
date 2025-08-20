# Important Shells

[![GitHub license](https://img.shields.io/github/license/owaiskaifi/Important-shells)](https://github.com/owaiskaifi/Important-shells/blob/main/LICENSE)
[![GitHub issues](https://img.shields.io/github/issues/owaiskaifi/Important-shells)](https://github.com/owaiskaifi/Important-shells/issues)
[![GitHub stars](https://img.shields.io/github/stars/owaiskaifi/Important-shells)](https://github.com/owaiskaifi/Important-shells/stargazers)

This repository contains a collection of essential Python scripts and shell utilities for basic image/XML operations commonly used in preparing custom datasets for deep learning model training. The scripts are designed to handle various computer vision tasks including annotation format conversions, object detection preprocessing, and dataset management.

## Table of Contents

- [Important Note](#important-note)
- [XML and Annotation Operations](#xml-and-annotation-operations)
- [Image Processing](#image-processing)
- [Dataset Utilities](#dataset-utilities)
- [System Tools](#system-tools)
- [Contributing](#contributing)

The code is sourced and adapted from various internet resources. Contributions and improvements are welcome!

## Important Note

⚠️ **Warning**: It is recommended to always make a copy of your data before using any script as a small mistake may delete your files/dataset.

⚠️ **Disclaimer**: The user is responsible for any loss/problem caused by these scripts.

---

## XML and Annotation Operations

### Draw Bounding Boxes on Images

This program draws bounding boxes on all images in a folder by reading their bounding box values from XML annotations (COCO format).

**Requirements:**
- Images and corresponding XML annotations in separate folders

**Usage:**
1. Download [draw_bounding_box_on_all_images.py](https://github.com/owaiskaifi/Important-shells/blob/master/draw_bounding_box_on_all_images.py)
2. Change the `imagesPath` and `xmlPath` variables in the script
3. Run the script:
   ```bash
   python draw_bounding_box_on_all_images.py
   ```

**Output:** Images with bounding boxes will be saved in the `bbimages` folder.

--- 

### Count Total Objects in PASCAL VOC XML Files

This program counts the total number of objects in all XML annotations in a folder.

**Usage:**
1. Download [countObjects_In_XML.py](https://github.com/owaiskaifi/Important-shells/blob/master/countObjects_In_XML.py)
2. Change the `xmlPath` variable in the script
3. Run the script:
   ```bash
   python countObjects_In_XML.py
   ```

**Output:** Displays total number of objects across all XML files.

---

### Count Specific Objects in PASCAL VOC XML Files 

This program counts the total number of objects as well as objects for each class in all XML annotations in a folder.

**Usage:**
1. Download [specific_ObjectsCounter_in_xmls.py](https://github.com/owaiskaifi/Important-shells/blob/master/specific_ObjectsCounter_in_xmls.py)
2. Change the `xmlPath` variable in the script
3. Update the class names to match your dataset (currently supports: person, car, truck, bus, motorbikes, bicycle, other)
4. Run the script:
   ```bash
   python specific_ObjectsCounter_in_xmls.py
   ```

**Output:** Displays total number of objects, per-class counts, and objects from other classes.

**Note:** Class names must match exactly with those in the XML files.

---

### Delete Single Object from PASCAL VOC XML Files

This program deletes objects from all XML annotations in a folder based on custom conditions (e.g., bounding boxes with xmin > xmax).

**Usage:**
1. Download [Delete_single_object.py](https://github.com/owaiskaifi/Important-shells/blob/master/Delete_single_object.py)
2. Change the input and output paths in the script
3. Modify the deletion conditions according to your needs
4. Run the script:
   ```bash
   python Delete_single_object.py
   ```

**Output:** Edited XML files will be saved in the specified output folder.

---

### Delete Specific Objects by Name from PASCAL VOC XML Files

This program deletes specific objects by name (e.g., 'person', 'car') from all XML annotations in a folder.

**Usage:**
1. Download [delete_objects_in_xml_by_name.py](https://github.com/owaiskaifi/Important-shells/blob/master/delete_objects_in_xml_by_name.py)
2. Change the input and output folder paths in the script
3. Specify the object names you want to delete (names must match exactly with XML content)
4. Run the script:
   ```bash
   python delete_objects_in_xml_by_name.py
   ```

**Output:** Edited XML files will be saved in the specified output folder.

---

### Clean Empty PASCAL VOC XML Files 

This program identifies and optionally deletes XML annotations that contain no objects, which can cause issues during AI model training.

**Usage:**
1. Download [count&Delete_XML_Dont_Have_objects.py](https://github.com/owaiskaifi/Important-shells/blob/master/count%26Delete_XML_Dont_Have_objects.py)
2. Change the input path in the script
3. Run the script to see empty XML files:
   ```bash
   python count&Delete_XML_Dont_Have_objects.py
   ```
4. To delete empty XML files, uncomment line 30 in the script

**Recommendation:** First run without deletion to verify the files, then enable deletion.

---

### Rename Objects in PASCAL VOC XML Files

This program renames specific objects in XML annotations (e.g., rename 'pedestrian' to 'person').

**Usage:**
1. Download [rename_objects_in_xml.py](https://github.com/owaiskaifi/Important-shells/blob/master/rename_objects_in_xml.py)
2. Change the input and output paths in the script
3. Update the object name mappings (lines 21-29 in the script)
4. Run the script:
   ```bash
   python rename_objects_in_xml.py
   ```

**Output:** Renamed XML files will be saved in the specified output folder.

---

## Annotation Format Conversions

### Convert Darknet (.txt) to PASCAL VOC (.xml) 

This program converts Darknet (.txt) annotations to PASCAL VOC (.xml) format.

**Requirements:**
- TXT annotations and corresponding images in separate folders

**Usage:**
1. Download [Convert_TXT_to_XML.py](https://github.com/owaiskaifi/Important-shells/blob/master/Convert_TXT_to_XML.py)
2. Change the `input_txt_path` and `input_images_path` in the script
3. Update the class labels (lines 18-27) to match your annotations
4. Run the script:
   ```bash
   python Convert_TXT_to_XML.py
   ```

**Note:** The script maps numerical labels in TXT files to class names in XML files based on the position in the labels array.

**Output:** XML files will be generated in the specified output folder.

---

### Convert PASCAL VOC (.xml) to Darknet (.txt) 

This program converts PASCAL VOC (.xml) annotations to Darknet (.txt) format in a two-step process.

#### Step 1: Create Image Lists

**Requirements:**
- Organize your data in this structure:
  ```
  Dataset/VOCdevkit/VOC2007/
  ├── Annotations/          # Place XML files here
  ├── JPEGImages/           # Place images here  
  └── ImageSets/Main/       # Empty folder
  ```

**Usage:**
1. Download [2-1-split_voc_train_test_from_imgAndAnnotations.py](https://github.com/owaiskaifi/Important-shells/blob/master/2-1-split_voc_train_test_from_imgAndAnnotations.py)
2. Update the paths on lines 15-17 in the script
3. Place the script in `Dataset/VOCdevkit/VOC2007/` folder
4. Run the script:
   ```bash
   python 2-1-split_voc_train_test_from_imgAndAnnotations.py
   ```

**Output:** Creates `train.txt` and `val.txt` in the `Dataset/VOCdevkit/VOC2007/ImageSets/Main/` directory.

#### Step 2: Convert XML to TXT

**Usage:**
1. Download [2-2-Convert_xmlToTxt_voc_label.py](https://github.com/owaiskaifi/Important-shells/blob/master/2-2-Convert_xmlToTxt_voc_label.py)
2. Place the script in the `Dataset/` folder
3. Update the `classes` list in the script to match your XML annotations
4. Run the script:
   ```bash
   python 2-2-Convert_xmlToTxt_voc_label.py
   ```

**Important Notes:**
- Class names must exactly match those in your XML files
- TXT labels will be numbered based on class position (e.g., 'person' = 0, 'car' = 1)
- Only specified classes will be converted to TXT format

**Output:** TXT annotations will be generated in `Dataset/VOCdevkit/VOC2007/labels/` folder.

---

### Convert CSV to Darknet (.txt) 

This program converts annotations from CSV files to Darknet TXT format. Supports multiple conversion modes:

1. Multiple CSV files → Single TXT file
2. Multiple CSV files → Multiple TXT files  
3. Multiple entries from one CSV → One TXT file

**Usage:**
1. Download [Convert_csv2txt.py](https://github.com/owaiskaifi/Important-shells/blob/master/Convert_csv2txt.py)
2. Change the `input_folder_name` in the script
3. Modify the code according to your specific conversion needs
4. Run the script:
   ```bash
   python Convert_csv2txt.py
   ```

**Output:** TXT files will be saved in the same folder with `output.txt` name.

---

## Image Processing

### Convert Audio Formats

**Convert MP3 to PCM:**

This shell script converts all MP3 audio files in a folder to PCM format.

**Usage:**
1. Download [Convert_mp3_to_pcm.sh](https://github.com/owaiskaifi/Important-shells/blob/master/Convert_mp3_to_pcm.sh)
2. Place the script in the folder containing MP3 files
3. Run the script:
   ```bash
   sh Convert_mp3_to_pcm.sh
   ```

**Output:** PCM audio files will be saved in the same folder.

---

### Image Format Conversions

**Convert JPG to BGR:**

**Usage:**
1. Download [Ruyi-convert-jpg2bgr.py](https://github.com/owaiskaifi/Important-shells/blob/master/Ruyi-convert-jpg2bgr.py)
2. Update input and output paths (lines 3-4)
3. Run the script:
   ```bash
   python Ruyi-convert-jpg2bgr.py
   ```

**Convert JPG/RGB to YUV:**

**Usage:**
1. Download [Ruyi-convert-jpg2yuv.cpp](https://github.com/owaiskaifi/Important-shells/blob/master/Ruyi-convert-jpg2yuv.cpp)
2. Update the image path (line 13)
3. Compile and run using any C++ editor

**Convert YUV to JPG/RGB:**

**Usage:**
1. Download [Yuv2RGB.py](https://github.com/owaiskaifi/Important-shells/blob/master/Yuv2RGB.py)
2. Update input and output folder paths (lines 13-14)
3. Run the script:
   ```bash
   python Yuv2RGB.py
   ```

**Batch Convert PNG to JPG (and vice versa):**

Use this command to convert all images in a folder:
```bash
for i in images/*.png ; do convert "$i" "${i%.*}.jpg" ; done
```

---

## Dataset Utilities

### File Management

**Rename All Files in a Folder:**

**Usage:**
1. Download [Rename_all_files_in_folder.py](https://github.com/owaiskaifi/Important-shells/blob/master/Rename_all_files_in_folder.py)
2. Change the input folder path (line 3)
3. Modify the file extension if needed (currently set for .jpg images)
4. Run the script:
   ```bash
   python Rename_all_files_in_folder.py
   ```

**Rename Files in Two Folders (Keep Sequence):**

This script renames files in two different folders while maintaining the same sequence (useful for images and their corresponding annotations).

**Usage:**
1. Download [Rename_All_Files_And_Keep_Sequence.py](https://github.com/owaiskaifi/Important-shells/blob/master/Rename_All_Files_And_Keep_Sequence.py)
2. Update input and output folder paths (lines 23-27)
3. Run the script:
   ```bash
   python Rename_All_Files_And_Keep_Sequence.py
   ```

**Combine Two Images into One:**

This script combines all images from folder A with corresponding images from folder B.

**Usage:**
1. Download [Combine2ImagesInto1.py](https://github.com/owaiskaifi/Important-shells/blob/master/Combine2ImagesInto1.py)
2. Organize images into folders A and B
3. Run the script:
   ```bash
   python combineAB.py --fold_A ./A --fold_B ./B --fold_AB ./AB
   ```

**Output:** Combined images will be saved in the AB folder.

**Copy Corresponding Files:**

This script reads files from one folder and copies corresponding files from another folder based on filename matching.

**Usage:**
1. Download [CopyFiles_or_images.py](https://github.com/owaiskaifi/Important-shells/blob/master/CopyFiles_or_images.py)
2. Update input and output folder paths
3. Modify file extensions if needed (lines 20, 23)
4. Run the script:
   ```bash
   python CopyFiles_or_images.py
   ```

**Output:** Copied files will be saved in the `Copied` folder.

---

## System Tools

### CUDA and cuDNN Version Check

These commands help you check CUDA and cuDNN versions installed on Ubuntu:

**Check CUDA Version:**
```bash
cat /usr/local/cuda/version.txt
```
Output format: `Cuda compilation tools, release 10.0, V10.0.130` (version = 10.0)

**Check cuDNN Version:**

For installations using .tar file:
```bash
cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2
# or
cat /usr/include/cudnn.h | grep CUDNN_MAJOR -A 2
```

For cuDNN >= 8.0:
```bash
cat /usr/local/cuda/include/cudnn_version.h | grep CUDNN_MAJOR -A 2
```

For installations using .deb file:
```bash
cat /usr/include/cudnn_version.h | grep CUDNN_MAJOR -A 2
```

### Installation Guides

**Install CUDA, cuDNN and Caffe:**
- [Caffe Installation Guide 1](https://github.com/yixindu1573/Caffe-Installation-Ubuntu-16.04-cuda-9.0-cudnn-v7)
- [Caffe Installation Guide 2](https://github.com/IraAI/caffe-gpu-installation)
- [Additional Caffe Guide](http://installing-caffe-the-right-way.wikidot.com/start)

**Compile OpenCV in Ubuntu 16.04:**
- [OpenCV Compilation Guide](https://note.youdao.com/ynoteshare1/index.html?id=0626a4c9f331f1a70e85f355ce410824&type=note)

---

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

## License

This project is open source and available under the [MIT License](LICENSE).
