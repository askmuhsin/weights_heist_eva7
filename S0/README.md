**What are Channels and Kernels (according to EVA)?**

**Channels** are containers of information or features. Any sensible (sensible can be relative from problem to problem) concepts grouped together can be considered as 1 channel. A data point can be a formation of several channels. For example, an image can be considered as a data point that is formed using 3 channels, which are the Red, Green, and Blue Image channels. The same image can be conceptually broken down into a different set of channels for example one that contains all the vertical lines, and another channel that contains all the horizontal lines, and more channels constituting other angled lines.

**Kernels** are feature extractors. They are mechanisms by which we can split the channels of a data point. For example, a vertical edge filter is a kernel in computer vision (a 3X3 matrix generally), which can be used to extract out all the vertical lines in a channel. A sieve that allows only particles beyond a certain size to let through it, can be considered as a kernel in the physical world that is extracting out a channel of certain sized particles. In machine learning, a kernel is often learned from labeled data.

A 3X3 vertical edge detection kernel --

    -1 0 1
    
    -2 0 2
    
    -1 0 1

----------

**Why should we (nearly) always use 3x3 kernels?**

**Can replace kernels of any other size --** 3x3 kernels can be used to create kernels of any other size. For example, in order to create a 2x2 kernel, we can just pad out the first row and column of a 3x3. A 5X5 kernel can be formed by combining two 3x3 kernels.

**Optimized for performance --** 3x3 kernels are widely optimized on all popular hardware and software making it an easy choice.

**Higher receptive field --** The receptive field of using a 3x3 kernel is higher than using a 5x5 kernel.

**Fewer parameters/memory --** The number of parameters in using 2 3x3 kernels will be 18 (9 + 9), whereas using one 5X5 kernel will be 25.

**Deeper networks --** using 3X3 kernels means the image size is not reduced as much on each step, meaning more deeper networks are possible.

----------

**How many times do we need to perform 3x3 convolutions operations to reach close to 1x1 from 199x199?**

We will have to perform the 3X3 Convolution operation 99 times for 199X199 to reach 1X1

[199 X 199] >

[197 X 197] > [195 X 195] > [193 X 193] > [191 X 191] > [189 X 189] >

[187 X 187] > [185 X 185] > [183 X 183] > [181 X 181] > [179 X 179] >

[177 X 177] > [175 X 175] > [173 X 173] > [171 X 171] > [169 X 169] >

[167 X 167] > [165 X 165] > [163 X 163] > [161 X 161] > [159 X 159] >

[157 X 157] > [155 X 155] > [153 X 153] > [151 X 151] > [149 X 149] >

[147 X 147] > [145 X 145] > [143 X 143] > [141 X 141] > [139 X 139] >

[137 X 137] > [135 X 135] > [133 X 133] > [131 X 131] > [129 X 129] >

[127 X 127] > [125 X 125] > [123 X 123] > [121 X 121] > [119 X 119] >

[117 X 117] > [115 X 115] > [113 X 113] > [111 X 111] > [109 X 109] >

[107 X 107] > [105 X 105] > [103 X 103] > [101 X 101] > [99 X 99] >

[97 X 97] > [95 X 95] > [93 X 93] > [91 X 91] > [89 X 89] >

[87 X 87] > [85 X 85] > [83 X 83] > [81 X 81] > [79 X 79] >

[77 X 77] > [75 X 75] > [73 X 73] > [71 X 71] > [69 X 69] >

[67 X 67] > [65 X 65] > [63 X 63] > [61 X 61] > [59 X 59] >

[57 X 57] > [55 X 55] > [53 X 53] > [51 X 51] > [49 X 49] >

[47 X 47] > [45 X 45] > [43 X 43] > [41 X 41] > [39 X 39] >

[37 X 37] > [35 X 35] > [33 X 33] > [31 X 31] > [29 X 29] >

[27 X 27] > [25 X 25] > [23 X 23] > [21 X 21] > [19 X 19] >

[17 X 17] > [15 X 15] > [13 X 13] > [11 X 11] > [9 X 9] >

[7 X 7] > [5 X 5] > [3 X 3] > [1 X 1]

----------

**How are kernels initialised?**

Kernels are initialised as random small numbers typically with a mean 0 and a standard deviation of 1. Depending on the other settings of the learning algorithm the mean and standard deviation can change. Since we are expecting to have several kernels in our learning algorithms and we ideally want all of them to learn to extract different features, it won’t be a good idea to initialise all of them with the same number. Also since we are using back-propagation, having very large or small initialised can lead to gradient explosion or vanishing.

A point worth noting is that how kernel initialisation is done is no more really a highly discussed topic, this is thanks to more robust regularisation approaches being used in modern deep neural networks like batch normalisation, or image augmentations.

----------

**What happens during the training of a DNN?**

In the beginning, a DNN consists of several layers, each of which consists of several kernels (CNN) / neurons initialized randomly (this is also called the parameters of the network or the weights of the network). The DNN if used for classification would have a final layer that is the same size as the number of classes. With a random initialization, the output from the final layer for a given input would also be random and thus not valid. During the training process, the amount by which the output is incorrect is measured (error) using a loss function. Further using an algorithm called backpropagation each of those individual neurons are updated to produce more correct output. The end of this process would be when all the neurons in the network are set such that the output available on the final layer for most of the input data has reached some acceptance criterion (accuracy, recall, precision; on some test set).
