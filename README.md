![DALL·E 2023-08-20 17 02 08 - X-Ray body part classification model](https://github.com/zmaktr/x-ray-body-part-classification/assets/90152617/58238549-fa60-449e-a4b4-b821d0ff47ed)
# Body Part Classification from X-ray Images

This repository contains code for classifying body parts from X-ray images using a pre-trained model. The model is designed to work with RGB images of size 224x224 pixels.

## Contents

- [Introduction](#introduction)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
- [Model and Labels](#model-and-labels)
- [Example Code](#example-code)
- [Contributing](#contributing)
- [License](#license)

## Introduction

X-ray image classification is an essential task in medical imaging. This repository provides a pre-trained model capable of classifying body parts in X-ray images. The provided model can be easily loaded and used to predict the body part present in an input image.

## Getting Started

### Prerequisites

- Python 3.x
- Required Python packages are listed in `requirements.txt`.

### Installation

1. Clone this repository to your local machine:

   ```bash
   git clone https://github.com/your-username/body-part-classification.git
   cd body-part-classification
   pip install -r requirements.txt
   ```

### Usage

To classify body parts in an X-ray image, follow these steps:

1. Prepare your input image in RGB format with a size of 224x224 pixels.
2. Normalize the image:

   ```
   import numpy as np

   image_array = ...  # Load your image as an array
   normalized_image = (image_array.astype(np.float32) / 127.5) - 1
   ```

3. Load the pre-trained model:

   ```
   from tensorflow.keras.models import load_model

   model = load_model('./model/keras_model.h5')
   ```

4. Use the model to predict the body part:
   ```
   prediction = model.predict(np.expand_dims(normalized_image, axis=0))
   predicted_class = np.argmax(prediction)
   with open('./model/labels.txt', 'r') as labels_file:
       labels = labels_file.read().splitlines()
   predicted_body_part = labels[predicted_class]
   print("Predicted Body Part:", predicted_body_part)
   ```

### Model and Labels

The pre-trained model is located in the ./model/keras_model.h5 file.
The corresponding labels for the model's output classes are stored in the ./model/labels.txt file.

### Example Code

For a complete usage example, refer to the ./scripts/4.Testing.ipynb file in the repository.
This file demonstrates how to load the model, preprocess an image, and make predictions.

### Contributing

Contributions to this repository are welcome. Feel free to open issues for bug reports, feature requests, or general discussions.

### License

This project is licensed under the MIT License.
