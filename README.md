# Image Deblurring
**Group Members:** Jinghao Ye, Lanfeng Liu, Zizhuang Guo, Yuhang Sun

## Overview
We tried three non-deep-learning methods and two deep learning methods successfully. The three non-dl methods are the Wiener Filter for Motion Deblurring, the Two-Phase Kernel Estimation for Motion Deblurring and the Wiener Filter for Out of Focus Deblurring. The two deep learning methods are the DeblurGAN-v2 model and the SRN Deblur model.
![img01](https://github.com/sunyuhang01/CS585-final-non-DL-deblur/blob/master/output/results/01.jpg?raw=true)
![img02](https://github.com/sunyuhang01/CS585-final-non-DL-deblur/blob/master/output/results/02.jpg?raw=true)
![img03](https://github.com/sunyuhang01/CS585-final-non-DL-deblur/blob/master/output/results/03.jpg?raw=true)
![img04](https://github.com/sunyuhang01/CS585-final-non-DL-deblur/blob/master/output/results/04.jpg?raw=true)

## Non-DL Methods


**Introduction:**

Our project has three non-deep-learning filters: wiener filter for motion deblurring and out of focus deblurring and two-phase kernel estimation for motion deblurring.

Non-DL functions estimate a point spread function (PSF) to deconvolute the blurred image. Motion deblur filter uses PSF of a linear motion blur distortion and out-of-focus deblur filter uses circular PSF.

The two-phase kernel estimation function provides a specific strategy to calculate PSF, so it is more efficient than the wiener filter.

 

**Advantages of using motion deblur filter:**

- It is more efficient to use motion deblur filter on those blurred images caused by fast moving.

- Non-dl functions do not need to train for a long time, so they are easier to use.

**Advantages of using out-of-focus deblur filter:**

- Out-of-focus deblur filter can be more efficient on blurring problems due to incorrect focus

- Non-dl functions do not need to train for a long time, so they are easier to use.

 

 

## DL methods

### DeblurGAN-v2 experiment

**Pre-trained model**: InceptionResNet-v2

**Dataset used for train**: GoPro Test Dataset

**Introduction:**

DeblurGAN-v2, which is an improved version of DeblurGAN. Compared to DeblurGAN, The main change of DeblurGAN-v2 is that the authors introduce the Feature Pyramid Network (FPN) for the generator, and they adopt a relativistic discriminator for the discriminator. 

The architecture is based on the FPN backbone. The authors take five final feature maps of different scales as the output. Those features are later up-sampled to the same 1/4 input size and concatenated into one tensor which contains the semantic information on different levels. They additionally add two upsampling and convolutional layers at the end of the network to restore the original image size and reduce artifacts

**Advantages of using DeblurGAN-v2:**

- **high performance**

The deblurred images have high resolution. It can keep the rich details in the image and create the image very close to the real image

- **Flexibility** 

We can choose different backbones depending on the demand. For strong deblurring performance, we can choose InceptionResNet-v2. For lightweight and efficient image deblurring, we can choose MobileNet V2 and MobileNet-DSC.  







### SRN deblur(Scale Recurrent Networks)

**Pre-trained model**:  LSTM model (There are two other non-LSTM pre trained model, produced by tuning parameters)

**Dataset used for train**: [DeepDeblur_release](https://github.com/SeungjunNah/DeepDeblur_release)

**Introduction**:

Single image deblurring is highly ill-posed. Traditional methods applied various constraints to model characteristics of blur (e.g. uniform/non-uniform/depth-aware), and utilized different natural image priors to regularize the solution space.

Learning-based methods have also been proposed for deblurring. Among them, Nah et al. have achieved state-of-the-art results using a multiscale convolutional neural network (CNN). This framework follows the multi-scale mechanism in traditional methods, where the coarse-to-fine pipelines are common when handling large blur kernels .



**Advantages:**

- **Less time than previous multi-scale CNN method**

  Since the SRN use shared parameters for different scales, It significantly reduces the number of trainable parameters. 



- **Better performance **

  Combined with RNN structure, the hidden state captures useful information and benefits restoration across scales.











 

 

 