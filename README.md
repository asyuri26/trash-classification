# trash-classification
This project is an implementation of an image classification model for the TrashNet dataset using a tuned DenseNet121 architecture. The model is implemented with TensorFlow and uses Weights & Biases (WandB) for experiment tracking, training, as well as model artefact management.

*Fitur Proyek*
- Model : DenseNet121 with fine-tuning
- Preprocessing Data : Resize, one-hot encoding for labeling
- Augmentasi Fata : Image augmentation on the training dataset using RandomFlip, RandomRotation, and RandomZoom
- Wandb for parameter and metrics during train session
- Balancing Data : Class balancing using class weights to handle data imbalance
- Deployment : Model saved into format model.h5

*How to Implement*
- Initialize WandB: Start a new WandB session to track training parameters such as model type, batch size, epochs, and learning rate.
- Load Dataset: The garythung/trashnet dataset is loaded using load_dataset from the datasets library and split into training and validation sets.
- Preprocessing & Augmentation:
  -  The preprocess() function resizes and normalizes images and performs one-hot encoding for labels.
  -  Data augmentation is applied to the training set using RandomFlip, RandomRotation, and RandomZoom.
- Class Weights Calculation: compute_class_weight is used to handle class imbalance.
- Model Creation with DenseNet121:
  - DenseNet121 is imported from tensorflow.keras.applications as a base model without the top layer and is followed by additional layers for classification.
- Model Training:
  - The model is trained with the wandb.keras.WandbCallback() to log metrics and weights.
  - steps_per_epoch and validation_steps are used to ensure all data is processed in each epoch.
- Model Evaluation & Saving:
  - The model is evaluated on the validation set, and the final accuracy is printed.
  - The model is saved as an artifact in WandB for versioning and tracking.

*Additional Notes*
- This project uses the datasets API and requires an internet connection to download the garythung/trashnet dataset.
- Adjust parameters like test_size and model configuration as needed for specific experiment requirements.
