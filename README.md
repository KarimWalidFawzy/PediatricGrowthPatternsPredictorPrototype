# Patient Curve Assistant

A comprehensive tool for analyzing pediatric growth patterns using World Health Organization (WHO) child growth standards. This assistant helps healthcare professionals assess child growth trajectories, calculate weight-for-age percentiles, and visualize growth curves against international standards.

## 📋 Overview

The Patient Curve Assistant is designed to:
- Download and process WHO child growth standards data
- Calculate precise weight-for-age percentiles using interpolation
- Generate visual comparisons between patient data and growth standards
- Support both girls and boys from birth to 5 years of age
- Provide interactive charts for clinical decision-making

## 🚀 Features

### Data Management
- **Automatic Data Download**: Fetches 8 WHO datasets covering weight-for-age standards
- **Comprehensive Coverage**: Includes both z-scores and percentiles for girls and boys
- **Age Range Support**: From 0-13 weeks and 0-5 years
- **Data Integrity**: Built-in error handling and status checking

### Clinical Calculations
- **Precise Percentile Calculation**: Uses scipy interpolation for accurate centile determination
- **Flexible Input**: Accepts age in days, weight in kg, and sex
- **Interpolation Methods**: Handles both exact matches and interpolated values
- **Boundary Handling**: Properly manages edge cases (very low/high weights)

### Visualization
- **Growth Curve Plots**: Matplotlib-based percentile curves
- **Interactive Charts**: Plotly-based comparative analysis
- **Patient Comparison**: Overlay individual patient data on standards
- **Export Capability**: Saves interactive charts as HTML files

## 📊 Data Sources

The assistant uses official WHO child growth standards:
- **Weight-for-Age Standards**: Both z-scores and percentiles
- **Gender-Specific**: Separate standards for girls and boys
- **Expanded Tables**: Detailed percentile data for precise calculations
- **Source**: World Health Organization Child Growth Standards

## 🛠️ Installation

### Prerequisites
- Python 3.7+
- Jupyter Notebook or JupyterLab
- Internet connection for data downloads

### Required Packages
```bash
pip install openpyxl matplotlib seaborn scikit-learn scipy plotly nbformat pandas numpy requests
```

### Setup
1. Clone or download the project
2. Open `data_analysis.ipynb` in Jupyter
3. Run the installation cell to ensure all dependencies are available
4. Execute cells sequentially to load data and initialize functions

## 📖 Usage

### Basic Workflow

1. **Data Loading**: Run the data loading cells to download WHO standards
2. **Function Initialization**: Import required libraries and functions
3. **Centile Calculation**: Use `get_predicted_centile(age_days, weight_kg, sex)`
4. **Visualization**: Generate growth curves and patient comparisons

### Example Usage

```python
# Calculate percentile for a 30-day-old female weighing 3.5kg
centile = get_predicted_centile(30, 3.5, 'female')
print(f"Percentile: {centile:.1f}")  # Output: Percentile: 10.4

# Plot growth curves for the first 100 days
plot_growth_curves('female', (0, 100))

# Compare patient data against standards
patient_data = pd.DataFrame({
    'age_days': [7, 14, 21, 30, 60, 90],
    'weight_kg': [3.0, 3.2, 3.5, 4.0, 5.5, 7.0],
    'sex': ['female'] * 6
})
plot_patient_vs_standards(patient_data, 'female')
```

### Patient Data Format

Patient data should be provided as a pandas DataFrame with columns:
- `age_days`: Age in days (numeric)
- `weight_kg`: Weight in kilograms (numeric)
- `sex`: 'female' or 'male' (string)

## 📈 Clinical Applications

### Growth Monitoring
- Track individual patient growth trajectories
- Identify growth faltering or excessive growth
- Monitor response to nutritional interventions

### Screening and Assessment
- Calculate precise percentiles for clinical decision-making
- Compare against international standards
- Support early identification of growth disorders

### Research and Analysis
- Batch processing of patient cohorts
- Statistical analysis of growth patterns
- Epidemiological studies

## 🔧 Technical Details

### Interpolation Method
- Uses `scipy.interpolate.interp1d` with linear interpolation
- Handles age-based interpolation between data points
- Manages percentile boundaries appropriately

### Data Structure
- **Expanded Tables**: 1857 data points per gender
- **Percentile Range**: P01 (1st) to P999 (99.9th percentile)
- **Age Precision**: Daily intervals for accurate calculations

### Visualization Options
- **Matplotlib**: Static plots for reports and publications
- **Plotly**: Interactive charts for clinical review
- **HTML Export**: Browser-compatible interactive visualizations

## 📁 Project Structure

```
PatientCurveAssistant/
├── Prototype/
│   ├── data_analysis.ipynb    # Main analysis notebook
│   ├── growth_chart.html      # Generated interactive chart
│   └── README.md             # This file
```

## ⚠️ Important Notes

### Data Privacy
- No patient data is stored or transmitted
- All calculations are performed locally
- WHO data is downloaded securely from official sources

### Limitations
- Based on weight-for-age only (other anthropometric measures not included)
- Requires internet connection for initial data download
- Designed for children 0-5 years of age

### Clinical Disclaimer
- This tool is for educational and research purposes
- Clinical decisions should be made by qualified healthcare professionals
- Results should be interpreted in the context of complete clinical assessment

## 🤝 Contributing

To contribute to this project:
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly with clinical data
5. Submit a pull request

## 📄 License

This project is provided for educational and research purposes. Please ensure compliance with WHO data usage policies and local regulations regarding health data analysis.

## 📞 Support

For technical issues or questions:
- Check the notebook comments for detailed explanations
- Verify all dependencies are properly installed
- Ensure WHO data downloads complete successfully

## 🔗 References

- World Health Organization Child Growth Standards
- WHO Multicentre Growth Reference Study
- UNICEF/WHO Technical Report on Child Growth Standards

---

**Developed for pediatric healthcare professionals and researchers (Especially my beloved father)** 🏥📊 