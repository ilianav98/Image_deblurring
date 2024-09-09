# Aerial Image Deblurring using UNet Autoencoder

This project uses a **UNet Autoencoder** to remove motion blur from aerial images, restoring them to a sharp state. The model was trained and tested on two different datasets, and its performance was evaluated using the **PSNR (Peak Signal-to-Noise Ratio)** metric.

## Datasets

1. **Training Dataset - 10,000 Aerial Images**:
   - This dataset consists of **10,000 high-resolution aerial images**, along with artificially blurred versions to simulate the effects of motion blur (e.g., capturing images from a moving aircraft or drone).
   - The dataset was used to train the UNet model, allowing it to learn how to reverse the blurring effect and reconstruct sharp images.

2. **Test Dataset - 350 Blurred/Sharp Image Pairs**:
   - This dataset consists of **350 real-world motion-blurred aerial images** paired with their corresponding sharp versions.
   - It was used to evaluate the trained model and assess its ability to generalize to real-world motion blur conditions.

## Running the Project

### 1. Clone the Repository

To get started, clone the repository to your local machine:

```bash
git clone https://github.com/yourusername/Aerial-Image-Deblurring.git
cd Aerial-Image-Deblurring
