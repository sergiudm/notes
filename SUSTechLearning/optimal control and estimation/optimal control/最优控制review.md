# Lec 1 

## inner product
### basic
![[Pasted image 20250414105523.png]]
![[Pasted image 20250414105534.png]]
![[Pasted image 20250414105606.png]]
![[Pasted image 20250414105625.png]]
### general inner product

function inner product
![[Pasted image 20250414110045.png]]
![[Pasted image 20250414105832.png]]
matrix 
![[Pasted image 20250414105940.png]]

延展到傅里叶级数
![[Pasted image 20250414110711.png]]
![[Pasted image 20250414110720.png]]
![[Pasted image 20250414111908.png]]
![[Pasted image 20250414112249.png]]
![[Pasted image 20250414112508.png]]
傅里叶变换
![[Pasted image 20250414112617.png]]
![[Pasted image 20250414112645.png]]
![[Pasted image 20250414112734.png]]

## geometric

![[Pasted image 20250414113009.png]]

![[Pasted image 20250414113014.png]]

# Lec 2
## state space model
1. all differencial equation can be written as state-space form
2. state space model has only 1st order derivative difference(无论状态空间方程的复杂，总是能引入一些状态量使其化简为一阶微分方程)
### static 
![[Pasted image 20250414120326.png]]

### Dynamic
![[Pasted image 20250414120416.png]]
![[Pasted image 20250414120533.png]]

### general continuous-time state space model
![[Pasted image 20250414232245.png]]

### general discrete-time state space model
![[Pasted image 20250414232347.png]]

### example of ssm


### RNN is special class of ssm![[Pasted image 20250414233901.png]]
RNN: map sequential input to sequential output

in RNN, there are assumption: 
![[Pasted image 20250414234128.png]]

if you realize the RNN: 
![[Pasted image 20250414234248.png]]
![[Pasted image 20250414234319.png]]


## C2D D2C

### C2D
![[Pasted image 20250414234512.png]]![[Pasted image 20250414234609.png]]
![[Pasted image 20250414234648.png]]


## nonlinear to linear

![[Pasted image 20250414235036.png]]
![[Pasted image 20250414235100.png]]


![[Pasted image 20250414235553.png]]

## System solution and stability

for LTI :
![[Pasted image 20250414235752.png]]


Most control problem can be transfer to regulation problem (if $y_{ref}(t)$is time variant, it is called tracking problem) 

### internal Stability 
it is for autonomous system or special close loop system.(形如$x_{k+1} = f(x_k)$) 
![[Pasted image 20250415000543.png]]
for linear system:
![[Pasted image 20250415000738.png]]
![[Pasted image 20250415000754.png]]


# Lec 3
## Eigenvalues    System Response (consider system: $x(k) = A^kx(0)$) 

Case 1 : 
 ![[Pasted image 20250415002027.png]]
 
 
 case 2
![[Pasted image 20250415002041.png]]


The shape of **transient response** is determined by the locations  of the eigenvalues
![](https://api2.mubu.com/v3/document_image/34d09a69-f751-41b1-8303-f96a4ff80131-28037886.jpg)



### 二阶系统

![[Pasted image 20250415003141.png]]
![[Pasted image 20250415003149.png]]

c2d
![[Pasted image 20250415003213.png]]



# Lec 4 
## what is the optimal problem?



## modeling a problem into optimal problem
> for a system, CL eigenvalues can not indicate all infomation of **transient response** , and we want to small input 

### Metric-based controller design 
> design object = cost function; 
> cost func is  always penalized. Result in 1) state deviation from 0. 2)Large control effort
> conflicting goals: larger control can often drive state to  zero faster 

### some basic point of optimal control 
![[Pasted image 20250415202724.png]]
![[Pasted image 20250415202736.png]]

### example of modeling a question 
![[Pasted image 20250415202937.png]]


## intro of DP
the approuch to address the optimal problem 

### basic knowledge(倒的)
![[Pasted image 20250415204605.png]]![[Pasted image 20250415204617.png]]
![[Pasted image 20250415205645.png]]
![[Pasted image 20250415205113.png]]

### How to solve the DP problem ---Value iteration

![[Pasted image 20250415205205.png]]
![[Pasted image 20250415205357.png]]

