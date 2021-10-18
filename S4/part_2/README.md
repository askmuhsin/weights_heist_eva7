# Discussion points
- 99.44% test accuracy achieved at EPOCH 17 with a total parameter of 16,452.
- Have used BN, Dropout, a Fully connected layer, have used GAP.
- Dropout value is set to 0.1.
- Training batch size is 128.
- Training is done on GPU.

-----
# Model Summary
![model summary](https://github.com/askmuhsin/weights_heist_eva7/blob/main/S4/part_2/model_summary.png)

-----
# Training Log
```
01 / 19 || train_loss=0.0831431 test_loss: 0.0384, test_accuracy: 9881/10000 (98.81%)
02 / 19 || train_loss=0.0204352 test_loss: 0.0297, test_accuracy: 9908/10000 (99.08%)
03 / 19 || train_loss=0.0841991 test_loss: 0.0291, test_accuracy: 9909/10000 (99.09%)
04 / 19 || train_loss=0.0297721 test_loss: 0.0231, test_accuracy: 9932/10000 (99.32%)
05 / 19 || train_loss=0.0659731 test_loss: 0.0248, test_accuracy: 9911/10000 (99.11%)
06 / 19 || train_loss=0.0449319 test_loss: 0.0244, test_accuracy: 9923/10000 (99.23%)
07 / 19 || train_loss=0.0059894 test_loss: 0.0246, test_accuracy: 9918/10000 (99.18%)
08 / 19 || train_loss=0.0472389 test_loss: 0.0222, test_accuracy: 9928/10000 (99.28%)
09 / 19 || train_loss=0.0102763 test_loss: 0.0229, test_accuracy: 9923/10000 (99.23%)
10 / 19 || train_loss=0.0097757 test_loss: 0.0216, test_accuracy: 9932/10000 (99.32%)
11 / 19 || train_loss=0.0210064 test_loss: 0.0282, test_accuracy: 9922/10000 (99.22%)
12 / 19 || train_loss=0.0168874 test_loss: 0.0230, test_accuracy: 9924/10000 (99.24%)
13 / 19 || train_loss=0.0023660 test_loss: 0.0260, test_accuracy: 9913/10000 (99.13%)
14 / 19 || train_loss=0.0026819 test_loss: 0.0247, test_accuracy: 9920/10000 (99.20%)
15 / 19 || train_loss=0.0022785 test_loss: 0.0230, test_accuracy: 9936/10000 (99.36%)
16 / 19 || train_loss=0.0327119 test_loss: 0.0199, test_accuracy: 9939/10000 (99.39%)
17 / 19 || train_loss=0.0123389 test_loss: 0.0177, test_accuracy: 9944/10000 (99.44%)  <-- 99.40%+ acc on test set
18 / 19 || train_loss=0.0194245 test_loss: 0.0223, test_accuracy: 9938/10000 (99.38%)
19 / 19 || train_loss=0.0189116 test_loss: 0.0244, test_accuracy: 9927/10000 (99.27%)
```

-----
# Training Charts
![test accuracy](https://github.com/askmuhsin/weights_heist_eva7/blob/main/S4/part_2/test_acc.png)
![test loss](https://github.com/askmuhsin/weights_heist_eva7/blob/main/S4/part_2/test_loss.png)
