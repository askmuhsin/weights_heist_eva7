
# Task
Train a neural network to take in a random image from MNIST dataset, and a random number (one-hot encoded) and output the sum of it. 

------
# Training Logs
![image](https://user-images.githubusercontent.com/8600096/137781190-edb14bee-cf2a-415a-9e11-8f2a972fc7f2.png)
![image](https://user-images.githubusercontent.com/8600096/137781216-a917b0c0-c2eb-44a8-9f6a-baef04d4ccd1.png)

------
# Dataset 
The task requires a custom dataloader to load 1 image from the MNIST dataset, and a one-hot encoding of a random number.     
```python
class MnistPlusNum(Dataset):
    
    def __init__(self, train=True):
        self.train = train
        self.mnist = datasets.MNIST(
            root='./datasets/mnist_data/',
            train=self.train,
            download=True,
            transform=transforms.Compose([
              transforms.ToTensor(),
              transforms.Normalize((0.1307,), (0.3081,)),
            ])
        )
        print(self)
        
    def __len__(self):
        return len(self.mnist)
    
    def __getitem__(self, idx):
        img_data = self.mnist[idx][0]
        img_label = self.mnist[idx][1]
        
        rand_num = torch.randint(low=0, high=10, size=(1,))
        num_data = torch.zeros(1, 10)
        num_data[0, rand_num] = 1
        
        num_label = rand_num + img_label
        
        return img_data, img_label, num_data, num_label
    
    def __repr__(self):
        return 'Loaded MNIST "{}" dataset with random number added to it. Data size - {}'.format(
            'train' if self.train else 'test', self.__len__()
        )
```
The Data is generated as follows --
- get an MNIST image and its label       
- then followed by it generate a random number
- one-hot encode the random number
- add the random number with MNIST LABEL
- there are two LABEL outputs -- 1. MNIST LABEL, 2. SUMMER LABEL
- there are two DATA (model input) outputs -- 1. MNIST image, 2. Random Number

```shell
img_data :  torch.Size([1, 1, 28, 28])
img_label :  tensor([7])
num_data : 
	value - tensor([[4]])
	shape - torch.Size([1, 1, 10])
	tensor - tensor([[[0., 0., 0., 0., 1., 0., 0., 0., 0., 0.]]])
out_label : 
	value - 11
	shape - torch.Size([1, 1])
	tensor - tensor([[11]])
```

------
## Model Architecture (discussion)
The model takes two inputs : image and random number    
the model takes the MNIST image and following conv and pool blocks is brought to an output size of 1X1X10    
the 1X1X10 is resized to tensor of 1X10.    
this tensor of CNN output is concatenated with the random number also of size 1X10 to form a tensor of 1X20    
the 1X20 tensor is then sent through a few Fully connected layers to finally get an output of 19 classes.    

------
## Evaluation
for training and testing loss we use calculate two losses,     
1. the pred of `img` vs `img target`, and       
2. the pred of `rand num + img target` vs  `sum target`.      
the overall loss on train set at 0.0678, and on test set was at 0.0009. (at EPOCH 9]    
        
for accuracy on test set, the calculation was done seperately on each task.       
for image classification task our accuracy was 99%, and for summer task it was 98%.       
        
Training was done on GPU, and took about 30sec per epoch, with a batch size of 128.        

------
## loss fn
the loss fn used was CrossEntropyLoss as it was a classifcation task with 20 classes.        
It is worth noting that the module torch.nn.functional was used for it.     
