# MOVIE RECOMMENDATION SYSTEM WITH FACIAL EMOTION RECOGNITION

This project implements a real-time facial expression recognition system that suggests movies based on the detected emotion. It utilizes a pre-trained Keras model for emotion classification and integrates with a movie dataset to provide personalized recommendations.

## Features

*   **Webcam Integration**: Captures live video feed from the user's webcam.
*   **Face Detection**: Detects human faces in the captured video stream using OpenCV's Haar cascades.
*   **Facial Emotion Recognition**: Predicts one of seven basic emotions (Angry, Disgust, Fear, Happy, Neutral, Sad, Surprise) from the detected face.
*   **Movie Recommendation**: Suggests a movie title from a dataset based on the predicted emotion and a predefined genre mapping.
*   **Real-time Output**: Displays the detected emotion and the recommended movie directly in the Colab output.

## Technologies Used

*   **Python 3**
*   **Keras**: For loading and utilizing the pre-trained emotion detection model.
*   **OpenCV (cv2)**: For image processing, webcam capture, face detection, and drawing annotations.
*   **Pandas**: For data manipulation, especially with the movie dataset.
*   **NumPy**: For numerical operations, particularly with image data.
*   **`google.colab` utilities**: For webcam access and displaying images in Google Colab notebooks.

## Setup

To run this project, you need a Google Colab environment. 

1.  **Clone the Repository**: Download the notebook and associated files (or upload them to your Colab environment).
2.  **Model File**: Ensure the pre-trained Keras model file (`FER_model (1).h5`) is available in the `/content/` directory or update the `model_path` variable to its correct location.
3.  **Movie Dataset**: Ensure the movie recommendation CSV file (`movierecom.csv`) is available in the `/content/` directory or update the `pd.read_csv` path accordingly.

### Required Libraries
The following Python libraries are required. They can be installed using pip:
```bash
!pip install opencv-python-headless keras h5py
```
(This is already included in the first cell of the notebook.)

## Usage

1.  **Open the Colab Notebook**: Open the `.ipynb` file in Google Colab.
2.  **Run All Cells**: Execute all cells in the notebook sequentially.
3.  **Webcam Access**: When prompted, grant access to your webcam. A 'Capture' button will appear. Click it to take a photo.
4.  **View Output**: The notebook will then process the captured image, detect your facial expression, and display the detected emotion along with a suggested movie. The image with the detected face and emotion label will also be shown.

## How it Works

1.  **Image Capture**: The `take_photo` JavaScript function captures an image from your webcam.
2.  **Face Detection**: OpenCV's Haar Cascade classifier (`haarcascade_frontalface_default.xml`) is used to detect faces within the captured image.
3.  **Emotion Prediction**: The detected face region is resized to 48x48 pixels, converted to grayscale, normalized, and fed into the loaded Keras model for emotion prediction.
4.  **Movie Suggestion**: Based on the predicted emotion, the code looks up associated movie genres in `emotion_to_genres` dictionary. It then randomly selects a movie from the `movierecom.csv` dataset that matches these genres.

### Emotion to Genre Mapping:

*   **Happy**: Comedy, Adventure, Fantasy, Musical
*   **Sad**: Comedy, Family, Fantasy, Animation
*   **Angry**: Action, Thriller, Crime
*   **Fear**: Horror, Thriller, Mystery
*   **Neutral**: Drama, Documentary, History
*   **Disgust**: Comedy, Fantasy
*   **Surprise**: Mystery, Fantasy, Science Fiction
