# Bluesky SMS Notification Service

This project allows users to receive SMS notifications via Twilio whenever a specified Bluesky user posts. Users can enter their phone number and the Bluesky username they want to follow. The backend uses Firebase Firestore to store user subscriptions and periodically checks for new posts by the specified Bluesky user.

## Features
- Sign up for SMS notifications for Bluesky posts.
- Automatically checks for new posts and sends SMS alerts.
- Simple frontend with form validation and formatting for U.S.-based phone numbers.

## Prerequisites
- Python 3.9 or later
- Google Cloud Platform account for Firebase
- Twilio account for sending SMS messages

## Setup Instructions

### Step 1: Clone the Repository
```bash
git clone https://github.com/your-username/bluesky-sms-notification.git
cd bluesky-sms-notification
```

### Step 2: Install Dependencies
Create a virtual environment and install the required packages.

```bash
python -m venv venv
```
On Unix, activate your virtual environment with
```bash
source venv/bin/activate
```
On Windows, use 
```powershell
venv\Scripts\activate
```

Install all dependencies
```bash
pip install -r requirements.txt
```

### Step 3: Twilio Setup
Sign up for a Twilio account if you haven't already.
From your Twilio dashboard, create a new project or select an existing one.
Obtain your Account SID and Auth Token from the Twilio Console.
Purchase a Twilio phone number capable of sending SMS.
Update main.py with your Twilio credentials:
```python
TWILIO_ACCOUNT_SID = 'your_account_sid'
TWILIO_AUTH_TOKEN = 'your_auth_token'
TWILIO_PHONE_NUMBER = 'your_twilio_phone_number'
```

### Step 4: Firebase Setup
Go to the Firebase Console and create a new project or select an existing Google Cloud project.
Under Build > Firestore Database, click Create Database and choose Start in production mode.
Go to Project Settings > Service accounts > Generate new private key. This will download a JSON file with your Firebase credentials.
Place the JSON file in your project directory and update main.py to reference it:
```python
cred = credentials.Certificate("path/to/your-firebase-adminsdk.json")
```

### Step 5: Run the Application
```python
main.py
```

The application will run on http://localhost:8080. You can access the signup form at this URL.

### Step 6 (Optional): Google Cloud Deployment
This project can be deployed on Google Cloud App Engine, and comes with a template apps.yaml file that I used in my own testing.

Set up Google Cloud CLI and initialize your project.
Update app.yaml with your project's configurations.
Deploy with:
```bash
gcloud app deploy
```
### Project Structure
```plaintext
├── main.py               # Main Flask application with Twilio and Firebase integration
├── requirements.txt      # Project dependencies
├── templates/
│   └── index.html        # Frontend form for user input
├── static/               # Static assets (e.g., CSS, JS)
└── app.yaml              # Google App Engine configuration
```

License:
MIT License

Author:
Brandon Pimentel <3
