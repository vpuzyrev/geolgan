## Geophysical model generation with GANs

Deep neural networks are widely used for estimation of subsurface parameters from geophysical measurements. To be efficient, they require large training datasets consisting of hundreds of thousands to millions of different models. This is not often possible with real data or manually generated models. A recent approach to artificial data generation based on generative adversarial networks (GANs) can be used to address this problem.<br>

We present a generator of 2D subsurface models based on StyleGAN2 (Karras, Laine, et al., 2020) and StyleGAN2 with adaptive discriminator augmentation (ADA, Karras, Aittala, et al., 2020) and apply it to the generation of synthetic density and stratigraphy models. As a training set, we use a representative set of subsurface models generated using Badlands modelling code (Salles et al., 2018). Once our GANs are trained and reach a sufficient degree of accuracy, they can be used to generate in real-time sufficiently detailed and varied artificial geological models. This allows creating multiple synthetic density and stratigraphy models in a cost-effective manner. A similar approach can be used to create subsurface models with different physical properties such as velocity models. The proposed method can serve as a useful augmentation tool for various deep learning codes, thus facilitating the development of more advanced tools for real-time estimation of subsurface parameters from collected data.


## Requirements

Re-training the networks will require the following (similar to https://github.com/NVlabs/stylegan2/):

* Linux and Windows are supported, but we recommend Linux for performance and compatibility reasons.
* 64-bit Python 3.6 or 3.7. We recommend Anaconda3 with numpy 1.14.3 or newer.
* We recommend TensorFlow 1.14, which we used for all experiments in the paper, but TensorFlow 1.15 is also supported on Linux. TensorFlow 2.x is not supported.
* On Windows you need to use TensorFlow 1.14, as the standard 1.15 installation does not include necessary C++ headers.
* 1&ndash;8 high-end NVIDIA GPUs with at least 12 GB of GPU memory, NVIDIA drivers, CUDA 10.0 toolkit and cuDNN 7.5.

## Getting started

Pre-trained networks are stored as `*.pkl` files in 'networks' folder

Running StyleGAN2 generator for stratigraphic models:

```.bash
python stylegan2/run_generator.py generate-images --network=networks/stylegan2-stratigraphy6000.pkl --seeds=0-100 --truncation-psi=0.50 --result-dir=OUTPUT_DIR
```

Running StyleGAN2 ADA generator for density models (change ADA_DIR to your StyleGAN2 ADA path):

```.bash
python ADA_DIR/run_generator.py --network=networks/stylegan2ada-density1000.pkl --seeds=0-100 --truncation-psi=0.50 --outdir=OUTPUT_DIR
```
