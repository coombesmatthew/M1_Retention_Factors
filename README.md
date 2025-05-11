# 🔁 M1 User Retention — Logistic Regression Model

This project is a basic implementation of logistic regression to predict **M1 retention**, which refers to whether a user returns and places another order within 30 days of their first purchase.

We use simple historical order data and run a logistic regression to understand what factors increase or decrease the chances of a user coming back. The model also gives us **odds ratios**, which tell us how each input feature affects user retention.

---

## 📌 What This Project Does

- Loads a CSV file of user orders
- Cleans the data by dropping rows with missing values
- Prepares the input features (e.g. delivery fee, item count, city)
- Trains a logistic regression model to predict `Return_in_30_Days`
- Calculates **odds ratios** to interpret the model’s output

---

## 📂 Dataset Requirements

Your input CSV should contain the following columns:

| Column Name       | Description                            |
|-------------------|----------------------------------------|
| `user_id`         | Unique user identifier                 |
| `city`            | City of the user or delivery           |
| `Delivery_Fee`    | Delivery fee amount                    |
| `Items`           | Number of items in the order           |
| `Missing_Item`    | Number of items reported missing       |
| `Order_Value`     | Total order value                      |
| `Total_Discount`  | Total discount applied                 |
| `Completion_Time` | Time taken to complete the delivery    |
| `Return_in_30_Days` | Target variable (1 = returned, 0 = did not return) |

---

## ⚙️ How It Works

1. **Data Cleaning**  
   Drops any rows with missing data.

2. **Feature Selection**  
   Uses the following input features to train the model:
   - Categorical: `city`  
   - Numerical: `Delivery_Fee`, `Items`, `Missing_Item`, `Order_Value`, `Total_Discount`, `Completion_Time`

3. **Model Pipeline**  
   - Scales numerical features
   - One-hot encodes the city column
   - Fits a logistic regression model with these features

4. **Model Interpretation**  
   - Calculates coefficients from the model
   - Converts them to **odds ratios**
   - Sorts and displays which features have the most influence on M1 retention

---

## 📈 Example Output

After training, the script prints a table like this:

| Feature                  | Coefficient | Odds Ratio |
|--------------------------|-------------|------------|
| `Order_Value`            | 0.43        | 1.53       |
| `Missing_Item`           | -0.77       | 0.46       |
| `city_Riyadh`            | 0.22        | 1.25       |

- Odds ratio > 1 means **more likely** to return  
- Odds ratio < 1 means **less likely** to return

---

## ▶️ How to Run

1. Clone this repo or copy the script
2. Make sure you have a file named `test_sample.csv` with the correct columns
3. Run the script in Python (Google Colab or Jupyter Notebook works well)
4. View the printed odds ratio table

---

## 🛠️ Requirements

- Python 3.7+
- pandas
- scikit-learn
- numpy

You can install dependencies with:

```bash
pip install pandas scikit-learn numpy
