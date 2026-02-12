[[Intro to DS]]
## Image processing and Convolution
* example: image filtering with box filter
* ex: smoothening with box filter
The box filter is also known as a kernel
* usually a 3x3
The output (activation map) of convolution indicates whether a certain pattern is detected
* if yes, return high value(bright)
* If no, return low value(dark)
Many time, image resolution is shrunk since the original image isnt completely covered due to out of bound errors. To combat this, the original image is given padding to encapsulate the full image
![[Pasted image 20260122163531.png]]

#### Sobel Kernel: helps identify the vertical and horizontal edges in an image
* useful for cases like face/age recognition by seeing patterns in the vertical/horizontal images.

Kernel used to differentiate between cats and dogs: 

## CNNs:
#### Convolution Layer:
* 32x32x3 image: preserves spatial structure. (3=RGB, 3 depth)
* 5x5x3 filter(kernel): (again 3 for RGB depth)

these 2 layers in turn return 1 number by getting the dot product between filter (for each input taken from the original image) This is called an Activation Map

**for example if we had 6 5x5 filters, we'll get 6 separate activation maps (1 kernel for horizontal edges, vertical, etc** 

* CNN contains a sequence of Convolution layers interspersed with activation functions

Ex: lets say 7x7 input with 3x3 filter. the activation map becomes 5x5 because the border pixels can't be reached properly for the kernel
Ex2: lets say same scenario but step by 2 each time. the activation map is now 3x3

*Output size can be determined by:*
``` bash
Output size = (N-F)/stride+1 //no padding P=0
Output size = (N+2P-F)/stride+1 //P=padding

where 
P = padding
N = input dimension
F = kernel dimension
stride = stride length
```

Example: Input: 32x32x3 and 10 5x5 filters with stride 1, pad 2
Output volume size: 32x32x10 (bc of 10 filters)
(32+2\*2-5)/1+1 = 32 spacially
Number of parameters = 

## Summary
To summarize, the Conv Layer:
Live example: poloclub.github.io/cnn-explainer
- Accepts a volume of size **W₁ × H₁ × D₁**

- Requires four hyperparameters:
  - Number of filters **K**
  - Their spatial extent **F**
  - The stride **S**
  - The amount of zero padding **P**

- Produces a volume of size **W₂ × H₂ × D₂**, where:
  - **W₂ = (W₁ − F + 2P) / S + 1**
  - **H₂ = (H₁ − F + 2P) / S + 1**  
    *(i.e., width and height are computed equally by symmetry)*
  - **D₂ = K**

- With parameter sharing, it introduces:
  - **F · F · D₁** weights per filter  
  - For a total of **(F · F · D₁) · K** weights
  - And **K** biases

- In the output volume, the *d*-th depth slice (of size **W₂ × H₂**) is the result of:
  - Performing a valid convolution of the *d*-th filter over the input volume
  - Using stride **S**
  - Then offset by the *d*-th bias
