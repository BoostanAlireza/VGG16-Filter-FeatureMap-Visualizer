## Enhanced VGG16 Visualization: Filters and Feature Maps

This project provides an educational, visual walkthrough of how Convolutional Neural Networks (CNNs) learn hierarchical features from images using the pre-trained VGG16 model. The notebook loads VGG16 (trained on ImageNet), visualizes first-layer filters, and extracts/plots feature maps from multiple convolutional layers to show how feature complexity increases with network depth.

### Key Highlights
- **Model**: VGG16 pre-trained on ImageNet
- **Visualizations**:
  - First-layer learned filters (edge/color detectors)
  - Feature maps from multiple layers (e.g., `block1_conv1`, `block2_conv1`, `block3_conv1`)
  - Side-by-side comparison of shallow vs deep layer activations
- **Saved outputs**: Figures are exported to image files for easy inspection

---

## Project Structure

- `vgg16_1.ipynb`: Main notebook containing all code and explanations
- `README.md`: This documentation
- Output images created at runtime:
  - `01_original_image.png`
  - `02_first_layer_filters.png`
  - `03_feature_maps_<layer_name>.png` (one per visualized layer)
  - `04_hierarchical_comparison.png`

---

## Requirements

Tested on Windows 10 with Python 3.12.

Python packages:
- `tensorflow>=2.19` (includes Keras)
- `numpy`
- `matplotlib`
- `pillow` (for image loading)

Install with pip:

```bash
python -m pip install "tensorflow>=2.19,<3" numpy matplotlib pillow
```

Optional (to run Jupyter locally):

```bash
python -m pip install notebook
```

## Getting Started

1) Clone or download this repository and open a terminal in the project folder.

2) Ensure dependencies are installed (see Requirements).

3) Provide an input image:
- Place an image file named `me.jpg` in the project root, or
- Edit the notebook where `load_and_preprocess_image('me.jpg')` is called to point to your image path.

4) Launch Jupyter and open the notebook:

```bash
python -m notebook
```

Then open `vgg16_1.ipynb` and run cells top-to-bottom.

Alternatively, you can run the notebook in VS Code, PyCharm, or upload to Google Colab.

---

## What the Notebook Does

1) **Load VGG16**: Downloads VGG16 weights (first run only) and prints the layer summary.

2) **Analyze Convolutional Layers**: Iterates through model layers to report filter counts and shapes for all convolutional layers.

3) **Load and Preprocess Image**: Loads `me.jpg`, resizes to 224×224, applies VGG16 preprocessing.

4) **Visualize First-Layer Filters**: Normalizes and plots filters from the first conv layer (separate RGB channels), saving `02_first_layer_filters.png`.

5) **Visualize Feature Maps**: Builds feature-extractor submodels for selected layers and plots `num_features` activations on an `grid_size × grid_size` grid, saving images like `03_feature_maps_block1_conv1.png`.

6) **Compare Layer Depths**: Side-by-side comparison of activations from shallow, mid, and deep layers; saves `04_hierarchical_comparison.png`.

7) **Key Takeaways**: Prints a concise summary of CNN concepts (hierarchical learning, filters as detectors, parameter sharing, etc.).

---

## Customization

- **Input image**: Change the filename/path in `load_and_preprocess_image(...)`.
- **Layers to visualize**: Edit the `layers_to_visualize` list in the feature maps section. Examples:
  - `('block1_conv1', 64, 8)` — early layer (edges/colors)
  - `('block2_conv1', 64, 8)` — mid layer (textures/shapes)
  - `('block3_conv1', 64, 8)` — deeper layer (more complex patterns)
- **Number of features/grid**: Adjust `num_features` and `grid_size` to control how many feature maps are displayed and the layout.
- **Colormap/style**: Change Matplotlib style and colormap to taste (e.g., `plt.style.use(...)`, `cmap='viridis'`).

---

## Expected Outputs

After running all cells successfully, you should see:
- The original image preview and `01_original_image.png`
- First-layer filter visualizations in `02_first_layer_filters.png`
- Feature maps per selected layer in files like `03_feature_maps_block1_conv1.png`
- A three-panel comparison in `04_hierarchical_comparison.png`

---

## Troubleshooting

- **FileNotFoundError: 'me.jpg' not found**
  - Ensure `me.jpg` exists in the project root, or change the path in the notebook.

- **Model download is slow or fails**
  - Requires internet on first run to download VGG16 weights. Retry later or check firewall/proxy.

- **TensorFlow / Keras import errors**
  - Ensure you installed `tensorflow>=2.12`. If you also installed standalone `keras`, prefer relying on the TensorFlow-bundled Keras to avoid version mismatches.

- **Out-of-memory (OOM) on GPU**
  - Run on CPU, or configure GPU memory growth in TensorFlow. Close other GPU apps.

---

## References

- Simonyan, K., & Zisserman, A. (2014). Very Deep Convolutional Networks for Large-Scale Image Recognition. arXiv:1409.1556.
- Keras Applications: VGG16 documentation (`https://keras.io/api/applications/vgg/#vgg16-function`)

---

## License

- MIT

