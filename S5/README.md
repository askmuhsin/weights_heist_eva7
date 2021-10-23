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
- accuracy at 15 epoch is only 99.31%, but train accuracy is already at 99.22%. so probably will need to try adding some regularizations in a future iteration
