# Job Salary Prediction Web App

A Flask-based web application for predicting job salaries and positions in the Philippines using machine learning models. Built with data mining techniques on job listings, it allows users to input experience levels and salaries to get predictions via linear regression, KNN, Naive Bayes variants, and K-means clustering.

## Features

- **Salary Prediction**: Predict annual salary based on position level and years of experience using Linear Regression.
- **Job Position Prediction**: Classify job roles (Junior, Senior, Project Manager, CTO) based on experience and salary using KNN.
- **Naive Bayes Classification**: Multiple variants (Gaussian, Multinomial, Bernoulli) for job position prediction.
- **K-Means Clustering**: Visualize job clusters based on experience and salary.
- **Interactive UI**: Simple web interface with forms for inputs and results display.
- **Data-Driven**: Trained on real Philippine job market data (scraped from job boards).

## Demo

Run the app locally or deploy to a server. Access endpoints like `/linear`, `/knn`, `/naive`, and `/kmeans` for different models.

## Installation

1. **Clone the Repository**:
   ```
   git clone https://github.com/yourusername/deyb12-data-mining.git
   cd deyb12-data-mining
   ```

2. **Create a Virtual Environment** (recommended):
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**:
   ```
   pip install -r requirements.txt
   ```

   Key packages:
   - Flask (web framework)
   - NumPy, scikit-learn (ML models)
   - Pandas, Matplotlib (data processing and visualization)
   - Gunicorn (production server)

4. **Load Models**:
   The app loads pre-trained models from the `Models/` directory:
   - `linreg_model.pkl`: Linear Regression for salary prediction.
   - `knn_model.pkl`: K-Nearest Neighbors for job classification.
   - `nbG_model.pkl`, `nbM_model.pkl`, `nbB_model.pkl`: Naive Bayes variants.
   - `km_model.pkl`: K-Means clustering (includes visualization pickle).

   Ensure these files are present; they were trained on `Clean_Job_data.csv`.

## Usage

1. **Run the App**:
   ```
   python app.py
   ```
   The server starts on `http://localhost:8000`.

2. **Navigate Pages**:
   - Home: `/` – Landing page.
   - About: `/about` – Project overview.
   - Classifier: `/classifier` – Model selection.
   - Linear Regression: `/linear` – Predict salary (input: position level 1-4, experience in years).
   - KNN: `/knn` – Predict job from experience and salary.
   - Naive Bayes: `/naive` – Multi-model job prediction.
   - K-Means: `/kmeans` – View clustered visualization.

3. **Example Predictions**:
   - **Linear**: Position 1 (Junior), 2 years experience → Predicted Salary: ~PHP 49,804.
   - **KNN**: 3 years experience, PHP 80,000 salary → Predicted Job: Senior.
   - **Naive Bayes**: Similar inputs yield classifications from Gaussian/Multinomial/Bernoulli models.
   - **K-Means**: Scatter plot showing clusters by experience vs. salary.

## Data

- **Source**: `Models/Job_data.csv` – Raw job listings (e.g., Junior Graphics Designer, salaries in PHP, experience levels).
- **Cleaned Data**: `Models/Clean_Job_data.csv` – Processed for training (Experience, Job_Pos, New Salary).
- Data focuses on Philippine job market (e.g., remote/hybrid roles in Manila, Cebu).

## Models Overview

| Model | Purpose | Input Features | Output |
|-------|---------|----------------|--------|
| **Linear Regression** | Salary Prediction | Position Level (1-4), Experience (years) | Predicted Salary (PHP) |
| **KNN** | Job Classification | Experience (years), Salary (PHP) | Job Role (e.g., Junior) |
| **Gaussian NB** | Job Classification | Experience, Salary | Job Role |
| **Multinomial NB** | Job Classification | Experience, Salary | Job Role |
| **Bernoulli NB** | Job Classification | Experience, Salary | Job Role |
| **K-Means (n=4)** | Clustering | Experience, Salary | Visual Clusters (Junior/Senior/etc.) |

Models were trained using scikit-learn on the cleaned dataset. Accuracy varies by model (e.g., KNN ~85% on test set).

## Development

- **Tech Stack**: Python 3.12, Flask, scikit-learn, Pandas, Matplotlib.
- **Training Notebook**: See `app.ipynb` for model training code (includes data cleaning, EDA, and visualization).
- **Port**: Defaults to 8000; customizable in `app.py`.

To retrain models:
1. Load `Clean_Job_data.csv` in a Jupyter notebook.
2. Use provided code snippets for fitting and pickling.

## Contributing

1. Fork the repo.
2. Create a feature branch (`git checkout -b feature/amazing-feature`).
3. Commit changes (`git commit -m 'Add amazing feature'`).
4. Push to branch (`git push origin feature/amazing-feature`).
5. Open a Pull Request.

## License

This project is open-source under the MIT License. See [LICENSE](LICENSE) for details (add if needed).
