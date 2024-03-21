# Computer Vision: Totally-Looks-Like (TLL) image matching

# Abstract
This project addresses the challenge of Totally-Looks-Like image matching. To achieve this, we utilize feature extraction methods based on pre-trained CNN models, including VGG, ResNet, and DenseNet. The following model training is carried out using Siamese networks.

# Methods
- **A. Data Preprocessing (Data augmentation)**
  - To enlarge our dataset, we employed three distinct data augmentation techniques: horizontal (left-right) flipping, contrast enhancement, and brightness adjustment.
    ![data_aug](https://github.com/W-Hsieh/Computer-Vision/assets/142127312/c476723a-cf97-4dc1-8c80-ea2e09cb8042)

- **B. Feature Extraction**
  - For this project, we have utilized three deep learning architectures for feature extraction: VGG, ResNet, and DenseNet.
    - **VGG (Visual Geometry Group):** VGG leverages a sequence of convolutional layers followed by max-pooling. It excels at hierarchically extracting intricate patterns and textures from images. This architecture's depth ensures the capture of both low-level and high-level features, providing a robust representation of the input image.
    - **ResNet (Residual Network):** ResNet introduced the innovative concept of ”skip connections” or ”shortcuts.” These connections allow ResNet to delve deeper into feature extraction and enhance generalization across various computer vision tasks.
    - **DenseNet (Densely Connected Network):** DenseNet takes the idea of connections a step further by continually merging and concatenating feature maps. This approach promotes feature propagation, leading to a diversified feature extraction process.
    By leveraging these three distinct architectures, we ensure that our model comprehensively captures a broad range of patterns and details.
    
- **C. Siamese Networks**
  - Following the feature extraction process, we proceeded to train our model using the Siamese Networks. Siamese Networks comprise multiple sister networks that share weights. Each of these networks generates embedding vectors for their individual inputs. Simultaneously, they aim to reduce the distance between embeddings of inputs from the same class. This approach crafts an embedding space that mirrors the class delineation of the training inputs. For distance computation, we have chosen to apply both Manhattan Distance (L1) and Euclidean Distance (L2) separately. Additionally, to prevent overfitting, we employed dropout to modify the structure of the neural network, which is equivalent to training different networks.
    
- **D. Evaluation metrics**
  - **1) Baseline (cosine similarity):**
       When skipping feature extraction and training processes, we directly expanded all pixels into a column vector and then calculated the cosine similarity for the test data to serve as our baseline. Our choice of cosine similarity stems from its fundamental design for measuring distance between vectors. Euclidean Distance and Manhattan Distance were not chosen for two reasons: Both these distances are highly sensitive to changes in high-dimensional spaces. Additionally, they are influenced by magnitude, which could result in misleading distance measurements in our context.
  - **2) Loss function:** Comparing the loss functions of the training dataset and test dataset provides insights into how well the model is trained and whether there are any overfitting or underfitting issues.
  - **3) Recall:** We chose recall as the evaluation metric over accuracy because the test data concerns about top-2 accuracy. Recall shows whether a model can find all objects of the target class, whereas accuracy indicates how often a model is correct overall. Hence, recall is a more representative metric for this project.

# Experiments
- A. Baseline
  - Directly calculate the cosine similarity for the test data.
- B. Feature Extraction and Cosine Similarity
  - We applied feature extraction on the test data using VGG, ResNet, and DenseNet, followed by the calculation of cosine similarity. The features extracted via VGG have 25088 dimensions, ResNet yields 2048 dimensions, and DenseNet produces 1024 dimensions. It’s evident that higher dimensions capture more information, potentially leading to better results.
- C. Siamese Networks Training
  - After feature extraction for both training and test data, we employed the Siamese Networks for model training. Though higher dimensions capture more intricate details, VGG’s 25088 dimensions pose computational challenges during training. Hence, we implemented max pooling to downsize this dimensionality to 512. Max pooling was preferred over average pooling due to its capacity to retain more informative features. Our model’s training involved various parameters:
    - **Architectures:** VGG, ResNet, and DenseNet.
    - **Batch sizes:** 64, 32, 16.
    - **Number of layers in the shared Siamese Network:** 1, 2.
    - **Distance metrics in the Siamese Network:** Manhattan Distance (L1) and Euclidean Distance (L2).
    - **Data augmentation:** Yes, No
 
# Conclusion
To summarize, our best results were achieved using only the feature extraction from VGG with a dimension of 25088. While we aimed for enhanced results by training the data using the Siamese Networks, the outcomes did not surpass those obtained from feature extraction alone. Despite testing 144 parameter combinations, the optimal outcome only surpassed the benchmark but fell short compared to our initial feature extraction results. However, it would be hasty to deduce that training doesn’t enhance prediction accuracy. Future experiments
could delve into a wider range of hyperparameters, alternative feature extraction architectures, and more intricate Siamese Network designs.
