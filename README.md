# Vision Transformers (ViT) for Dark Matter Morphology

![GSoC](https://github.com/SVJLucas/ViT-for-Dark-Matter-Morphology/assets/60625769/e31e9939-4a6e-4642-b65d-8e738fbed106)

The project titled "Vision Transformers (ViT) for Dark Matter Morphology" was conceived and developed as part of the **Google Summer of Code** initiative. This globally recognized annual program, sponsored by Google, provides a paid opportunity for student developers to engage with and contribute to open-source software projects. The project was carried out in collaboration with Machine Learning for Sciences (ML4SCI), an organization dedicated to integrating machine learning methodologies into scientific research.

Through Google Summer of Code, students are given the chance to work on significant projects during their summer break, all while gaining real-world, hands-on experience in software development and becoming familiar with the dynamics of open-source projects. Participating students are paired with a mentor from their project, fostering a learning environment guided by experienced developers.

In this particular project, I focused on the application of Vision Transformers, a type of machine learning methodology, to the field of dark matter morphology. By skillfully combining traditional physics-based characteristics with state-of-the-art machine learning techniques and metaheuristic optimization, a robust model was developed capable of detecting and analyzing dark matter substructures in images. This project highlights the vast potential that interdisciplinary collaboration holds for advancing both scientific and technological domains.


# Transformers (ViT) for Physics

The Transformer design has shown to be very successful for a wide range of NLP applications, leading to its widespread acceptance in the field. In recent years, there has been growing interest in using Transformers for a variety of other applications beyond NLP, including computer vision. At the same time, the use of deep learning techniques in the field of science has become common, with the introduction of Physics-informed neural networks (PINNs). In this context, I use both techniques together, in this project, to find Dark Matter substructures in observations, extracting features of physical meaning from the observations (images) and, then, concatenating them to be process by a Vision Transformer (ViT) neural network.


# Image Processing  

First, we need to process incoming images. By finding the region of interest (and then the possible observation of dark matter interaction), we can crop out the most important part of the image. When performing a rotation, we also decrease the space of symmetries (since we minimize the rotational symmetry), which turns rotated images into similar images and facilitates model learning.

![Finding the Region Of Interest](https://user-images.githubusercontent.com/60625769/229907149-af594bc3-d14a-4116-89a3-423d666bc972.png)

# Feature Engineering

Next, we will take some features induced by physical knowledge of the problem. The area occupied in the observation of the Dark Matter substructure is a characteristic of this substructure, as well as the number of points of greater luminosity. These features have value for model prediction and will be added to the neural network.


![Crop and Rotate the ROI (1)](https://user-images.githubusercontent.com/60625769/229908064-8632743a-d8bd-4b33-95a4-9073626fad97.png)

# Model Architecture

The final architecture is inspired by the [Vision Transformers for Small-Size Datasets](https://arxiv.org/abs/2112.13492), using innovations proposed by this paper, such as the Shifted Patch Tokenization (SPT) layer and Locally Multihead Attention (LMHA), which facilitate the learning of the ViT. The final model was, then, totally implemented in Pytorch.

![Cropped, Rotated and Resized the Region of Interest (ROI) (2)](https://user-images.githubusercontent.com/60625769/229917865-feada814-8653-4423-88db-c9c596158e05.png)


# Bayesian Optimization

Since visual transformers are sensitive to some of their hyperparameters, Baysian optimization was performed on some of them. For the proposed transformer in question, the learning rate proved to be of very important optimization, since the transformer could not train


![download (20)](https://user-images.githubusercontent.com/60625769/229910378-60739e6c-c4c8-45cd-9978-387d10ecda90.png)

Below, find the plot of the negative ROC-AUC of the model versus the number of iterations. We can see that the optimization was effective, when we left a model with ROC-AUC=0.85 (not in the graph) to the final model with ROC-AUC=0.91.

![download (19)](https://user-images.githubusercontent.com/60625769/229911713-dc00154b-f45d-4b27-9bd2-94d28c96e191.png)

# Model Performance

After the final training, the Transformer performed with a ROC-AUC of 0.956, a high value, showing the good performance of the technique used, approaching the ideal ROC curve, as can be seen in the graph.

![download (21)](https://user-images.githubusercontent.com/60625769/229914249-8c5e47b8-4891-4d82-9ab3-0ef5a5587219.png)

These results are impressive and show the power of combining classical features (inspired by physical meaning), Machine Learning and Metaheuristic Optimization.



