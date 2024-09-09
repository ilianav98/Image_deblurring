# Aerial Image Deblurring
# Aerial Image Deblurring Using UNet Autoencoder

This project focuses on using a **UNet Autoencoder** to sharpen aerial photos that were artificially degraded with motion blur. The model is trained to reverse the blurring effects and restore the images to their original sharp state. The results are evaluated using the **PSNR (Peak Signal-to-Noise Ratio)** metric.

## Project Overview

The goal of this project is to improve the quality of aerial images taken under conditions that cause motion blur. A pre-trained UNet model was applied to test datasets, and the results were evaluated and compared using the PSNR metric.

### Key Features

- **UNet Autoencoder Model**: The model is designed to remove motion blur from aerial images and reconstruct sharper versions of the images.
- **PSNR Evaluation**: The model’s performance is measured using the PSNR metric, which quantifies the accuracy of the reconstructed images compared to the ground-truth sharp images.

## Project Structure

- **`model/`**: Contains the pre-trained UNet model.
- **`scripts/`**: Python scripts used for training, testing, and evaluating the model.
- **`data/`**: Placeholder for the aerial image datasets (blurred and sharp images).
- **`results/`**: Folder containing the reconstructed images and evaluation metrics (PSNR results).
  
## Dataset

The dataset contains **350 blurred** and **350 sharp aerial images**. The blurred images simulate real-world conditions where motion blur occurs due to aircraft movement or drone instability.

## Installation

To run this project locally, follow the steps below:

1. **Clone the repository**:
    ```bash
    git clone https://github.com/yourusername/Aerial-Image-Deblurring.git
    cd Aerial-Image-Deblurring
    ```

2. **Install dependencies**:
    Install the necessary Python libraries:
    ```bash
    pip install -r requirements.txt
    ```

3. **Run the model**:
    You can run the testing script to evaluate the model on your data:
    ```bash
    python scripts/test_model.py --data_path /path/to/your/dataset
    ```

## Results

The results were evaluated using the PSNR metric. The model achieved an average PSNR of **10-11 dB** on the new dataset, which is lower than expected. However, when tested on the original training dataset, the PSNR was **around 33 dB**. The lower performance on the new dataset is likely due to the difference in the type of blur and dataset size.

## Future Work

1. **Expand the dataset**: Increase the variety and quantity of aerial images used for training.
2. **Improve model generalization**: Apply advanced data augmentation techniques to simulate a wider range of motion blur patterns.
3. **Experiment with specialized architectures**: Test more complex deblurring models such as DeepDeblur.
4. **Apply in real-time**: Explore real-time applications for drone-based aerial photography.
