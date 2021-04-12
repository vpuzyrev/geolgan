## Geophysical model generation with GANs

Deep neural networks are widely used for estimation of subsurface parameters from geophysical measurements. To be efficient, they require large training datasets consisting of hundreds of thousands to millions of different models. This is not often possible with real data or manually generated models. A recent approach to artificial data generation based on generative adversarial networks (GANs) can be used to address this problem.<br>

We present a generator of 2D subsurface models based on StyleGAN2 (Karras, Laine, et al., 2020) and StyleGAN2 with adaptive discriminator augmentation (ADA, Karras, Aittala, et al., 2020) and apply it to the generation of synthetic density and stratigraphy models. As a training set, we use a representative set of subsurface models generated using Badlands modelling code. Once our GANs are trained and reach a sufficient degree of accuracy, they can be used to generate in real-time sufficiently detailed and varied artificial geological models. This allows creating multiple synthetic density and stratigraphy models in a cost-effective manner. A similar approach can be used to create subsurface models with different physical properties such as velocity models. The proposed method can serve as a useful augmentation tool for various deep learning codes, thus facilitating the development of more advanced tools for real-time estimation of subsurface parameters from collected data.


## Requirements

* Linux and Windows are supported, but we recommend Linux for performance and compatibility reasons.
* 64-bit Python 3.6 or 3.7. We recommend Anaconda3 with numpy 1.14.3 or newer.
* We recommend TensorFlow 1.14, which we used for all experiments in the paper, but TensorFlow 1.15 is also supported on Linux. TensorFlow 2.x is not supported.
* On Windows you need to use TensorFlow 1.14, as the standard 1.15 installation does not include necessary C++ headers.
* 1&ndash;8 high-end NVIDIA GPUs with at least 12 GB of GPU memory, NVIDIA drivers, CUDA 10.0 toolkit and cuDNN 7.5.
* Docker users: use the [provided Dockerfile](./Dockerfile) to build an image with the required library dependencies.

The generator and discriminator networks rely heavily on custom TensorFlow ops that are compiled on the fly using NVCC. On Windows, the compilation requires Microsoft Visual Studio to be in `PATH`. We recommend installing [Visual Studio Community Edition](https://visualstudio.microsoft.com/vs/) and adding it into `PATH` using `"C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`.

## Getting started

Pre-trained networks are stored as `*.pkl` files in 'networks' folder


