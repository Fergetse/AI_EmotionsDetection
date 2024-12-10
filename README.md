
# Real-Time Emotion Detection  

This repository contains a Python-based project that uses OpenCV and a pre-trained XML model to recognize human emotions in real-time through video. The system processes live video input, detects faces, and predicts emotions like happiness, anger, and surprise.  

---

## Features  
- **Real-Time Emotion Detection:** Detects emotions in real-time using a webcam feed.  
- **Customizable Models:** Utilizes a pre-trained FisherFaceRecognizer model (`emociones_model_3.xml`).  
- **Facial Detection:** Employs Haar Cascade for face detection.  
- **Scalable Emotion Recognition:** Predefined emotion labels with room for expansion.  

---

## Prerequisites  

Ensure you have the following installed:  
- Python 3.x  
- OpenCV (`cv2`)  

To install OpenCV:  
```bash  
pip install opencv-python opencv-contrib-python  
```  

---

## Usage  

1. Clone the repository:  
   ```bash  
   git clone https://github.com/yourusername/emotion-detection.git  
   cd emotion-detection  
   ```  

2. Place the following files in the same directory:  
   - `emociones_model_3.xml`: The pre-trained emotion recognition model.  
   - `haarcascade_frontalface_alt.xml`: Haar Cascade XML for face detection.  

3. Run the script:  
   ```bash  
   python emotion_detection.py  
   ```  

---

## Code Explanation  

1. **Loading the Pre-Trained Model**  
   The FisherFaceRecognizer model is loaded from the XML file:  
   ```python  
   faceRecognizer = cv.face.FisherFaceRecognizer_create()  
   faceRecognizer.read('emociones_model_3.xml')  
   ```  

2. **Face Detection**  
   Haar Cascade is used to detect faces in the video stream:  
   ```python  
   rostro = cv.CascadeClassifier('haarcascade_frontalface_alt.xml')  
   rostros = rostro.detectMultiScale(gray, 1.03, 4)  
   ```  

3. **Emotion Recognition**  
   For each detected face, the model predicts the corresponding emotion:  
   ```python  
   result = faceRecognizer.predict(frame2)  
   if result[1] < 400:  
       cv.putText(frame, '{}'.format(faces[result[0]]), ...)  
   ```  

4. **Live Video Feed**  
   The live feed from the webcam is processed frame by frame:  
   ```python  
   cap = cv.VideoCapture(0)  
   while True:  
       ret, frame = cap.read()  
       ...  
   ```  

---

## Emotion Labels  
The system currently detects the following emotions:  
- Happy  
- Angry  
- Surprised  
(Unused labels are placeholders and can be updated for additional emotions.)  

---

## Example Output  
The program displays the webcam feed with bounding boxes around detected faces, along with the predicted emotion label and confidence level.  

---

## Keybindings  
- Press `Esc` to exit the program.  

---

## Contribution  
Feel free to fork the repository and submit pull requests for improvements, additional emotion labels, or new features!  

---

## License  
This project is licensed under the MIT License. See the `LICENSE` file for details.  

---  
Happy Coding! 😊
