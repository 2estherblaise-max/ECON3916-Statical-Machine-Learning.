# 📊 Economic Data Science Portfolio

Welcome! I'm Esther, a sophomore at Northeastern University pursuing dual degrees in Business Administration and Economics with a concentration in Finance. This repository showcases my journey in **ECON 3916: Statistical & Machine Learning for Economics**, where I'm learning to bridge traditional economic theory with modern data science techniques.

## 🎯 About This Portfolio

This collection represents my exploration of the intersection between economics and machine learning. Through this coursework, I'm developing skills that combine:

- **Causal Inference**: Understanding *why* economic relationships exist and how policy interventions create real-world impacts
- **Predictive Analytics**: Leveraging machine learning to forecast outcomes and identify patterns in complex economic data
- **Scalable Thinking**: Taking foundational statistical concepts (like OLS regression) and extending them with modern ML algorithms (like Lasso, Ridge, and ensemble methods)

My goal is to demonstrate how economic intuition and computational tools work together to solve meaningful problems in data analysis, economic consulting, and finance.

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google_Colab-F9AB00?style=for-the-badge&logo=google-colab&logoColor=white)
![Statsmodels](https://img.shields.io/badge/Statsmodels-4B8BBE?style=for-the-badge&logo=python&logoColor=white)

**Core Libraries & Tools:**
- **Python**: Primary programming language for data analysis and modeling
- **Pandas**: Data manipulation and exploratory analysis
- **Scikit-Learn**: Machine learning model development and evaluation
- **Statsmodels**: Econometric modeling and statistical inference
- **Google Colab**: Cloud-based development and collaboration

## 📂 Repository Structure

Each folder in this repository contains labs, problem sets, and projects that demonstrate the "Concept Extension" methodology—starting with classical econometric foundations and scaling up to machine learning applications.

## 🚀 What I'm Learning

- Regularization techniques (Lasso, Ridge, Elastic Net) for high-dimensional economic data
- Cross-validation and model selection strategies
- Causal inference frameworks alongside predictive modeling
- Real-world applications in labor economics, finance, and policy analysis

## 📫 Connect With Me

I'm actively seeking opportunities in **data analysis, economic consulting, and finance** where I can apply these skills to drive data-informed decision-making. Feel free to explore my work and reach out!

---

*This portfolio is a living document of my growth as an economist and data scientist. I'm eager to learn, collaborate, and contribute to meaningful projects.*

# The Cost of Living Crisis: A Data-Driven Student Inflation Analysis

## 📊 Project Overview

This project reveals a critical gap between official government inflation statistics and the real economic pressures facing college students. Using Federal Reserve economic data and custom index construction, I demonstrate that **student-specific inflation significantly outpaces** the Consumer Price Index (CPI) reported in national headlines.

**Key Finding:** Between 2016 and 2024, my custom Student Price Index (SPI) shows students experienced substantially higher cost increases than the official CPI suggests, driven primarily by education and housing expenses.

---

## 🎯 The Problem

The official Consumer Price Index (CPI) is designed to reflect the "average American household." However:

- **Students aren't average** - Our spending is concentrated in tuition, rent, and food
- **Geographic disparities exist** - National averages hide local market realities (e.g., Boston vs. rural areas)
- **Weighting matters** - Housing represents ~34% of official CPI, but can be 50%+ of a student budget

**Research Question:** *How much does student-specific inflation diverge from official government statistics?*

---

## 🔬 Methodology

### Data Sources
- **Federal Reserve Economic Data (FRED API)** - Official government price indices
- **Time Period:** January 2016 - December 2024
- **Geographic Scope:** National USA and Boston-Cambridge-Newton metro area

### Index Components & Proxies

Since the Bureau of Labor Statistics doesn't track "Chipotle burritos" or "Spotify subscriptions," I mapped student expenses to official CPI categories:

| Student Expense | FRED Series Code | Official Category |
|----------------|------------------|-------------------|
| Tuition | CUSR0000SEEB | Tuition, Fees & Childcare |
| Rent | CUSR0000SEHA | Rent of Primary Residence |
| Streaming Services | CUSR0000SERA02 | Cable & Streaming TV |
| Dining Out | CUSR0000SEFV | Food Away From Home |

### Technical Approach

**1. Data Normalization (Laspeyres Index Theory)**
```python
# All series re-indexed to Jan 2016 = 100
Value_Normalized = (Value_Current / Value_Jan2016) * 100
```

**Why this matters:** FRED indices have different base years (1982, 2002, etc.). Without normalization, comparing a series at 900 vs. 100 is meaningless—like comparing Celsius to Fahrenheit.

**2. Custom Weighting Schema**
```python
Student_SPI = (Tuition × 0.40) + (Rent × 0.30) + 
              (Food_Away × 0.25) + (Streaming × 0.05)
```

Weights reflect actual student budget allocation vs. the CPI's generic household weights.

**3. Regional Comparison**
Added Boston-Cambridge-Newton CPI (CUURA103SA0) to test whether local market conditions diverge from national trends.

---

## 📈 Key Findings

### 1. **The Student Inflation Premium**
Students face a **[X]% inflation gap** compared to official CPI figures. While national CPI increased by [Y]%, the Student SPI rose [Z]%.

### 2. **Geographic Disparities**
Boston-area students experience [higher/lower] inflation than the national average, with the Boston CPI tracking at [percentage] compared to the national baseline.

### 3. **Category-Specific Drivers**
- **Tuition:** [X]% increase (largest contributor)
- **Rent:** [Y]% increase (second-largest impact)
- **Food Away From Home:** [Z]% increase
- **Streaming Services:** Most stable category

*(Note: Insert your actual percentages from the final chart values)*

---

## 🛠️ Technologies Used

- **Python 3.x** - Core analysis language
- **Libraries:**
  - `fredapi` - Federal Reserve data retrieval
  - `pandas` - Data manipulation and time series handling
  - `matplotlib` - Data visualization
  - `numpy` - Numerical computations
- **APIs:** FRED (Federal Reserve Economic Data)
- **Development Environment:** Jupyter Notebook

---

## 📊 Visualizations

### Student SPI vs. Official CPI (National & Boston)
![Inflation Comparison Chart](path/to/your/chart.png)

*The red shaded area represents the "reality gap" between student costs and official inflation metrics.*

---

## 💡 Business Insights

**For Policy Makers:**
- Student loan calculations and financial aid packages based on national CPI may systematically underestimate student need

**For Financial Services:**
- Student-focused products (banking, credit) should consider SPI-adjusted metrics rather than standard CPI

**For Universities:**
- Demonstrates the compounding effect of tuition increases beyond general inflation

---

## 🚀 How to Run This Analysis

1. **Clone the repository:**
```bash
   git clone https://github.com/yourusername/student-inflation-analysis.git
```

2. **Install dependencies:**
```bash
   pip install fredapi pandas matplotlib numpy
```

3. **Get a FRED API key** (free):
   - Visit: https://fred.stlouisfed.org/docs/api/api_key.html
   - Register and copy your key

4. **Run the Jupyter Notebook:**
```bash
   jupyter notebook student_inflation_analysis.ipynb
```

5. **Insert your API key** in the notebook where indicated

---

## 📚 Future Enhancements

- [ ] Expand analysis to include textbook costs and technology fees
- [ ] Add interactive Plotly visualizations
- [ ] Compare multiple metro areas (NYC, SF, Chicago)
- [ ] Incorporate income data to calculate real purchasing power changes
- [ ] Build a web dashboard for real-time SPI tracking

---

## 👤 Author

**[Your Name]**
- LinkedIn: [your-profile]
- Portfolio: [your-website]
- Email: [your-email]

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## 🙏 Acknowledgments

- Federal Reserve Bank of St. Louis for maintaining FRED
- Bureau of Labor Statistics for CPI methodology documentation
- [Your University/Professor Name] for project guidance

---

**⭐ If you found this analysis valuable, please star this repository!**
