# "offlad" model of programming
- CPU starts program
- CPU copies data to GPU memory(over IO(eg.PCle))
- CPU dispatches kernels for execution on GPU
- CPU copies data from GPU
# GPU memory model
## global memory, shared memory, local memory
## block, threads, grids
why do we need blocks：
### how to find thread index

## streamming process

# metrics
- threads per block(up to 1024)
- blocks(up to $(2^31) - 1$)
- register memory
- shared memory
