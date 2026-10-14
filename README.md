# Kidney Disease Classification using VGG16

A deep learning and MLOps project for classifying kidney CT scan images into **Normal** and **Tumor** categories using transfer learning with VGG16.

The project includes a data ingestion pipeline, model preparation, model training, evaluation, experiment tracking with MLflow, pipeline orchestration with DVC, and a Flask web interface for local predictions.

> **Note:** This project is intended for educational and research purposes. Its predictions are not a substitute for professional medical diagnosis.

## Features

- **VGG16 Transfer Learning:** Uses a pretrained convolutional neural network as the foundation for image classification.
- **Data Ingestion:** Downloads and prepares the dataset for the pipeline.
- **Model Preparation:** Configures the base model for the classification task.
- **Model Training:** Trains and saves the updated model.
- **Model Evaluation:** Evaluates the trained model and records evaluation results.
- **MLflow:** Tracks experiments locally.
- **DVC:** Defines and manages the machine learning pipeline stages.
- **Flask Web UI:** Provides a local interface for submitting images and viewing predictions.

## Technologies

- Python 3.8
- TensorFlow 2.12
- Keras / VGG16
- Flask
- MLflow
- DVC
- NumPy and other dependencies listed in `requirements.txt`

## Project Structure

```text
.
├── app.py
├── main.py
├── requirements.txt
├── setup.py
├── params.yaml
├── dvc.yaml
├── dvc.lock
├── config/
│   └── config.yaml
├── src/
│   └── cnnClassifier/
│       ├── components/
│       ├── config/
│       ├── entity/
│       ├── pipeline/
│       └── utils/
├── templates/
├── research/
├── model/
├── .gitignore
└── README.md
```

The exact contents of some directories may vary depending on the local setup. Generated datasets, trained model files, and local MLflow logs are not included in the Git repository by default.

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/kidney-disease-classification-mlops.git
cd kidney-disease-classification-mlops
```

Replace `YOUR-USERNAME` with the GitHub account that owns the repository.

### 2. Create and activate the Conda environment

```bash
conda create -n KidneyPro python=3.8.20 -y
conda activate KidneyPro
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

If a dependency fails to install, check the Python and package versions supported by the project before changing the environment.

## Dataset and Model Preparation

The dataset and trained model are generated or retrieved through the project pipeline. They are not necessarily included in the GitHub repository.

Check `config/config.yaml` for the configured dataset source and local output paths. Ensure you have permission to access the dataset and that its source is still available.

## Running the Pipeline

From the project root, activate the Conda environment and run:

```bash
python main.py
```

This is the pipeline entry point in the local project. It runs the configured stages for data ingestion, model preparation, training, and evaluation, provided the required files, dataset source, and dependencies are available.

The DVC pipeline is defined in `dvc.yaml`. To run it through DVC, use:

```bash
dvc repro
```

The DVC command requires the configured DVC stages and their dependencies to be available. If the project uses a remote DVC data store, configure access to that store separately.

## Run the Web Application

After the required model and data artifacts have been generated, start the Flask application:

```bash
python app.py
```

Open the local address displayed in the terminal in your web browser. If the application uses port `8088`, the address is typically:

```text
http://127.0.0.1:8088
```

Upload a supported kidney CT scan image to test the prediction interface.

## Experiment Tracking with MLflow

MLflow is used to track local machine learning experiments.

The local tracking directory is:

```text
mlruns/
```

This directory is excluded from Git by default because it contains generated experiment data. Reproduce experiments locally to generate new tracking records.

## Configuration

- `config/config.yaml`: Dataset paths and artifact locations.
- `params.yaml`: Model and training parameters.
- `dvc.yaml`: Pipeline stages and dependencies.
- `dvc.lock`: Recorded DVC stage state and dependency information.

Review these files before running the project in a new environment.

## Limitations

- The trained model and dataset may need to be generated or downloaded separately.
- Results depend on dataset quality, preprocessing, model configuration, and training settings.
- A successful local prediction does not establish clinical accuracy or reliability.
- The web application is intended for local demonstration unless additional deployment and security measures are implemented.

## Future Improvements

- Add automated tests for preprocessing and prediction.
- Add model performance visualizations and evaluation reports.
- Configure a remote DVC storage location for sharing large artifacts.
- Add continuous integration checks for code quality and reproducibility.
- Improve the web interface and deployment documentation.

## License

Add the license that matches the project's intended use and the licenses of the dataset and pretrained model. Do not assume that every dataset or pretrained model can be redistributed.

## Author

**YOUR NAME**

GitHub: https://github.com/YOUR-USERNAME
