# matrix-vector multiplication
## problem formulation:
$$ Y_{m*1}=A_{m*n} x_{n*1}$$
$$y_i=\sum_{j=1}^{m} A_{ij}x_j$$
without GPU:
```C
for(int i = 0;i<m;i++)
{
	y[i] = 0;
	for(int j=0;j<n;j++)
	{
		y[i] += y[i] + A[i][j]*x[j];
	}
}
```

with CUDA:
```C
int idx = threadIdx.x + blockIdx.x * blockDim.x;
for (size_t i = 0; i < n; i++)
{
	y[idx] += A[idx][i] + x[i];
}
```
use shared memory:
```C
int ithr = threadIdx.x;
int i = threadIdx.x+blockDim.x*blockIdx;
int nthr = blockDim.x;
float s=0;
__shared__float xb[1024];
for(int j0=0;j0<n;j0+=nthr)
{
	xb[ithr]=x[j0+ithr];
	__syncthreads();
	for(int j1=0;j1<nthr;j1++)
	{
		s+=A[i*n+(j0+j1)]*xb[j1];
	}
	__syncthreads()
}
y[i]=s;
```
