<h1 style="text-align:center">torch</h1>

It's a Python-based scientific computing package targeted at two sets of audiences:
- A replacement for NumPy to use the power of GPUs
- a deep learning research platform that provides maximum flexibility and speed

**torch.Size** is in fact a tuple, so it supports all tuple operations.

**view/reshape**

**detach/clone**

If you have a one element tensor, use .item() to get the value as a Python number

```
x = torch.randn(1)
print(x)
print(x.item())
```

> 100+ Tensor operations, including transposing, indexing, slicing, mathematical operations, linear algebra, random numbers, etc.

**numpy/tensor**

All the Tensors on the CPU except a CharTensor support converting to NumPy and back.

```
import torch
a = torch.ones(5)
b = a.numpy()
import numpy as np
a = np.ones(5)
b = torch.from_numpy(a)
```

**cpu/gpu**

**save/load**

**Random sampling**

**有用的函数**

- torch.is_tensor(obj)
    - Returns True if obj is a PyTorch tensor.
- torch.set_default_dtype(d)
    - The default floating point dtype is initially torch.float32
- torch.get_default_dtype() -> torch.dtype
    - Get the current default floating point torch.dtype.
- torch.numel(input) -> int
    - Returns the total number of elements in the input tensor.
- torch.tensor(data, dtype=None, device=None, requires_grad=False, pin_memory=False) -> Tensor
    - torch.tensor() always copies data
    - torch.tensor(x) == x.clone().detach()
    - torch.tensor(x, requires_grad=True) == x.clone().detach().requires_grad_(True)
    - **data**: can be a list, tuple, NumPy, scalar
    - **requires_grad**: default: False
- torch.as_tensor(data, dtype=None, device=None) -> Tensor
    - 如果dtype和device相同，则不会进行拷贝，否则拷贝
- torch.from_numpy(ndarray) -> Tensor
    - Creates a Tensor from a numpy.ndarray.
- torch.zeros(*size, out=None, dtype=None, layout=torch.strided, device=None, requires_grad=False) -> Tensor
    - Returns a tensor filled with the scalar value 0
- torch.ones(*size, out=None, dtype=None, layout=torch.strided, device=None, requires_grad=False) -> Tensor
    - Returns a tensor filled with the scalar value 1
- torch.arange(start=0, end, step=1, out=None, dtype=None, layout=torch.strided, device=None, requires_grad=False) -> Tensor
    - Returns a 1-D tensor of size up(end - start / step)
- torch.linspace(start, end, steps=100, out=None, dtype=None, layout=torch.strided, device=None, requires_grad=False) -> Tensor
    - Returns a one-dimensional tensor of steps equally spaced points between start and end.
    - The output tensor is 1-D of size steps
- torch.logspace(start, end, steps=100, base=10.0, out=None, layout=torch.strided, device=None, requires_grad=False) -> Tensor
    - Returns a one-dimensional tensor of steps points logarithmically spaced with base(base between base^start and base^end)
    - The output tensor is 1-D of size steps
- torch.eye(n, m=None, out=None, dtype=None, layout=torch.strided, device=None, requires_grad=False) -> Tensor
    - Returns a 2-D tensor with ones on the diagonal and zeros elsewhere
- torch.empty(*size, out=None, dtype=None, layout=torch.strided, device=None, requires_grad=False, pin_memory=False) -> Tensor
    - Returns a tensor filled with unintialized data.
- torch.full(size, fill_value, out=None, dtype=None, layout=torch.strided, device=None, requires_grad=False) -> Tensor
    - Returns a tensor of size size filled with fill_value
- torch.cat(tensors, dim=0, out=None) -> Tensor
    - Concatenates the given sequence of seq tensors in the given dimension.
- torch.chunk(intput, chunks, dim=0) -> List of Tensors
    - Splits a tensor into a specific number os chunks.
    - Last chunk will be smaller if the tensor size along the given dimension dim is not divisible by chunks
- torch.index_select(input, dim, index, out=None) -> Tensor
    - Returns a new tensor which indexes the input tensor along dimension dim using the entries in index which is a LongTensor
    - index(LongTensor) - the 1-D tensor containing the indices to index
    - The returned tensor does not use the same storage as the original tensor.
- torch.masked_select(input, mask, out=None) -> Tensor
    - Returns a new 1-D tensor which indexes the input tensor according to the boolean mask *mask* which is a BoolTensor
    - The returned tensor does not use the same storage as the original tensor
    - mask(BoolTensor) - the tensor containing the binary mask to index with
- torch.narrow(input, dim, start, length) -> Tensor
    - Returns a new tensor that is a narrowed version of *input* tensor. The dimension *dim* is input from *start* to *start + length*.
    - The returned tensor and *input* tensor share the same underlying storage
- torch.nonzero(input, *, out=None, as_tuple=False) -> LongTensor or tuple of LongTensors
    - *as_tuple=False* Returns a tensor containing the indices of all non-zero elements of input.
    - *as_tuple=True* Returns as tuple of 1-D tensors, one for each dimension in *input*, each containing the indices of all non-zero elements of *input*
- torch.reshape(input, shape) -> Tensor
    - Returns a tensor with same data and number of elements as *input*, but with the specified shape.
- torch.split(input, split_size_or_sections, dim=0) -> Tensor
    - Splits the tensor into chunks. Each chunk is a view of the original tensor.
- torch.squeeze(input, dim=None, out=None) -> Tensor
    - Returns a tensor with all the dimensions of *input* of size 1 removed
    - The returned tensor shares the storage with the input tensor
- torch.stack(tensors, dim=0, out=None) -> Tensor
    - Concatenates sequence of tensors along a new dimension
    - All tensors need to be of the same size
- torch.t(input) -> Tensor
    - Expects *input* to be <= 2-D tensor and transposes dimensions 0 and 1
- torch.take(input, index) -> Tensor
    - Returns a new tensor with the elements of *input* at the given indices. The input tensor is treated as if it were viewed as a 1-D tensor.
- torch.transpose(input, dim0, dim1) -> Tensor
    - Returns a tensor that is a transposed version *input*
    - The resulting *out* tensor shares it's underlying storage with the *input* tensor
- torch.unsqueeze(input, dim) -> Tensor
    - Returns a new tensor with a dimension of size one inserted at the specified position.
    - The returned tensor shares the same underlying data with this tensor
- torch.where(condition, x, y) -> Tensor
    - Return a tensor of elements selected from either *x* or *y*, depending on *condition*
- torch.manual_seed(seed)
    - Sets the seed for generating random numbers.
- torch.rand(*size, out=None, dtype=None, layout=torch.strided, device=None, requires_grad=False) -> Tensor
    - Returns a tensor filled with random numbers from a uniform distribution on the interval [0, 1)
- torch.randn(*size, out=None, dtype=None, layout=torch.strided, device=None, requires_grad=False) -> Tensor
    - Returns a tensor filled with random numbers from a normal distribution with mean 0 and variance 1
- torch.save(obj, f, pickle_module, pickle_protocol, _use_new_zipfile_serializatin=True)
    - Saves an object to a disk file
    - obj - saved object
    - f - a file-like object or a string or os.PathLike object containing a file name
- torch.load(f, map_location=None, pickle_module, **pickle_load_args)
    - Loads an object saved with torch.save() from a file
    - first deserialized on the CPU and are then moved to the device they were saved from. If this fails, an exception is raised.
    - f - file-like object
    - map_location - a function, torch.device, string or a dict specifying how to remap storage locations
- torch.get_num_threads() -> int
    - Returns the number of threads used for parallelizing CPU operations
- torch.set_num_threads(int)
    - Sets the number of threads used for intraop parallelism on CPU
- torch.no_grad
    - Context-manager that disabled gradient calculation
    - useful for inference
- torch.enable_grad
    - Context-manager that enables gradient calculation
- torch.abs(input, out=None) -> Tensor
    - Computes the element-wise absolute value of the given input tensor
- torch.add(input, other, out=None)
    - Adds the scalar other to each element of the input input and returns a new resulting tensor
- torch.ceil(input, out=None) -> Tensor
    - Returns a new tensor with the ceil of the elements of input
- torch.floor(input, out=None) -> Tensor
    - Returns a new tensor with the floor of the elements of input
- torch.clamp(input, min, max, out=None) -> Tensor
    - Clamp all elements in input into the range [min, max] and return a resulting tensor
- torch.div(input, other, out=None) -> Tensor
    - Divides each element of the input input with the scalar other and returns a new resulting tensor
- torch.exp(input, out=None) -> Tensor
    - Returns a new tensor with the exponential of the elements of the input tensor input
- torch.log(input, out=None) -> Tensor
    - Returns a new tensor with the natural logarithm of the elements of input
- torch.mul(input, other, out=None)
    - Multiplies each element of the input input with the scalar other and returns a new resulting tensor
    - Each element of the tensor input is multiplied by the corresponding element of the Tensor other
- torch.neg(input, out=None) -> Tensor
    - Returns a new tensor with the negative of the elements of input
- torch.pow(input, exponent, out=None) -> Tensor
    - Thakes the power of each element in input with exponent and returns a tensor with the result
- torch.sigmoid(input, out=None) -> Tensor
    - Returns a new tensor with the sigmoid of the elements of input
- torch.sqrt(input, out=None) -> Tensor
    - Returns a new tensor with the square-root of the elements of input
- torch.argmax(input, dim, keepdim) -> LongTensor
    - Returns the indices of the maximum values of a tensor across a dimension
- torch.argmin(input, dim, keepdim=False, out=None) -> LongTensor
    - Returns the indices of the minimum values of a tensor across a dimension
- torch.logsumexp(input, dim, keepdim=False, out=None)
    - Returns the log of summed exponentials of each row of the input tensor in the given dimension dim
    - keepdim - whether the output tensor has dim retained or not
- torch.mean(input, dim, keepdim=False, out=None) -> Tensor
    - Returns the mean value of each row of the input tensor in the given dimension dim
- torch.sum(input, dim, keepdim=False, dtype=None) -> Tensor
    - Returns the sum of each row of the input tensor in the given dimension dim
- torch.argsort(input, dim=-1, descending=False) -> LongTensor
    - Returns the indices that sort a tensor along a given dimension in ascending order by value
- torch.max(input, dim, deepdim=False, out=None) -> (Tensor, LongTensor)
    - Returns a namedtuple (values, indices) where values is the maximum value of each row of the input tensor in the given dimension dim. And indices is the index location of each maximum value found (argmax)
- torch.min(input, dim, keepdim=False, out=None) -> (Tensor, LongTensor)
    - Returns a namedtuple (values, indices) where values is the minimum value of each row of the input tensor in the given dimension dim. And indices is the index location of each minimum value found (argmin).
- torch.sort(input, dim=-1, descending=False, out=None) -> (Tensor, LongTensor)
    - Sorts the elements of the input tensor along a given dimension in ascending order by value
    - A namedtuple of (values, indices) is returned, where the values are the sorted values and indices are the indices of the elements in the original input tensor
- torch.topk(input, k, dim=None, largest=True, sorted=True, out=None) -> (Tensor, LongTensor)
    - Returns the k largest elements of the given input tensor along a given dimension
    - A namedtuple of (values, indices) is returned, where the indices are the indices of the elements in the original input tensor
- torch.cartesian_prod(*tensors)
    - Do cartesian product of the given sequence of tensors
- torch.diag(input, diagonal=0, out=None) -> Tensor
- torch.einsum(equation, *operands) -> Tensor
    - This function provides a way of computing multilinear expressions using the Einstein summation convention
- torch.flatten(input, start_dim=0, end_dim=-1) -> Tensor
    - Flattens a contiguous range of dims in a tensor
- torch.flip(input, dims) -> Tensor
    - Reverse the order of a n-D tensor along given axis in dims
- torch.trace(input) -> Tensor
    - Returns the sum of the elements of the diagonal of the input 2-D matrix
- torch.bmm(input, mat2, deterministic=False, out=None) -> Tensor
    - Performs a batch matrix-matrix product of matrices stored in input and mat2
- torch.dot(input, tensor) -> Tensor
    - Computes the dot product (inner product) of two tensors
- torch.matmul(input, other, out=None) -> Tensor
    - Matrix product of two tensors
