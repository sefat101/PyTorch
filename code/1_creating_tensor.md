# PyTorch Tensor Creation Functions

Based on the provided notes, here is a detailed breakdown of each PyTorch tensor creation function.

### 1. `torch.empty()`
*   **Explanation, Parameters, and Use Case:** This function is used to allocate memory for a tensor without initializing its values. The notes demonstrate this with `torch.empty(2,3)`, which passes two parameters to define a 2-by-3 matrix. The resulting variable `a` is shown to have the type `torch.tensor`. The primary use case is for performance optimization; it is the fastest way to create a tensor if you intend to immediately overwrite all the elements.
*   **Documentation Hints:** Because it does not initialize memory, the output will contain whatever random garbage values were previously stored in that memory block.
*   **Expected Output:** 
    ```text
    tensor([[ 1.042e-38, -2.431e+12,  0.000e+00],
            [ 4.312e-15,  1.111e+02, -1.000e-05]]) # (Arbitrary memory values)
    ```

### 2. `torch.zeros()`
*   **Explanation, Parameters, and Use Case:** This function generates a tensor filled entirely with zeros. The notes show the function written as `torch.zeoros(2,3)`, assigning the result to variable `b` and using two parameters to request a 2-by-3 shape. This is heavily used in machine learning for initializing biases, creating masking tensors, or padding data sequences.
*   **Documentation Hints:** By default, the values are created as 32-bit floating-point numbers (`torch.float32`), though you can change this using the `dtype` argument.
*   **Expected Output:**
    ```text
    tensor([[0., 0., 0.],
            [0., 0., 0.]])
    ```

### 3. `torch.ones()`
*   **Explanation, Parameters, and Use Case:** Similar to `zeros`, this function creates a tensor filled entirely with ones. The notes illustrate this with the call `torch.ones(2,3)`, requiring shape dimensions as its parameters. It is commonly used as a baseline multiplicative identity matrix, or when creating a baseline state for mathematical operations where a zero would destroy the data.
*   **Documentation Hints:** Like `torch.zeros()`, it defaults to float data types and accepts standard `device` and `requires_grad` keyword arguments.
*   **Expected Output:**
    ```text
    tensor([[1., 1., 1.],
            [1., 1., 1.]])
    ```

### 4. `torch.rand()` and `torch.manual_seed()`
*   **Explanation, Parameters, and Use Case:** `torch.rand()` generates a tensor with random numbers sampled from a uniform distribution between 0 and 1. The notes highlight that `torch.rand(2,3)` yields "every time diff vals" (different values on every run). However, by first calling `torch.manual_seed(100)` (which takes an integer seed parameter), the subsequent `torch.rand(2,3)` generates the "same vals" every time it is run. This is vital for initializing neural network weights and ensuring scientific reproducibility in ML experiments.
*   **Documentation Hints:** If you need random numbers from a standard normal distribution (mean 0, variance 1) instead of a uniform one, you should use `torch.randn()` instead.
*   **Expected Output:**
    ```text
    tensor([[0.1110, 0.5050, 0.4352],
            [0.9123, 0.1235, 0.7741]]) # (Values will be locked if seed 100 is set)
    ```

### 5. `torch.tensor()`
*   **Explanation, Parameters, and Use Case:** This function constructs a tensor directly from existing Python data structures. The notes show the parameter as a nested list: `([[1,2,3], [4,5,6]])`. This is used when you already have specific, hardcoded data (like a standard Python list or a NumPy array) and need to convert it into a PyTorch-compatible format to perform GPU-accelerated math.
*   **Documentation Hints:** `torch.tensor()` infers the data type automatically from the passed data. In this specific case, because the inputs are integers, the resulting tensor will have an `int64` data type.
*   **Expected Output:**
    ```text
    tensor([[1, 2, 3],
            [4, 5, 6]])
    ```

### 6. `torch.arange()`
*   **Explanation, Parameters, and Use Case:** Creates a 1D tensor with evenly spaced integer values across a given interval. The notes show `torch.arange(0, 10)`, which takes a start and end parameter. It is heavily used for creating indices, time steps, or loop counters natively within tensor formats.
*   **Documentation Hints:** The upper bound (the second parameter) is strictly exclusive. You can also pass a third parameter to define a custom step size (e.g., `step=2`).
*   **Expected Output:**
    ```text
    tensor([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
    ```

### 7. `torch.linspace()`
*   **Explanation, Parameters, and Use Case:** Creates a 1D tensor with linearly spaced floating-point values between a start and end point. The notes illustrate this with `torch.linspace(0, 10, ...)` (where the final parameter defines the number of steps). This is incredibly useful for generating coordinate spaces for graphing, sampling continuous functions, or interpolating values.
*   **Documentation Hints:** Unlike `arange()`, the `end` value in `linspace()` is inclusive. The third parameter dictates the total number of points generated, not the gap between them.
*   **Expected Output (assuming 5 steps):**
    ```text
    tensor([ 0.0000,  2.5000,  5.0000,  7.5000, 10.0000])
    ```

### 8. `torch.eye()`
*   **Explanation, Parameters, and Use Case:** Creates a 2D matrix with ones on the diagonal and zeros everywhere else, known mathematically as an identity matrix. The notes demonstrate `torch.eye(5)`, passing a single integer parameter to dictate a 5-by-5 shape. This is essential for specific linear algebra operations, maintaining transformations, or initializing specialized layers in deep learning.
*   **Documentation Hints:** If you provide two parameters instead of one (e.g., `torch.eye(n, m)`), you can create a rectangular matrix where the diagonal is still populated by ones.
*   **Expected Output:**
    ```text
    tensor([[1., 0., 0., 0., 0.],
            [0., 1., 0., 0., 0.],
            [0., 0., 1., 0., 0.],
            [0., 0., 0., 1., 0.],
            [0., 0., 0., 0., 1.]])
    ```

### 9. `torch.full()`
*   **Explanation, Parameters, and Use Case:** Creates a tensor of a specific shape populated entirely by a custom constant value. The notes show `torch.full((3,3), 5)`, which requires a shape tuple parameter `(3,3)` and a scalar fill value parameter `5`. This is useful when you need to initialize a system with a specific default weight, penalty value, or placeholder metric across multiple dimensions.
*   **Documentation Hints:** `torch.full` infers the data type from the fill value. Since `5` is passed as an integer, the tensor will be integer-based unless explicitly cast to a float.
*   **Expected Output:**
    ```text
    tensor([[5, 5, 5],
            [5, 5, 5],
            [5, 5, 5]])
    ```
