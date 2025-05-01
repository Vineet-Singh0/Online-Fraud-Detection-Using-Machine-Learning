# Fraud Detection

This project uses a Decision Tree Classifier to detect fraudulent financial transactions using a dataset of over 6 million records. The workflow includes data preprocessing, exploratory data analysis, feature engineering, model training, and prediction.

## Dataset

The dataset (`data.csv`) contains the following columns:

- `step`: Time step (hour) of the transaction
- `type`: Type of transaction (e.g., PAYMENT, TRANSFER, CASH_OUT, DEBIT, CASH_IN)
- `amount`: Amount of the transaction
- `nameOrig`: Customer ID of the originator
- `oldbalanceOrg`: Initial balance of the originator
- `newbalanceOrig`: New balance of the originator after the transaction
- `nameDest`: Customer ID of the recipient
- `oldbalanceDest`: Initial balance of the recipient
- `newbalanceDest`: New balance of the recipient after the transaction
- `isFraud`: Whether the transaction is fraudulent (1) or not (0)
- `isFlaggedFraud`: Whether the transaction was flagged as fraud by the system

## Project Structure

```
Fraud_Detection/
  ├── cyber.ipynb      # Main Jupyter notebook with code and analysis
  ├── data.csv         # Transaction dataset
  └── .ipynb_checkpoints/
```

## Requirements

- Python 3.11+
- pandas
- numpy
- seaborn
- matplotlib
- scikit-learn
- plotly

You can install the required packages with:

```bash
pip install pandas numpy seaborn matplotlib scikit-learn plotly
```

## Workflow

1. **Data Loading & Exploration**
   - Load the dataset and check for missing values.
   - Explore transaction types and their distributions.

2. **Data Preprocessing**
   - Encode categorical variables (e.g., transaction type).
   - Map the `isFraud` column to human-readable labels.
   - Select relevant features for modeling.

3. **Model Training**
   - Split the data into training and testing sets.
   - Train a Decision Tree Classifier on the training data.

4. **Evaluation**
   - Evaluate the model's accuracy on the test set.
   - Example accuracy: ~99.97% (note: may be due to class imbalance).

5. **Prediction**
   - Predict fraud status for new transactions using the trained model.

## Example Usage

In the notebook, you can predict if a transaction is fraudulent:

```python
# Example: Predict for a CASH_OUT transaction
model.predict([[2, 95340.00, 153450.00, 0.00]])  # Output: ['Fraud']

# Example: Predict for a PAYMENT transaction
model.predict([[1, 15000.00, 20000.00, 5000.00]])  # Output: ['No Fraud']
```

## Notes

- The model uses only a subset of features: `type`, `amount`, `oldbalanceOrg`, `newbalanceOrig`.
- The `type` column is encoded as integers:
  - PAYMENT: 1
  - CASH_OUT: 2
  - CASH_IN: 3
  - TRANSFER: 4
  - DEBIT: 5
- The dataset is highly imbalanced; most transactions are not fraud.

## Visualization

The notebook includes visualizations of transaction type distributions using Plotly.

## License

This project is for educational purposes. 
