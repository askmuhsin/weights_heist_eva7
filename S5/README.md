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

