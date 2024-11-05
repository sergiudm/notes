# 1. Why we need deep NNs
# 2. Failure of effectively training
## the different layers in our deep network are learning at vastly different speeds:
- Case 1: when later layers in the network are learning well, early layers often get stuck during training,  learning almost nothing at all.
- Case 2: the early layers may be learning well, but later layers can become stuck

## 2.1 the vanishing gradient problem
## 2.2 the exploding gradient problem
## 2.3 The unstable gradient problem
The fundamental problem here isn't so much the vanishing gradient problem or the exploding gradient problem. It's that the gradient in early layers is the product of terms from all the later layers. When there are many layers, that's an intrinsically unstable situation.

# 3.*The prevalence of the vanishing gradient problem*
  
make sure that $|w\sigma'(z) \leq1|$



