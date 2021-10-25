# Iteration 0 [_CODE SETUP_] --> [notebook link](https://github.com/askmuhsin/weights_heist_eva7/blob/main/S5/nbs/iteration_0.ipynb)
## Target
- Iteration #0
- get the code setup right.
- starting from the 8th iteration of class.
  - not using any img aug, and lr steps now.
- the intention of this step is to have the correct code setup.
- expecting to see a test accuracy of 99.41 at 9th epoch, as that is what was achieved for the same run on class.

## Result
  - Parameters - 13,808
  - max_test_accuracy 		- 99.39	[EPOCH -- 14]
  - max_train_accuracy 		- 99.23	[EPOCH -- 13]
  - test_accuracy @ epoch 15 	- 99.31
  - train_accuracy @ epoch 15 	- 99.22

## Analysis
- the parameters are higher than the target. in next iteration will start with a smaller model. 
- accuracy at 15 epoch is only 99.31%, but train accuracy is already at 99.22%. so probably will need to try adding some regularizations in a future iteration.

## Charts
### train test loss accuracy
![image](https://user-images.githubusercontent.com/8600096/138561941-98fe613d-666c-41e9-b88c-8f8f8c58003f.png)

----

# Iteration 1 [_REDUCE PARAMETERS_] --> [notebook link](https://github.com/askmuhsin/weights_heist_eva7/blob/main/S5/nbs/iteration_1.ipynb)
## Target
- Iteration #1
- reduce the number of parameters to about 8k
- the strategy for reducing the parameters is by propotionally removing channels from each layer. ie.
- expecting accuracy to drop, but maybe not too much; to around 93% on test set.

## Result
  - Parameters - 7,936
  - max_test_accuracy 		- 99.27	[EPOCH -- 11]
  - max_train_accuracy 		- 99.04	[EPOCH -- 15]
  - test_accuracy @ epoch 15 	- 99.26
  - train_accuracy @ epoch 15 	- 99.04

## Analysis
- the test accuracy dropeed by 0.12% with a decrease in number of parameters.
- Noticably this model seemed to have less stable accuracy compared to the previous larger model with 14k parameters.
- next step planning to add image augmentations, to improve the test accuracy.

## Charts
### train test loss accuracy
![image](https://user-images.githubusercontent.com/8600096/138561988-aa8c2e01-6463-4e25-aadf-69b92794fadd.png)
### comparison of iteration 0 and 1
![image](https://user-images.githubusercontent.com/8600096/138562029-897a0ea2-02f0-48f1-aab3-a33d016a2777.png)


----
# Iteration 1 [IMAGE AUGMENTATION] --> [notebook link](https://github.com/askmuhsin/weights_heist_eva7/blob/main/S5/nbs/iteration_2.ipynb)

## Target
- Iteration #2
- add image augmentations.
  ```python
    transforms.ColorJitter(brightness=0.2, contrast=0.2, saturation=0.2, hue=0.1),
    transforms.RandomRotation((-8., 8.)),
    transforms.GaussianBlur(kernel_size=(3, 9), sigma=(0.1, 5.)),
    transforms.RandomPerspective(distortion_scale=0.5, p=0.2),
    transforms.RandomAffine(degrees=8., translate=(0.1, 0.3), scale=(0.5, 0.75)),
    ```

## Result
  - Parameters - 7,936
  - max_test_accuracy 		- 86.94	[EPOCH -- 15]
  - max_train_accuracy 		- 91.63	[EPOCH -- 15]
  - test_accuracy @ epoch 15 	- 86.94
  - train_accuracy @ epoch 15 	- 91.63

## Analysis
- saw a dip in performance. but both the the train and test accuracies has decreased.
- thinking the augmentation strategy was too strong. will reduce in on the next iteration to just rotation, gaussianblur, randomaffince, and colorjitter.
- while also reducing the parameters of rotation degree, translate, and scale values.



