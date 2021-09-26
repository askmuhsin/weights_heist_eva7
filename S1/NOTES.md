# Softmax function / layer
A function that takes a vector of len K and squashes all the numbers in the vector from 0 to 1. The sum of the new vector will be 1. 
<br>In other words it outputs the vector as probabilities (confidence ?)
![image](https://user-images.githubusercontent.com/8600096/134802137-35cbe14f-36d2-4e56-9824-b1cd5fd31d7e.png)



# Negative Log-Likelihood (NLL)
Softmax and NLL is used together. 
<br>if the prediction is correct and has high confidence the we get low loss value.
<br>if the prediction is wrong and has low confidence (on the correct class) then we get high loss value.
![image](https://user-images.githubusercontent.com/8600096/134802282-7494d59b-2967-4647-950a-6197d90dea47.png)
<br>
<br>nll_loss in pytorch --> takes a list of class probabilities, and the target class to calculate the loss.
<br>when working with nll important to keep in mind the the expected class probabilities are 
<br>
```python
# input is of size N x C = 3 x 5
input = torch.randn(3, 5, requires_grad=True)
# each element in target has to have 0 <= value < C
target = torch.tensor([1, 0, 4])
output = F.nll_loss(F.log_softmax(input), target)
output.backward()
```

https://pytorch.org/docs/stable/generated/torch.nn.functional.nll_loss.html?highlight=f%20nll_loss#torch.nn.functional.nll_loss


![image](https://user-images.githubusercontent.com/8600096/134802814-d6836c9f-4a37-465d-a2c1-24fe61d47470.png)
https://ljvmiranda921.github.io/notebook/2017/08/13/softmax-and-the-negative-log-likelihood/
