# CNN_Classification
🐱🐶 Cat vs Dog Image Classifier using CNN

A Deep Learning project that classifies images as Cat 🐱 or Dog 🐶 using a Convolutional Neural Network (CNN) built with TensorFlow and Keras.

📌 Project Overview

This project implements a CNN model trained on 100x100 RGB images to classify cats and dogs.

The model:

Uses Data Augmentation

Applies multiple Conv2D + MaxPooling layers

Uses Dropout to reduce overfitting

Achieves ~70%+ validation accuracy

🧠 Model Architecture

The CNN consists of:

Input (100x100x3)
↓
Conv2D (32 filters) + ReLU
↓
MaxPooling2D
↓
Dropout (0.25)
↓
Conv2D (64 filters) + ReLU
↓
MaxPooling2D
↓
Dropout (0.25)
↓
Conv2D (128 filters) + ReLU
↓
MaxPooling2D
↓
Dropout (0.25)
↓
Flatten
↓
Dense (128 neurons) + ReLU
↓
Dropout (0.5)
↓
Dense (1 neuron) + Sigmoid

🔹 Loss Function:

binary_crossentropy

🔹 Optimizer:

Adam

🔹 Evaluation Metric:

Accuracy

📂 Dataset Structure

The project uses CSV formatted image datasets:

input.csv
labels.csv
input_test.csv
labels_test.csv


Each image:

Resized to 100x100

RGB format (3 channels)

Pixel values normalized between 0 and 1

Dataset Size:

Dataset	Samples
Training	2000
Testing	400
🔄 Data Preprocessing

Reshaped to: (samples, 100, 100, 3)

Normalized using:

X_train = X_train / 255.0
X_test = X_test / 255.0

🔁 Data Augmentation

To improve generalization:

ImageDataGenerator(
    rotation_range=20,
    width_shift_range=0.2,
    height_shift_range=0.2,
    zoom_range=0.2,
    horizontal_flip=True
)


This helps prevent overfitting.

📊 Training Details

Epochs: 30

Batch Size: 32

Final Validation Accuracy: ~70%

Final Validation Loss: ~0.54

🎯 Model Performance
Test Accuracy: 70.75%
Test Loss: 0.5438


The model successfully predicts whether an image contains a cat or a dog.

🖼 Example Prediction Code
y_pred = model.predict(X_test[idx2, :].reshape(1, 100, 100, 3))
y_pred = y_pred > 0.5

if(y_pred[0][0] == 0):
    pred = 'dog'
else:
    pred = 'cat'

💾 Saving the Model
model.save('model.h5')


The trained model is saved as:

model.h5


You can later load it using:

from tensorflow.keras.models import load_model
model = load_model('model.h5')

🛠 Technologies Used

Python

NumPy

Matplotlib

TensorFlow

Keras

🚀 How to Run the Project

Clone the repository:

git clone <your-repo-link>
cd cat-dog-classifier


Install dependencies:

pip install numpy matplotlib tensorflow


Run the script:

python main.py

📌 Future Improvements

Increase dataset size

Add EarlyStopping callback

Use BatchNormalization

Try Transfer Learning (VGG16 / ResNet50)

Deploy using Flask or Streamlit

📷 Project Output

Trained CNN Model

Accuracy and Loss metrics

Random image prediction display

👨‍💻 Author

Madduri Jaya Himanshu Sharma
GitHub: https://github.com/himanshu-sharma27

📜 License

This project is open-source and available under the MIT License.
