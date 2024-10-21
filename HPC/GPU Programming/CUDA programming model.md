# CUDA programming basis
host=CPU;device=GPU
## copy data
###  to GPU
``` C
cudaMemcp(args)
```
### from GPU
```C

```
## declare a CUDA [[kernel]]
### call from a host
```C
func<<<nblck, nthr>>>(args);

```

- nthr: number of threads per block, can be scalar or a `dim3` type
- nblck: 
#### dim3 type
```C
dim3 blcks(4,3,bz);
dime thr(16,8,tz);

/*
args:
	blockDim.x=16, blockDim.y=8
	gridDim.x = 4,gridDim.y = 3
*/
```
notice: total threads number: $blockDim.x*bloclDim.y*gridDim.x*gridDim.y$

## thread coordinates within kernel
