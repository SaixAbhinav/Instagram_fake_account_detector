# Fake Instagram Account Detector

A machine learning-powered tool that leverages computer vision and meta-ensemble techniques to detect fake Instagram accounts. This project uses a combination of a Convolutional Neural Network (CNN) for profile picture classification, a Random Forest model for extracting Instagram profile features, and a meta-model to combine these predictions for a final verdict.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Overview

Instagram is a prime target for fake accounts that can spread misinformation or manipulate social interactions. This project aims to automatically classify Instagram accounts as "fake" or "real" by:
- Scraping profile pictures and Instagram metadata.
- Processing profile pictures using a pre-trained CNN model.
- Analyzing Instagram features (number of posts, followers, following, and follower-following ratio) using a Random Forest classifier.
- Combining both predictions with a meta-model (stacking) for a robust final prediction.

## Features

- **Instagram Scraping:**  
  - Downloads the profile picture using the [Instaloader](https://instaloader.github.io/) library.
  - Extracts Instagram metadata such as followers, following, number of posts, and bio.

- **Image Preprocessing & CNN Prediction:**  
  - Preprocesses profile images (resize and normalization) for the CNN.
  - Uses a TensorFlow-based CNN model to classify the profile picture as indicative of a fake or real account.

- **Random Forest Prediction:**  
  - Extracts key Instagram features.
  - Uses a scikit-learn Random Forest model to classify account authenticity based on numerical features.

- **Meta-Model Stacking:**  
  - Combines predictions from the CNN and Random Forest models.
  - Uses a pre-trained meta-model (also built with scikit-learn) to produce a final classification ("fake" or "real") after scaling the combined predictions.

- **API Service with FastAPI:**  
  - Provides an API endpoint (`/predict/`) to input an Instagram username and receive:
    - Final prediction ("fake" or "real")
    - Instagram profile details (followers, following, number of posts, bio)
    - URL for the downloaded profile picture
  - Serves static files and a basic index page for potential front-end integration.

## Technologies Used

- **Programming Language:** Python
- **Machine Learning & Deep Learning:**  
  - TensorFlow (for CNN model)
  - scikit-learn (for Random Forest and meta-model)
- **Web Framework:** FastAPI (for API endpoints)
- **Web Scraping:** Instaloader (for downloading Instagram profile data)
- **Image Processing:** Pillow (PIL)
- **Data Handling:** NumPy
- **Model Serialization:** joblib
- **HTTP Requests:** requests
