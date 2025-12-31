# Lead Conversion Predictor

A machine learning project to predict lead conversion probability for an education company using logistic regression.

## 📋 Problem Statement

**X Education** is an online education company that sells courses to industry professionals. The company markets its courses on various websites and search engines like Google. When professionals land on their website and fill up a form providing their email address or phone number, they are classified as a **lead**. The company also acquires leads through past referrals.

The sales team then contacts these leads through calls and emails. However, the current lead conversion rate is only around **30%**, which is quite low. For example, out of 100 leads acquired in a day, only about 30 get converted into paying customers.

### The Challenge

The company needs to identify the most promising leads (also known as **'Hot Leads'**) to improve the lead conversion rate. By focusing the sales team's efforts on high-potential leads rather than contacting everyone, the conversion rate should increase significantly. The CEO has set a target lead conversion rate of around **80%**.

### Solution

This project builds a **logistic regression model** to assign a **lead score between 0 and 100** to each lead. A higher score indicates a "hot lead" that is most likely to convert, while a lower score indicates a "cold lead" with lower conversion probability. This scoring system helps the sales team prioritize their efforts and improve overall conversion rates.

## 🎯 Objective

The primary goals of this project are:

1. **Build a Predictive Model**: Develop a logistic regression model to predict lead conversion probability
2. **Lead Scoring System**: Assign a lead score (0-100) to each lead based on conversion probability
3. **Identify Hot Leads**: Help the sales team identify and prioritize high-potential leads
4. **Improve Conversion Rate**: Increase the lead conversion rate from 30% to the target of 80%
5. **Business Impact**: Enable the sales team to focus on leads with higher conversion probability

## 📊 Dataset

The dataset contains approximately **9,000 data points** with various attributes about leads, including:

- **Lead Information**: Lead origin, lead source, prospect ID
- **Demographic Data**: Country, occupation, specialization
- **Behavioral Metrics**: 
  - Total visits to the website
  - Total time spent on website
  - Page views per visit
- **Engagement Data**: Last activity, last notable activity
- **Marketing Channels**: Search, newspaper articles, digital advertisements, recommendations
- **Preferences**: Course selection criteria, interest in free materials
- **Target Variable**: `Converted` (1 = converted, 0 = not converted)

**Note**: Many categorical variables contain a level called 'Select' which is treated as a null value since it indicates the user didn't make a selection.

## 🔧 Methodology

### 1. Data Cleaning
- Removed duplicate records
- Handled missing values (replaced 'Select' with NaN, filled missing values with 'not provided')
- Removed columns with single unique values
- Removed columns with >35% missing values
- Bucketed country values into categories (India, Outside India, Not Provided)

### 2. Exploratory Data Analysis (EDA)
- **Univariate Analysis**: Analyzed distribution of categorical and continuous variables
- **Bivariate Analysis**: Examined relationship between features and target variable
- **Outlier Analysis**: Identified and handled outliers using IQR method

### 3. Feature Engineering
- Created dummy variables for categorical features
- Scaled numerical features using MinMaxScaler
- Applied Recursive Feature Elimination (RFE) to select top 15 features

### 4. Model Building
- **Algorithm**: Logistic Regression
- **Feature Selection**: RFE with 15 features
- **Multicollinearity Check**: Used VIF (Variance Inflation Factor) to remove highly correlated features
- **Final Model**: Selected features with low p-values (<0.05) and low VIF values (<5)

### 5. Model Evaluation
- **Metrics Used**:
  - Accuracy
  - Sensitivity (Recall)
  - Specificity
  - Precision
  - ROC-AUC Score
- **Optimal Cutoff**: Determined using precision-recall curve (0.42)
- **Lead Scoring**: Conversion probability converted to score (0-100)

## 📈 Key Results

### Model Performance

The logistic regression model achieved strong performance metrics:

- **Train Set Accuracy**: 81.09%
- **Test Set Accuracy**: 80.17%
- **Sensitivity (Recall)**: 82.23%
- **Specificity**: 79.01%
- **ROC-AUC Score**: 88.36%
- **Precision**: 73.24%
- **Optimal Cutoff Threshold**: 0.42

The model demonstrates excellent predictive power with an ROC-AUC score of 88.36%, indicating strong ability to distinguish between converting and non-converting leads. The test accuracy of 80.17% means the model correctly predicts lead conversion approximately 4 out of 5 times.

### Top Features

The top 3 most important features contributing to lead conversion (based on feature importance analysis):

1. **TotalVisits** - Number of website visits is the strongest predictor of conversion
2. **Total Time Spent on Website** - Leads spending more time on the website show higher conversion probability
3. **Lead Origin (Lead Add Form)** - Leads originating from the lead add form have significantly higher conversion rates

## 🚀 Getting Started

### Prerequisites
- Python 3.7+
- Jupyter Notebook

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/lead-conversion-predictor.git
cd lead-conversion-predictor
```

2. Install required packages:
```bash
pip install -r requirements.txt
```

3. The dataset is already included in the repository (`Leads.csv`)

4. Run the notebook:
```bash
jupyter notebook lead-conversion-predictor.ipynb
```

## 📁 Project Structure

```
lead-conversion-predictor/
│
├── lead-conversion-predictor.ipynb  # Main analysis notebook
├── Leads.csv                         # Dataset
├── requirements.txt                  # Python dependencies
├── README.md                         # Project documentation
└── .gitignore                        # Git ignore file
```

## 🛠️ Technologies Used

- **Python**: Core programming language
- **Pandas**: Data manipulation and analysis
- **NumPy**: Numerical computations
- **Matplotlib & Seaborn**: Data visualization
- **Scikit-learn**: Machine learning algorithms and evaluation metrics
- **Statsmodels**: Statistical modeling and VIF calculation

## 📝 Key Insights

### Business Insights

1. **Website Engagement Matters**: Leads with multiple visits and higher time spent on the website are significantly more likely to convert. This suggests that nurturing leads through engaging website content can improve conversion rates.

2. **Lead Source Quality**: Leads from the "Lead Add Form" show higher conversion probability, indicating that this source generates higher-quality leads compared to other channels.

3. **Model Reliability**: With 80%+ accuracy and 88% ROC-AUC, the model provides reliable predictions that sales teams can trust for prioritizing their efforts.

4. **Conversion Rate Improvement Potential**: By focusing on leads with scores above 42 (optimal threshold), the sales team can potentially move from the current 30% conversion rate toward the target of 80%.

5. **Resource Optimization**: The lead scoring system enables better allocation of sales resources, allowing the team to focus on high-probability leads while still maintaining contact with lower-scoring leads as capacity allows.

### Recommendations

- **Implement Lead Scoring**: Deploy the scoring system to assign scores to all incoming leads
- **Prioritize High-Score Leads**: Focus immediate sales efforts on leads with scores above 42
- **Monitor and Refine**: Continuously monitor model performance and retrain periodically with new data
- **A/B Testing**: Test the impact of prioritizing high-score leads on overall conversion rates

## 👤 Author

*[Your name]*

## 📄 License

This project is open source and available under the MIT License.

## 🙏 Acknowledgments

- **X Education** for providing the dataset and business context
- This project was developed as part of a case study to improve lead conversion rates

