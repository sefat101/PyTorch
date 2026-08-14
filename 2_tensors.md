# What are Tensors?

A **tensor** is a specialized multi-dimensional array designed for mathematical and computational efficiency. It is the fundamental data structure used in deep learning.

---

## Dimensions and Real-World Examples

Tensors are categorized by their **rank**, which corresponds to their number of dimensions. 

### 1. Scalars (Rank 0 / 0-Dimensional Tensors)
*   **Definition:** Represents a single value or number. Often used for simple metrics or constants.
*   **Example:** A **Loss value**. After a forward pass, the loss function computes a single scalar value indicating the difference between predicted and actual outputs. 
*   **Mathematical Example:** `5.0` or `-3.14`.

### 2. Vectors (Rank 1 / 1-Dimensional Tensors)
*   **Definition:** Represents a sequence or a list/collection of values.
*   **Example:** A **Feature vector** in natural language processing. Each word in a sentence may be represented as a 1D vector using embeddings.
*   **Mathematical Example:** `[0.12, -0.84, 0.33]` (e.g., a word embedding from Word2Vec or GloVe).

### 3. Matrices (Rank 2 / 2-Dimensional Tensors)
*   **Definition:** Represents tabular or 2D grid-like data. 
*   **Example:** **Grayscale images**. A grayscale image can be represented as a 2D tensor, where each entry corresponds to a pixel intensity.
*   **Mathematical Example:** 
    ```text
    [[0, 255, 128],
     [34, 90, 180]]
    ```

### 4. 3D Tensors
*   **Definition:** Adds a third dimension, often used for stacking data. 
*   **Example:** **Coloured (RGB) Images**. A single RGB image is represented as a 3D tensor consisting of (width $\times$ height $\times$ channels).
*   **Shape Example:** An RGB image of size 256x256 would have a shape of `[256, 256, 3]`.

### 5. 4D Tensors
*   **Definition:** Adds batch size as an additional dimension to 3D data.
*   **Example:** **Batches of RGB Images**. A dataset of coloured images is represented as a 4D tensor: (batch size $\times$ width $\times$ height $\times$ channels).
*   **Shape Example:** A batch of 32 images, each 128x128 with 3 colour channels, would have a shape of `[32, 128, 128, 3]`.

### 6. 5D Tensors
*   **Definition:** Adds a time dimension for data that changes over time. 
*   **Example:** **Video data**. Video clips are represented as a sequence of frames, where each frame is an RGB image.
*   **Shape Example:** A batch of 10 video clips, each with 16 frames of size 64x64 and 3 channels, would have a shape of `[10, 16, 64, 64, 3]`.

---

## Why Are Tensors Useful?

1.  **Mathematical Operations:** Tensors enable the efficient mathematical computations (like addition, multiplication, and dot products) that are necessary for neural network operations.
2.  **Representation of Real-world Data:** Diverse data formats can be represented natively as tensors:
    *   **Images:** 3D tensors (width $\times$ height $\times$ channels).
    *   **Text:** Tokenized and represented as 2D or 3D tensors (sequence length $\times$ embedding size).
3.  **Efficient Computations:** Tensors are optimized specifically for hardware acceleration. They allow computations to be performed on GPUs or TPUs, which is crucial for training deep learning models efficiently.

---

## Where Are Tensors Used in Deep Learning?

1.  **Data Storage:** All training data (images, text, etc.) is stored in tensors before being fed into a model.
2.  **Weights and Biases:** The learnable parameters of a neural network itself (the weights and biases) are stored as tensors.
3.  **Matrix Operations:** Neural networks fundamentally involve operations like matrix multiplication, dot products, and broadcasting—all of which are performed using tensors.
4.  **Training Process:**
    *   During forward passes, tensors flow through the network from input to output.
    *   During the backward pass, gradients (which are also represented as tensors) are calculated to update the model.
