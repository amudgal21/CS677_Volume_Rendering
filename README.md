# CS677 Volume Rendering

## Overview

The `CS677_Parallel_distribution_axis-aligned Volume Rendering using MPI` project implements parallel volume rendering using MPI (Message Passing Interface). This Python script performs ray casting on a volume dataset, partitioning the data across multiple processes to accelerate rendering. The script also visualizes the results and reports **volume rendering time**, cecomposition time , chunking time, **fraction of rays terminated early**, and **final rendered image of bounded area**.

## Features

- **Parallel Volume Rendering:** Efficiently processes large volume datasets using MPI.
- **Domain Partitioning:** Supports both 1D and 2D partitioning of the dataset in x-direction or in both x and y.
- **Ray Casting:** Computes rendered images based on color and opacity transfer functions using interpolation for all the points along each ray.
- **Performance Reporting:** Provides statistics on early ray termination and timing metrics of volume rendering.
- **Image Stitching:** All the subimages gathered from all the processes are stitched together to get a final image.

## Prerequisites

Make sure you have the following Python libraries installed:

- `mpi4py`: For MPI support in Python.
- `argparse` : For parsing directories and other input variables
- `numpy`: For numerical operations and handling large arrays.
- `matplotlib`: For visualizing and saving rendered images.
- `time`: For calculating time during different processes
- `os`: For getting dimension of the file

## Code Running
1.**Install the required libraries:**

    ```bash
    pip install -r requirements.txt
    ```

2. **Prepare input files:**

    - **Volume Dataset:** The raw volume dataset file (e.g., `dataset.raw`).
    - **Color Transfer Function:** A text file defining the color transfer function (e.g., `color_TF.txt`).
    - **Opacity Transfer Function:** A text file defining the opacity transfer function (e.g., `opacity_TF.txt`).

## Running the Script

Use `mpiexec` to run the script with the desired number of MPI processes. Replace `<num_processes>` with the number of processes you want to use.

```bash
mpiexec -n <num_processes> python3 volume_rendering.py <input_dataset> <partition_type> <step_size> <x_bound_min> <x_bound_max> <y_bound_min> <y_bound_max> <color_tf> <opacity_tf>
```

Here `<input_dataset>` is our .raw file , `<partition_type>` means whether we want to decompose our data in 1D OR 2D (so for 1D give "1" or else "2"),  `<stepsize>` is the size of the step that we take in z-direction while ray casting , `<x_bound>` and `<y_bound>` is the bound area that we want to render, `<color_tf>` is the color transfer fucntion file, and `<opacity_tf>` is the opacity transfer function file

## OUTPUT IMAGE
![2000](https://github.com/user-attachments/assets/197d5a08-4091-4ce6-9c8e-75fe94ef6ba6)
![time_2000x2000](https://github.com/user-attachments/assets/3817df47-d695-4742-a4e0-c9bdb12e67e6)

This is our output for 2000x2000x400.raw file using 32 processes, for 1D at 0.5 stepsize

![999x700_15_1_0 5](https://github.com/user-attachments/assets/dc73f51c-e1a1-42cf-b3a4-370968370f66)
This is our output for 1000x1000x200.raw file using 15 processes, for 1D at 0.5 stepsize
![time_999x700](https://github.com/user-attachments/assets/0d7ac258-3bbc-43ed-8a2b-d3cdb2f48783)





