# MLOPS_Airflow_Lab

# Airflow Labs - MLOps Course

## Repository Overview
This repository contains lab assignments for the MLOps course focused on Apache Airflow workflow orchestration. Each lab demonstrates practical implementation of ML pipelines using containerized environments.

## Labs

### Lab 1: ML Workflow Automation with K-Means Clustering
A complete machine learning pipeline using Apache Airflow and Docker that automates data clustering workflow with an exploratory data analysis step.

**Key Features:**
- 5-task sequential pipeline
- K-Means clustering implementation
- Elbow method for optimal cluster detection
- Exploratory Data Analysis integration
- Docker containerized deployment

**Technologies:** Apache Airflow 2.5.1, Docker, Python, pandas, scikit-learn, kneed
### Core Functions (src/lab.py)

1. **load_data()**
   - Loads data from CSV, serializes, and returns it
   
2. **perform_eda(data)** ⭐ NEW
   - Performs exploratory data analysis
   - Prints summary statistics and data insights
   - Passes data to next task
    

3. **data_preprocessing(data)**
   - Deserializes data, handles missing values
   - Applies MinMaxScaler to features
   - Returns serialized preprocessed data

4. **build_save_model(data, filename)**
   - Builds K-Means clustering model
   - Saves model to file
   - Returns SSE values for elbow method

5. **load_model_elbow(filename, sse)**
   - Loads saved model
   - Determines optimal clusters using kneed library
   - Returns predictions


## Course Information
- **Course:** MLOps
- **Instructor:** Ramin
- **Institution:** Northeastern University
- **Program:** Master's in Data Analytics Engineering

## Getting Started

### Prerequisites
- Docker Desktop
- WSL2 (Windows users)
- Git
- 4GB+ RAM allocated to Docker

### Quick Clone
```bash
git clone https://github.com/YourUsername/Airflow_Labs.git
cd Airflow_Labs
```

## Repository Structure
```
Lab_1/
├── dags/
│   ├── data/
│   │   ├── file.csv          # Training data
│   │   └── test.csv          # Test data
│   ├── model/
│   │   └── model.sav         # Saved K-Means model
│   ├── src/
│   │   ├── __init__.py
│   │   └── lab.py            # Core ML functions
│   └── airflow.py            # DAG definition
├── logs/
├── plugins/
├── config/
│   ├── airflow_dashboard.png
│   └── dag_graph.png
├── .env
├── docker-compose.yaml

```

## Workflow Pipeline
```
The DAG (`Airflow_Lab1`) consists of **5 tasks** executed sequentially:

1. **load_data_task** - Loads data from CSV file
2. **perform_eda_task** - Performs Exploratory Data Analysis (**NEW ADDITION**)
3. **data_preprocessing_task** - Cleans and scales data using MinMaxScaler
4. **build_save_model_task** - Trains K-Means model (k=1 to 49) and saves it
5. **load_model_task** - Loads model and determines optimal clusters using elbow method

### Pipeline Flow Diagram
```
load_data → perform_eda → data_preprocessing → build_save_model → load_mode

## Learning Outcomes
- Understanding Airflow DAG architecture
- Implementing ML pipelines with task dependencies
- Container orchestration with Docker
- Data serialization and XCom for inter-task communication
- Best practices for ML workflow automation

## Resources
- [Apache Airflow Documentation](https://airflow.apache.org/docs/)
- [Course Blog](https://www.mlwithramin.com/blog/airflow-lab1)
- [Tutorial Video](https://youtu.be/exFSeGUbn4Q?feature=shared)

## Author
**Sailee Choudhari**  
Master's Student - Data Analytics Engineering  
Northeastern University


## License
This project is part of academic coursework.

---

⭐ Star this repo if you find it helpful!
