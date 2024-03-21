# Computer Vision: Totally-Looks-Like (TLL) image matching

# Abstract
This project addresses the challenge of Totally-Looks-Like image matching. To achieve this, we utilize feature extraction methods based on pre-trained CNN models, including VGG, ResNet, and DenseNet. The following model training is carried out using Siamese networks.

# Methods
- Data Preprocessing (Data augmentation)
  - To enlarge our dataset, we employed three distinct data augmentation techniques: horizontal (left-right) flipping, contrast enhancement, and brightness adjustment.
    ![image](https://github.com/W-Hsieh/Computer-Vision/assets/142127312/a2b69ed0-da96-4099-bccd-55fdd27db9d1)

- Feature Extraction
  - For this project, we have utilized three renowned deep learning architectures for feature extraction: VGG, ResNet, and DenseNet.
    - **VGG (Visual Geometry Group):** VGG leverages a sequence of convolutional layers followed by max-pooling. It excels at hierarchically extracting intricate patterns and textures from images. The depth of this architecture ensures the capture of both low-level and high-level features, providing a robust representation of the input image.
    - **ResNet (Residual Network):** ResNet introduced the innovative concept of ”skip connections” or ”shortcuts.” These connections allow ResNet to delve deeper in feature extraction, enhancing generalization across various computer vision tasks.
    - **DenseNet (Densely Connected Network):** Taking the idea of connections a step further, DenseNet continually merges and concatenates feature-maps. This approach promotes feature propagation, leading to a diversified feature extraction process.
    By leveraging these three distinct architectures, we ensure that our model comprehensively captures a broad range of patterns and details.
    
- Siamese Networks
- Evaluation metrics

# Conclusion
To summarize, our best results were achieved using only the feature extraction from VGG with a dimension of 25088. While we aimed for enhanced results by training the data using the Siamese Networks, the outcomes did not surpass those obtained from feature extraction alone. Despite testing 144 parameter combinations, the optimal outcome only surpassed the benchmark but fell short compared to our initial feature extraction results. However, it would be hasty to deduce that training doesn’t enhance prediction accuracy. Future experiments
could delve into a wider range of hyperparameters, alternative feature extraction architectures, and more intricate Siamese Network designs.
