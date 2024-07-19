# Dataset_extraction - A complete step-by-step guide to extract the radar data and process it for time synchronisation.
# Radar and Camera Data Processing

## Step 1: Save the Raw File

Save the raw file in a folder named `data collected scene_wise`. For example, `solio_lrr`.

## Step 2: Extract Radar Data

Run `extract_rad.ipynb` to save each radar scan in a separate file with the folder name as the timestamp of the scan.

**Notes:**
- Store the sensor IDs in the variable `temp`.
- Change the variable `j` according to the scene that is captured.
- The output will be saved in the same folder as the source files, in the format `jth_scene-obj/25/`.

## Step 3: Process Radar Object Data

The notebook `extract_radar_obj.ipynb` removes redundant labels and aligns the data so that each column represents a feature of a single radar object detection from a particular scan.

### Features Identified:
1. X Distance
2. Y Distance
3. Standard Deviation in X Distance
4. Standard Deviation in Y Distance
5. Radial Cross-Section (RCS)
6. Velocity in X direction
7. Velocity in Y direction
8. Acceleration in X direction
9. Acceleration in Y direction
10. Standard Deviation of Velocity in X direction
11. Standard Deviation of Velocity in Y direction
12. Standard Deviation of Acceleration in X direction
13. Standard Deviation of Acceleration in Y direction

**Notes:**
- Provide the `parent_folder` in the format `jth_scene-obj` (where `j` represents the scene instance at which the data was collected).
  - Example: `parent_folder = "1th_scene-obj"`
- Provide the `folder_path` in the format `ith_scene-obj/25` to rename the file names to exclude the year, month, and date from the timestamp.
  - Example: `2024_06_15_16-01-01.412823.csv` becomes `16-01-01.412823.csv`.

## Step 4: Organize Data

Create folders to store the radar and camera images.

**Radar CSV Files:**
- Format: `radar_folder_name/front/20/... .csv`

**Camera Data:**
- Format: `camera_folder_name/cam_front/subset`

## Step 5: Synchronize Radar and Camera Data

Run the Python script `radar_camera_synch.ipynb` to perform the synchronization.

**Notes:**
- Provide the `camera_root_folder` and `radar_root_folder`.
  - Example: 
    - `camera_root_folder = '/home/rad-cam/solio_dataset/timestamps/camera'`
    - `radar_root_folder = '/home/rad-cam/solio_dataset/timestamps/radar'`

**Output:**
- `radar_timestamps.csv` file stored in the `radar/front` folder.
- `camera_timestamps.csv` file stored in the `camera/cam_front` folder.
- The synchronized file `Radar_Camera_Synch_front.csv` saved in the `radar/front` folder.
