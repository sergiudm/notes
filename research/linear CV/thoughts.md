### GRU


![[Pasted image 20241123181218.png]]
![[Pasted image 20241123181644.png]]

### MiniGRU
Step 1: Drop previous hidden state dependencies from gates
![[Pasted image 20241123184926.png]]
- Why?
	- ![[Pasted image 20241123185105.png]]
Step 2: Drop range restriction of candidate states
![[Pasted image 20241123185217.png]]
- Why?
	- ![[Pasted image 20241123185455.png]]
																	- ![[Pasted image 20241123185952.png]]
	- ![[Pasted image 20241123185506.png]]



## How to achieve linear attention
- Parallelizable RNNs
	- S 6
	- 
- Modified $sim (Q,K)$
	- ![[Pasted image 20241123191644.png]]
	- [线性Attention的探索：Attention必须有个Softmax吗？ - 科学空间|Scientific Spaces](https://spaces.ac.cn/archives/7546)
- 

## Higher order reccurence?