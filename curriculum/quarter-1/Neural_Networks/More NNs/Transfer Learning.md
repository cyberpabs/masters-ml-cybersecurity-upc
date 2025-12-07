**Goal:** To leverage the complex, general features (like edge detection in images or sentence structure in text) learned by an existing model (the **Source Model**) that was trained on enormous datasets (like ImageNet or Wikipedia). _This saves massive computational resources and time, and is particularly effective when the **Target Task** has limited data._
  
**Mechanism:** Instead of starting the new model with random weights, you initialize it with the pre-trained weights from the source model. You then typically only retrain (or **fine-tune**) the last few layers for your specific classification problem. 
  
**Design Principle:** Models used for Transfer Learning are often designed to be **task-agnostic** in their initial layers, allowing the transferred features to be useful across different domains. 
![[transfer_learning_example.png|400]]
#### Key Transfer Learning Models in Classification

| Model                      | Source Domain                               | Target Classification Use                                                                                                |
| :------------------------- | :------------------------------------------ | :----------------------------------------------------------------------------------------------------------------------- |
| **[[VGG16]] / [[ResNet]]** | [[ImageNet]] (Millions of Images)           | [[Image classification]] (e.g., medical scans, product defects)                                                          |
| **[[MobileNetV2]]**        | [[ImageNet]] (Millions of Images)           | **Efficient** [[Image Classification]], Object Detection, and Semantic Segmentation (especially for mobile/edge devices) |
| **[[BERT]]**               | General Text Corpus (Wikipedia, BookCorpus) | [[Text Classification]] (e.g., sentiment analysis, spam detection)                                                       |
> Transfer learning on VGG16 involves training only the **final 3 layers** for our
> specific object detection/classification task. 

You can [[Fine Tuning|fine-tune]] a pre-trained BERT model on: 

- **Sentiment analysis dataset** (like IMDb movie reviews). BERT can then classify whether a given text expresses positive or negative sentiment. 
  
- **QA datasets** such as _SQuAD_. After fine-tuning, it can answer questions by selecting the most relevant span of text from a passage.
  
- **NER dataset** allows it to recognize entities like people’s names, organizations, and locations in new text. 
  
- **Spam detection datasets**, to classify emails or messages as spam or non-spam.

### Types
- [[Inductive Transfer Learning]]
- [[Transductive Transfer Learning]]
- [[Unsupervised Transfer Learning]]