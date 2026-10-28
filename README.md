# 🍔 Food Delivery Time Prediction

A machine learning-powered web application that estimates food delivery time based on delivery distance, traffic conditions, preparation time, delivery partner experience, weather, time of day, and vehicle type.

The application combines a trained regression model with a Flask web interface and MySQL-based user authentication.

## ✨ Features

- **Delivery Time Prediction:** Estimate delivery duration using a trained machine learning model.
- **User Registration:** Create an account with username, email, and password.
- **Secure Login:** Password hashing and session-based authentication.
- **Interactive Web Interface:** Web pages for the home page, about section, prediction, and methodology.
- **Multiple Input Factors:** Consider distance, traffic, preparation time, experience, weather, time of day, and vehicle type.
- **Model Persistence:** Load the saved machine learning model and traffic encoder using Joblib.
- **Database Integration:** Store and retrieve user account information through MySQL.

## 🛠️ Tech Stack

| Category | Technologies |
|---|---|
| Programming Language | Python |
| Backend | Flask |
| Machine Learning | Scikit-learn |
| Data Processing | NumPy |
| Model Persistence | Joblib |
| Database | MySQL |
| Frontend | HTML, CSS, JavaScript, Bootstrap |
| Configuration | python-dotenv |
| Development | Jupyter Notebook, VS Code |

## 🧠 How It Works

1. The user registers or logs in to the application.
2. The user opens the prediction page and enters the delivery details.
3. Traffic, weather, time of day, and vehicle inputs are encoded into numerical features.
4. The application passes the processed features to the saved regression model.
5. The model predicts the estimated delivery duration.
6. The result is displayed on the web page in minutes.

### Input Features

- Delivery distance
- Traffic level
- Preparation time
- Delivery partner experience
- Weather conditions
- Time of day
- Vehicle type

## 📂 Project Structure

```text
Food_delivery_project/
│
├── app.py                         # Flask application and routes
├── requirements.txt               # Python dependencies
├── Food_Delivery_Times.csv        # Dataset
├── Food delivery regression (1).ipynb  # Model development notebook
├── delivery_time_model.pkl        # Saved regression model
├── traffic_encoder.pkl            # Saved traffic encoder
├── model_columns.pkl              # Saved model feature information
├── .gitignore
│
├── templates/
│   ├── base.html
│   ├── index.html
│   ├── about.html
│   ├── methodology.html
│   ├── predict.html
│   ├── login.html
│   └── register.html
│
└── static/
    ├── css/
    ├── js/
    ├── img/
    ├── lib/
    └── scss/
```

## ⚙️ Installation and Setup

### Prerequisites

- Python 3.10 or later
- MySQL Server
- Git

### 1. Clone the repository

```bash
git clone https://github.com/keerthanakulal/Food_delivery_project.git
cd Food_delivery_project
```

### 2. Create and activate a virtual environment

**Windows PowerShell:**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

If PowerShell blocks activation, use Command Prompt and run:

```bat
.venv\Scripts\activate.bat
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Configure environment variables

Create a `.env` file in the project root directory:

```env
FLASK_SECRET_KEY=replace_with_a_secure_random_secret
FLASK_DEBUG=False

DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=food_db
```

Replace the example values with your local configuration. Generate a strong random secret for `FLASK_SECRET_KEY`.

**Security:** Never commit your `.env` file or publish database credentials.

### 5. Set up the MySQL database

Start your MySQL server and execute the following SQL to create the database and the user table expected by the application:

```sql
CREATE DATABASE IF NOT EXISTS food_db;

USE food_db;

CREATE TABLE IF NOT EXISTS users (
    u_id INT AUTO_INCREMENT PRIMARY KEY,
    uname VARCHAR(100) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL
);
```

If your MySQL username, password, or database name differs, update the `.env` file accordingly.

### 6. Run the application

```bash
python app.py
```

Open the following URL in your browser:

**http://127.0.0.1:4000**

Register an account and log in to access the prediction feature.

## 📈 Model and Dataset

The repository includes a dataset, a Jupyter Notebook for regression-model development, and serialized model artifacts.

- `Food_Delivery_Times.csv` — dataset used for the project.
- `Food delivery regression (1).ipynb` — notebook for exploring the data and developing the regression model.
- `delivery_time_model.pkl` — saved regression model used for predictions.
- `traffic_encoder.pkl` — saved encoder used to transform traffic-level inputs.
- `model_columns.pkl` — saved model feature information.

The prediction application constructs a numerical feature vector from the user's inputs before generating an estimated delivery duration.

## 🔐 Security Considerations

- User passwords are hashed using Werkzeug security utilities.
- Database queries use parameterized SQL for user authentication and registration.
- Session configuration uses a secret key supplied through environment variables.
- Local configuration and secret files should remain excluded from version control.

Before deploying the application publicly, configure production-grade session security, database permissions, input validation, and HTTPS.

## 🚀 Future Improvements

- Evaluate model performance using appropriate regression metrics such as MAE, RMSE, and R².
- Add visualizations for exploratory data analysis and model evaluation.
- Improve input validation and error handling.
- Add prediction history for registered users.
- Deploy the application to a production hosting platform.
- Add automated tests for prediction and authentication routes.

## 👩‍💻 Author

**Keerthana Kulal**

GitHub: [keerthanakulal](https://github.com/keerthanakulal)

---

*This project demonstrates the integration of machine learning, Flask web development, data preprocessing, and MySQL database connectivity in a food delivery time estimation application.*
