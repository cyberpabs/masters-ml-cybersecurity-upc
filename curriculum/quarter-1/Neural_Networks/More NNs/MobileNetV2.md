MobileNetV2 is a highly efficient [[Convolutional Neural Networks|Convolutional Neural Network]] architecture designed by Google specifically for **mobile and embedded vision applications**. Its primary goal is to achieve high accuracy while requiring significantly **fewer parameters and computations** than traditional large models.

MobileNetV2's efficiency comes from a very specific and optimized architecture, centered around two main innovations: the **Inverted Residual Block** and the **Linear Bottleneck**.

![[MobileNet_vs_MobileNetV2.png|600]]

## Model structure details

**Table 1**: Bottleneck residual block transforming from $k$ to $k'$ channels, with stride $s$, and expansion factor $t$.

| **Input Dimension**                         | **Operator**                                    | **Output Dimension**                          |
| ------------------------------------------- | ----------------------------------------------- | --------------------------------------------- |
| $h \times w \times k$                       | $1 \times 1$ conv2d, ReLU6 (Expansion)          | $h \times w \times (t k)$                     |
| $h \times w \times t k$                     | $3 \times 3$ Depthwise conv (stride $s$), ReLU6 | $\frac{h}{s} \times \frac{w}{s} \times (t k)$ |
| $\frac{h}{s} \times \frac{w}{s} \times t k$ | Linear $1 \times 1$ conv2d (Projection)         | $\frac{h}{s} \times \frac{w}{s} \times k'$    |

**Table 2 MobileNetV2**: Each line describes a sequence of 1 or more identical (modulo stride) layers, repeated $n$ times. All layers in the same sequence have the same number $c$ of output channels. The first layer of each sequence has a stride $s$ and all others use stride 1. All spatial convolutions use $3 \times 3$ kernels. The expansion factor $t$ is always applied to the input size as described in Table 1.

| **Input**                | **Operator**        | ***t*** | ***c*** | ***n*** | ***s*** |
| ------------------------ | ------------------- | ------- | ------- | ------- | ------- |
| $224^2 \times 3$         | conv2d              | -       | 32      | 1       | 2       |
| $112^2 \times 32$        | bottleneck          | 1       | 16      | 1       | 1       |
| $112^2 \times 16$        | bottleneck          | 6       | 24      | 2       | 2       |
| $56^2 \times 24$         | bottleneck          | 6       | 32      | 3       | 2       |
| $28^2 \times 32$         | bottleneck          | 6       | 64      | 4       | 2       |
| $14^2 \times 64$         | bottleneck          | 6       | 96      | 3       | 1       |
| $14^2 \times 96$         | bottleneck          | 6       | 160     | 3       | 2       |
| $7^2 \times 160$         | bottleneck          | 6       | 320     | 1       | 1       |
| $7^2 \times 320$         | conv2d $1\times1$   | -       | 1280    | 1       | 1       |
| $7^2 \times 1280$        | avgpool $7\times 7$ | -       | -       | 1       | -       |
| $1 \times 1 \times 1280$ | conv2d $1\times1$   | -       | k       | -       |         |
