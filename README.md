# Python Trick

## Numpy

### Consecutive, Overlapping Subsets of Array
```
In [41]: A
Out[41]: array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12])

In [42]: %timeit as_strided(A, shape=(5, 5), strides=(2*A.strides[-1],A.strides[-1]))
The slowest run took 6.18 times longer than the fastest. This could mean that an intermediate result is being cached.
100000 loops, best of 3: 14 µs per loop

In [43]: as_strided(A, shape=(5, 5), strides=(2*A.strides[-1],A.strides[-1]))
Out[43]: 
array([[ 0,  1,  2,  3,  4],
       [ 2,  3,  4,  5,  6],
       [ 4,  5,  6,  7,  8],
       [ 6,  7,  8,  9, 10],
       [ 8,  9, 10, 11, 12]])

In [44]: np.array([A[i:i+5] for i in range(0, 13-5+1, 2)])
Out[44]: 
array([[ 0,  1,  2,  3,  4],
       [ 2,  3,  4,  5,  6],
       [ 4,  5,  6,  7,  8],
       [ 6,  7,  8,  9, 10],
       [ 8,  9, 10, 11, 12]])

In [45]: %timeit np.array([A[i:i+5] for i in range(0, 13-5+1, 2)])
The slowest run took 9.04 times longer than the fastest. This could mean that an intermediate result is being cached.
100000 loops, best of 3: 5.27 µs per loop
```
In theory, `as_strided` creates a view of original array, memory usage is less then for-loop, although is slower.

### Construct an array by executing a function over each coordinate
```
np.fromfuction
```

### Increase the dimension of the existing array
```
x1 = np.array([1, 2, 3, 4, 5])
x1_new = x1[:, np.newaxis]
```

## Pytorch
### Custom weight Initilzation
```
module.weight.data.copy_(ndarray
```
The definition of Conv2d weight axis:[Channels, Groups, Height, Width] 
