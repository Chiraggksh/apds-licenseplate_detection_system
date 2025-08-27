🚗 License Plate Detection & Verification System

This project is an AI-powered License Plate Detection System built with YOLOv8 (Ultralytics) for license plate detection and Tesseract OCR for text extraction.
The system further matches the detected license plate numbers against a vehicle database to verify ownership, detect stolen vehicles, and support policy implementations such as Odd-Even traffic rules.

✨ Features

🔍 Automatic License Plate Detection

Uses YOLOv8 to detect and crop license plates from CCTV/vehicle images.

📝 OCR-based Text Extraction

Extracts alphanumeric registration numbers using Tesseract OCR.

Cleans noisy OCR output with regex and fuzzy matching for higher accuracy.

📚 Vehicle Database Matching

Matches extracted license plates against a simulated vehicle database.

Provides details such as owner, car model, year, and current status (Active / Stolen).

🚨 Stolen Vehicle Detection

In real-world usage, once a stolen vehicle is reported in an FIR database,
the system can automatically detect its presence through CCTV cameras and send alerts.

🅾️ Odd-Even Policy Implementation

Can be extended to enforce Odd-Even traffic rules by verifying plate numbers in real time.

📷 Image Output

Returns both the original image and the cropped license plate image as base64 (for frontend integration).

⚙️ Tech Stack

Backend Framework: Flask + Flask-CORS

Object Detection: YOLOv8 (Ultralytics)

OCR: Tesseract OCR + PIL

Database: Simulated (Python dictionary) – extendable to SQL/NoSQL

Others: Regex, Difflib (fuzzy matching), OpenCV, NumPy

📂 Project Workflow

Upload an Image → The system receives the vehicle image (from CCTV / camera).

YOLO Inference → Detects the license plate region.

OCR Processing → Extracts text from the cropped license plate.

Cleaning & Matching → Uses regex + fuzzy matching to map OCR text to actual license plate records.

Database Lookup → Fetches details (owner, car model, year, stolen/active status).

Alert Generation →

If stolen, trigger alert with CCTV location & timestamp.

If Odd-Even policy violation, flag the vehicle.

Response → Returns JSON with:

Extracted license plate number

Vehicle details paragraph

Original + Cropped plate image in Base64 format
📋 Example API Response
{
  "plate_number": "DL7CO1939",
  "vehicle_info": {
    "owner": "Chirag Kaushik",
    "car_model": "Creta",
    "year": "2017",
    "status": "Stolen"
  },
  "vehicle_info_paragraph": "The vehicle with registration number DL7CO1939 is a Creta model from the year 2017. It is owned by Chirag Kaushik, and the current status of the vehicle is Stolen.",
  "original_image": "data:image/jpeg;base64,...",
  "plate_image": "data:image/jpeg;base64,..."
}

🚀 Getting Started
1️⃣ Clone the Repository
git clone https://github.com/yourusername/license-plate-detection.git
cd license-plate-detection

2️⃣ Install Dependencies
pip install -r requirements.txt

3️⃣ Set up Tesseract OCR

Install Tesseract OCR
.

Update the path in app.py if necessary:

pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'

4️⃣ Run the Flask Server
python app.py

5️⃣ API Endpoint

POST /process

Body: Form-data with key "image" → Vehicle image file

🔮 Future Scope

📌 Integration with real FIR/stolen vehicle databases

📌 Real-time CCTV stream processing for live detection

📌 Geo-tagging CCTV cameras to provide exact location of detection

📌 Dashboard for traffic enforcement & stolen vehicle tracking

📌 Support for multiple languages in OCR

🛡️ Use Cases

Law Enforcement → Automated stolen vehicle detection from CCTV feeds.

Traffic Management → Enforce Odd-Even policy and congestion control.

Toll Booths / Parking Lots → Automated vehicle entry & exit logging.

Smart Cities → Real-time vehicle tracking and safety alerts.

👨‍💻 Author

Chirag Kaushik
🚀 Passionate about AI, Computer Vision, and building real-world impactful solutions.
