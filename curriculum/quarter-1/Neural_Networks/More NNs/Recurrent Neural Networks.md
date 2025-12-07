A **Recurrent Neural Network (RNN)** is a **type of neural network** built to handle **sequence data** where order matters (e.g., **text**, **speech**, **time series**).

Unlike Feedforward Networks (MLPs or CNNs), an RNN possesses **internal memory** via a **hidden state**. This state allows the network's current output to depend on **prior elements** in the sequence. Data is processed across **multiple time steps**, with the hidden state updated at each step based on the current input and the **previous state**.
![[RNNs_example_1.png]]