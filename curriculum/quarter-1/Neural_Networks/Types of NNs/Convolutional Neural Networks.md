A **Convolutional Neural Network (CNN)**, or **ConvNet**, is a specialized type of MLP network that's exceptionally good at working with **image data**. Input is not numerical, but **n-dimensional** like matrices. 

Its edges do not connect every node and unlike the MLP, which treats every pixel as an independent input, the CNN uses a clever structure to recognize the spatial relationships between nearby pixels.

![[CNN_example_1.png]]

### Noteworthy Specific CNN Models

Architectures known for performance and efficiency:
- [[Inception]] 
- [[ResNet]]

### Novel Architectures

Two novel architectures are also highlighted:

- **DeepFreqNet**: A new architecture that leverages **frequency-domain features**, making it adaptable to domains like medical imaging and sign language recognition.
  
- **Information Set based CNN (ISCNN)**: A CNN variant that introduces modified pooling and connection layers to improve robustness, particularly against noisy data.