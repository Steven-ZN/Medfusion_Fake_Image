

# Medfusion Fake Image Generator

**Medfusion Fake Image Generator** is a project focused on generating synthetic medical images using Variational Autoencoders (VAE) and Diffusion Models. The primary goal is to improve medical image analysis through high-quality image generation, particularly for datasets with limited data. The project includes pre-trained models, custom data processing scripts, and support for integrating new datasets.

---

## Features

- **Customizable Medical Image Generation**: Generate high-quality synthetic images using advanced models.
- **Pretrained VAE and Diffusion Models**: Models optimized for datasets like BUSI and CheXpert.
- **Supports 2D and 3D Data Augmentation**: Enhance your dataset with various augmentation techniques.
- **Flexible Dataset Integration**: Easily integrate your own datasets with customizable configurations.



## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Steven-ZN/Medfusion_Fake_Image.git
   cd Medfusion_Fake_Image
   ```

2. **Install Dependencies**:
   Ensure you have Python 3.8+ and pip installed. Run:
   ```bash
   pip install -r requirements.txt
   ```

3. **Set Up Environment**:
   - Configure GPU and CUDA environment for faster training and inference.
   - Ensure you have at least one NVIDIA GPU with CUDA 11+ installed.



## Usage

### 1. Training the VAE
Train the Variational Autoencoder (VAE) on your dataset:
```bash
python scripts/train_latent_embedder_2d.py --config configs/vae_config.yaml
```

### 2. Generating Images with Diffusion Model
Once the VAE is trained, use it to train the diffusion model for image generation:
```bash
python scripts/train_diffusion.py --config configs/diffusion_config.yaml
```

### 3. Evaluate the Model
Evaluate generated images and embeddings:
```bash
python scripts/evaluate_images.py --checkpoint path/to/vae_checkpoint.pth
```

---

## Dataset Configuration

### Preprocessing the BUSI Dataset
1. Place your dataset under `data/` with the following structure:
   ```
   data/
   ├── train/
   │   ├── benign/
   │   ├── malignant/
   │   ├── normal/
   ├── validation/
   │   ├── benign/
   │   ├── malignant/
   │   ├── normal/
   ├── test/
   │   ├── benign/
   │   ├── malignant/
   │   ├── normal/
   ```

2. Run preprocessing:
   ```bash
   python scripts/helpers/sample_dataset.py --input data/ --output processed_data/
   ```

### Custom Dataset Integration
1. Add your dataset to the `data/` folder.
2. Modify the dataset loader in `medical_diffusion/data/datasets` to include your data parsing logic.
3. Update configurations in `configs/`.

---

## Customization

### Adjusting Input Size
To change the image resolution:
1. Update the `img_size` parameter in the VAE and diffusion model configuration files (`configs/vae_config.yaml` and `configs/diffusion_config.yaml`).
2. Example:
   ```yaml
   img_size: 512
   ```

### Using a Custom Optimizer
The project supports custom optimizers. Modify the optimizer settings in the configuration file:
```yaml
optimizer:
  type: CustomOptimizer
  params:
    lr: 0.001
    weight_decay: 0.0001
```

---

## Contributing

We welcome contributions! Feel free to:
1. Open issues for bugs or feature requests.
2. Submit pull requests with enhancements or fixes.

---

## Acknowledgments

This project uses concepts and resources from:
- BUSI and CheXpert datasets.
- Variational Autoencoders (VAEs) and Diffusion Models.

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for more details.

---

## Contact

For questions or collaborations, please reach out via [GitHub Issues](https://github.com/Steven-ZN/Medfusion_Fake_Image/issues).
```

This README provides a complete overview, setup instructions, and customization details for your project. Let me know if you need further refinements!
![Medfusion](https://github.com/user-attachments/assets/2b50a57c-cfa2-40cd-9b9e-abd84649ad99)
