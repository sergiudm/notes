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
	- ![[Pasted image 20241123185506.png]]



## How to achieve linear attention
- Parallel recurrence
- Modified $sim (Q,K)$
- 