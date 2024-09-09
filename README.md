# Aerial Image Deblurring using UNet Autoencoder

This project applies a **UNet Autoencoder** to remove motion blur from aerial images and restore them to a sharp state. The model was trained and tested on two distinct datasets. The performance was measured using the **PSNR (Peak Signal-to-Noise Ratio)** metric, which evaluates the quality of the reconstructed images compared to the original sharp images.

## Project Overview

The aim of this project is to reconstruct sharp aerial images from those affected by motion blur. Motion blur can occur frequently in aerial photography due to the movement of drones or aircraft. By training a UNet autoencoder, the project seeks to automatically remove the blur from these images and restore the fine details, making them suitable for applications like surveillance, mapping, and environmental monitoring.

The process involves training the model on artificially blurred images to teach it how to reverse blurring effects. After training, the model is tested on a separate dataset of real-world blurred images to evaluate its performance in a more realistic setting.

## Datasets

1. **Training Dataset - 10,000 Aerial Images**:
   - The training dataset contains **10,000 high-resolution aerial images** paired with their artificially blurred versions. The blur was introduced to simulate motion blur typically encountered in aerial photography, where the image is taken while the aircraft or drone is moving.
   - The dataset was used to train the UNet autoencoder to recognize and reverse the blurring patterns, enabling the model to reconstruct the sharp images.

2. **Test Dataset - 350 Real-World Blurred and Sharp Images**:
   - The test dataset consists of **350 motion-blurred aerial images** along with their corresponding sharp versions. These images come from real-world conditions where motion blur occurs naturally, as opposed to the artificially generated blur in the training set.
   - This dataset was used to evaluate the trained model’s ability to generalize and handle real-world blurring, which can be more complex than the artificial blur used during training.

## Model Architecture

The **UNet Autoencoder** was chosen for this task due to its ability to perform well in image-to-image translation problems, particularly for tasks like image segmentation and restoration. The UNet architecture uses a combination of convolutional layers and upsampling layers, which allows it to capture both high-level and low-level features of an image.

- **Encoder**: The downsampling part of the network extracts key features while reducing the spatial dimensions of the image.
- **Bottleneck**: The center part of the network represents the most compressed version of the input image, capturing abstract features.
- **Decoder**: The upsampling part of the network reconstructs the image by increasing the spatial dimensions, ultimately producing the restored sharp image.

## Process

1. **Data Preparation**:
   - The training data was created by applying motion blur to the original aerial images. This allowed the model to learn the relationship between blurred and sharp images, focusing on the details lost due to motion blur.
   - Images were resized and normalized to ensure consistent input for the model.

2. **Training**:
   - The model was trained on the **10,000-image dataset**, where each blurred image was paired with its sharp counterpart.
   - The training process involved minimizing the difference between the predicted (reconstructed) sharp image and the actual sharp image using **Mean Squared Error (MSE)** as the loss function.
   - During training, the model learned to identify blurring patterns and how to reverse them to produce clear, sharp images.

3. **Testing**:
   - After training, the model was evaluated on the **350-image test dataset** of real-world motion-blurred images.
   - The performance was measured using **PSNR (Peak Signal-to-Noise Ratio)**, which quantifies how closely the reconstructed image matches the original sharp image.

## Results

- **Training Dataset**:
  - The model performed well on the **10,000-image training dataset**, achieving an average PSNR of **33 dB**. This indicates that the model was able to accurately reconstruct sharp images from artificially blurred inputs.
  - The high PSNR values suggest that the model learned to reverse the artificial blur effectively, restoring fine details and producing images close to the original sharp versions.

- **Test Dataset**:
  - On the **350 real-world blurred images**, the model achieved an average PSNR of **10-11 dB**. This is significantly lower than the training dataset’s results, indicating that the model struggled to generalize to the real-world blurring patterns.
  - The lower PSNR values suggest that the blur in the test dataset may have been more complex than the artificial blur used during training. Real-world motion blur can vary in intensity, direction, and complexity, making it harder for the model to accurately restore the images.

- **Comparison with Other Models**:
  - The PSNR results achieved by the UNet model were lower compared to state-of-the-art models reported in similar tasks, such as **DeepDeblur**, which achieved PSNR values over **25 dB** on similar datasets.
  - This performance gap is likely due to the differences in dataset size, the complexity of the motion blur, and the model architecture used.

## Conclusion

The UNet autoencoder performed well on the dataset it was trained on, achieving high PSNR values and effectively reconstructing sharp images from artificial blur. However, when applied to real-world motion-blurred images, the performance was significantly lower. This suggests that while the model is capable of handling artificial blurring, it struggles to generalize to more complex, natural blurring conditions.

The lower performance on the real-world dataset highlights the challenge of handling varying types of motion blur, as well as the limitations of training on artificially generated data.

## Future Improvements

1. **Expand and Diversify the Dataset**:
   - One of the key limitations of the current model is its training on artificially blurred images. Expanding the training dataset to include real-world blurred images would help the model generalize better to different types of motion blur encountered in aerial photography.

2. **Advanced Data Augmentation**:
   - To improve the robustness of the model, more advanced **data augmentation techniques** could be applied during training. For example, introducing various blur intensities, directions, and patterns could help the model learn to handle a wider range of blurring effects.

3. **Experimenting with Specialized Architectures**:
   - Exploring more advanced architectures like **DeepDeblur** or models that use **attention mechanisms** could improve the model’s ability to reconstruct fine details, especially in complex aerial imagery where motion blur varies significantly across the image.

4. **Fine-Tuning on Real Aerial Data**:
   - Fine-tuning the model on real aerial photography datasets, rather than relying solely on artificially blurred images, could improve the model’s real-world performance. This would allow the model to adapt better to the specific challenges of aerial photography, such as varying altitudes, lighting conditions, and atmospheric effects.

5. **Real-Time Application for Aerial Photography**:
   - Future work could also focus on optimizing the model for **real-time deblurring** in aerial photography. This would be particularly useful in drone-based applications, where clear images are critical for navigation, mapping, or surveillance.

## How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/Aerial-Image-Deblurring.git
cd Aerial-Image-Deblurring
