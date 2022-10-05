# note_week1_intro to GANs

### 1、GAN intro
GAN属于无监督学习，由两个模型组成，generator模型和discriminator模型互相对抗。  
eg: generator生成逼真的图片，discriminator去区分真的假的。  

generative models：已知Class Y，加上Noise，获得Features X，求的是P(X|Y)  
discriminator models：区分猫和狗，通过Features X，判断Class Y，求的是P(Y|X)  

**Generator** learns to make **fakes** that look **real**. (fool the discriminator)  
**Discriminator** learns to dinstinguish **real** from **fake**.  

在竞争中互相学习->最终假的会看起来是真的。  

### 2、generative models
**Variational Autoencoders（VAE）**  
~~realistic image -> encoder -> ~~latent space [vector find a place]-> decoder -> reconstruct the image  

**Generative Adversarial Networks（GAN）**  
vector/random noise -> generator -> image (像decoder）  
image -> discriminator -> fake or real   
adversarial：对抗性的  

### 3、Companies using GANs  
1、Adobe：Next-gen Photoshop  
2、Google：Text Generation  
3、IBM：Data Augmentation  
4、Snap/Tictok：Image Filters  
5、Disney：Super-resolution  

### 4、Discriminator
Classifiers：区分不同的class，分类器。  
1.jpg  
Y:Class, X:Features    
P(Y|X) 求的是条件概率     
Discriminator：P(class|feature) class=True/False,feature->images    
是分类器的一种，学习通过特征X输出类别Y的概率，对generator形成反馈。  

### 5、Generator
噪声向量--输入到神经网络--输出图片，每次生成的图片可能都是不一样的。  
2.jpg  
Generator：P(X|Y) = P(features|class) 求的是条件概率  
通过P(X)模拟可能的真实的猫的分布P，更有可能生成数据集里那些常见的猫（因为他们的特征更普遍）。
Generator会从数据集里学习特征X的分布，为了每次生成不同的图像会在输入添加随机特征。

### 6、BCE Cost Function