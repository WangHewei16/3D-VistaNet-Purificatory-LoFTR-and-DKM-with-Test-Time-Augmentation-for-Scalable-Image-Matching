## LoFTR-DKM-Network-with-TAA-for-Image-Matching

#### 1. Background of the problem to be solved
For the majority of us, our best camera is built into our phone. We may take a photograph of a landmark, such as Rome's Trevi Fountain, and share it with friends. That photo is only two-dimensional and includes the perspective of our shooting location. Of course, many people have photographed the fountain. We might be able to create a more complete, three-dimensional view if we work together. What if machine learning could aid in better capturing the richness of the world by utilizing the vast amounts of unstructured image collections that are freely available on the internet?


Structure-from-Motion (SfM) is a method for reconstructing 3D objects and buildings from images. Typically, these images are captured under controlled conditions by skilled operators, ensuring homogeneous, high-quality data. Building 3D models from disparate images is much more difficult, given the wide range of viewpoints, lighting and weather conditions, occlusions from people and vehicles, and even user-applied filters.


The first step is to determine which parts of two images capture the same physical points of a scene, such as window corners. This is typically accomplished through the use of local features (key locations in an image that can be reliably identified across different views). Local features include short description vectors that capture the appearance in the vicinity of the point of interest. By comparing these descriptors, it is possible to establish likely correspondences between the pixel coordinates of image locations in two or more images. This "image registration" allows for the recovery of the point's 3D location via triangulation.


Our task is to develop a machine learning algorithm for registering two images from different perspectives. To train and test our model, we have access to a dataset of thousands of images. Figure below shows the sample of image matching and the trainset sample.

<div align=center><img src="https://github.com/WangHewei16/LoFTR-DKM-Network-for-Image-Matching/blob/main/images/problem%20and%20trainset%20sample.png" width="700"/></div>



#### 2. Testset Sample
<div align=center><img src="https://github.com/WangHewei16/LoFTR-DKM-Network-for-Image-Matching/blob/main/images/testset%20sample.png" width="590"/></div>


#### 3. Kornia tool
We choose to use Kornia [[Link](https://kornia.readthedocs.io/en/latest/)] to develop our mode, this is a tool powered by PyTorch and good at dealing with image matching problem.

<div align=center><img src="https://github.com/WangHewei16/LoFTR-DKM-Network-for-Image-Matching/blob/main/images/Kornia%20icon.png" width="300"/></div>

#### 4. Process of solving this problem
As for estimator, we use OpenCV estimator that is available in [[Link1](https://www.jianshu.com/p/56344498af8c)] and [[Link2](https://zhuanlan.zhihu.com/p/45532306)].
<div align=center><img src="https://github.com/WangHewei16/LoFTR-DKM-Network-for-Image-Matching/blob/main/images/process.png" width="590"/></div>

#### 5. BackBone 
##### 5.1 LoFTR Achitecture
The figure below shows the achitecture of LoFTR [[Paper Link](https://arxiv.org/pdf/2104.00680.pdf)]
<div align=center><img src="https://github.com/WangHewei16/LoFTR-DKM-Network-for-Image-Matching/blob/main/images/LoFTR%20architecture.png" width="590"/></div>

##### 5.2 DKM Achitecture
The figure below shows the achitecture of Deep Kernelized Dense Geometric Matching (DKM) [[Paper Link](https://arxiv.org/pdf/2202.00667.pdf)]
<div align=center><img src="https://github.com/WangHewei16/LoFTR-DKM-Network-for-Image-Matching/blob/main/images/DKM%20architecture.png" width="590"/></div>


#### 6. Test Time Augmentation (TTA)
Adopt size transformation and flip and Test Time Augmentation (TTA) on the inference stage of LoFTR.

<div align=center><img src="https://github.com/WangHewei16/LoFTR-DKM-Network-for-Image-Matching/blob/main/images/Test%20Time%20Augmentation.png" width="590"/></div>


#### 7. Image preprocess skill
<div align=center><img src="https://github.com/WangHewei16/LoFTR-DKM-Network-for-Image-Matching/blob/main/images/figure%20preprocess.png" width="590"/></div>



