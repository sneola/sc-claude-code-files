# E-commerce Business Analytics Dashboard

A comprehensive business intelligence solution featuring both Jupyter notebook analysis and a professional Streamlit dashboard for e-commerce sales data with configurable time periods and reusable business metrics calculations.

## Overview

This project transforms a basic exploratory data analysis into a professional, maintainable business intelligence framework. The refactored solution provides:

- **Configurable Analysis**: Easily analyze any time period or compare different years
- **Modular Architecture**: Reusable data loading and metrics calculation modules
- **Professional Visualizations**: Business-oriented charts with proper formatting
- **Strategic Insights**: Automated generation of business recommendations

## Project Structure

```
data_analysis/
├── EDA_Refactored.ipynb     # Main analysis notebook
├── dashboard.py             # Streamlit dashboard application
├── data_loader.py           # Data loading and processing module
├── business_metrics.py      # Business metrics calculation module
├── requirements.txt         # Python dependencies
├── README.md               # This file
└── ecommerce_data/         # Data directory
    ├── orders_dataset.csv
    ├── order_items_dataset.csv
    ├── products_dataset.csv
    ├── customers_dataset.csv
    ├── order_reviews_dataset.csv
    └── order_payments_dataset.csv
```

## Features

### 1. Configurable Analysis Framework
- Set analysis year, comparison year, and month filters
- Flexible time period analysis without code changes
- Automatic handling of missing data periods

### 2. Comprehensive Business Metrics
- **Revenue Analysis**: Total revenue, growth rates, average order value
- **Product Performance**: Category analysis, revenue share, top performers
- **Geographic Insights**: State-level revenue and order analysis
- **Customer Satisfaction**: Review scores, satisfaction distribution
- **Delivery Performance**: Delivery times, speed categorization

### 3. Professional Visualizations
- Monthly revenue trend charts
- Product category performance bars
- Interactive geographic heatmaps
- Customer satisfaction distributions
- Consistent color schemes and formatting

### 4. Automated Insights
- Strategic recommendations based on data patterns
- Performance benchmarking and alerts
- Executive summary generation

## Installation and Setup

### Prerequisites
- Python 3.8 or higher
- Jupyter Notebook or JupyterLab (for notebook analysis)

### Installation Steps

1. **Clone or download the project files**

2. **Install required dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Ensure data files are in place**:
   - Place CSV files in the `ecommerce_data/` directory
   - Verify all required files are present (see Project Structure above)

4. **Run the applications**:

   **For Streamlit Dashboard**:
   ```bash
   streamlit run dashboard.py
   ```

   **For Jupyter Notebook Analysis**:
   ```bash
   jupyter notebook EDA_Refactored.ipynb
   ```

## Usage Guide

### Refactored Analysis Notebook (EDA_Refactored.ipynb)

The refactored notebook provides a complete, professional analysis framework with improved structure and documentation:

#### Key Improvements Over Original EDA:

1. **Structured Documentation**: Clear sections with table of contents and business objectives
2. **Configurable Analysis**: Easy-to-change parameters for different time periods
3. **Data Dictionary**: Comprehensive explanation of business terms and metrics
4. **Modular Code**: Reusable functions from imported modules
5. **Enhanced Visualizations**: Professional charts with proper titles, labels, and formatting
6. **Strategic Insights**: Automated recommendations based on analysis results

#### Quick Start Guide:

1. **Open the notebook**: Launch Jupyter and open `EDA_Refactored.ipynb`

2. **Set analysis parameters** (Cell 2):
   ```python
   ANALYSIS_YEAR = 2023        # Primary year to analyze
   COMPARISON_YEAR = 2022      # Year for comparison (set to None to disable)
   ANALYSIS_MONTH = None       # Specific month (1-12) or None for full year
   ```

3. **Run all cells** to generate the complete analysis with:
   - Executive summary with key metrics
   - Revenue trend analysis and growth rates
   - Product category performance rankings
   - Geographic market analysis with interactive maps
   - Customer satisfaction and delivery performance metrics
   - Strategic recommendations based on findings

4. **Customize for different periods**:
   ```python
   # Analyze Q1 2023 vs Q1 2022
   ANALYSIS_MONTH = [1, 2, 3]  # Can be modified in data_loader.py
   
   # Analyze just December 2023
   ANALYSIS_MONTH = 12
   ```

### Streamlit Dashboard

The professional Streamlit dashboard provides a comprehensive business analytics interface with real-time filtering and interactive visualizations.

#### Dashboard Layout Structure

1. **Header**: 
   - Title on the left: "E-commerce Analytics Dashboard"
   - Date range filter on the right (applies globally to all charts)

2. **KPI Row** (4 cards with uniform height):
   - **Total Revenue**: Current year total with trend indicator vs previous year
   - **Monthly Growth**: Average month-over-month growth with trend arrow
   - **Average Order Value**: Current AOV with trend indicator vs previous year  
   - **Total Orders**: Current year count with trend indicator vs previous year
   - All trend indicators show two decimal places with red/green color coding

3. **Charts Grid** (2x2 layout):
   - **Revenue Trend**: Line chart with solid line for current year, dashed line for previous year, grid lines, Y-axis formatted as $300K
   - **Top 10 Categories**: Horizontal bar chart sorted descending with blue gradient (darker = higher values), values formatted as $300K/$2M
   - **Revenue by State**: US choropleth map with blue gradient color-coding by revenue amount
   - **Satisfaction vs Delivery**: Bar chart showing average review score by delivery time buckets (1-3 days, 4-7 days, 8+ days)

4. **Bottom Row** (2 cards with uniform height):
   - **Average Delivery Time**: Days with trend indicator vs previous year
   - **Review Score**: Large number with star display and "Average Review Score" subtitle

#### Usage Instructions

1. **Launch the dashboard**:
   ```bash
   streamlit run dashboard.py
   ```

2. **Interactive Features**:
   - **Date Range Filter**: Select year in top-right dropdown (all charts update automatically)
   - **Hover Details**: Hover over charts for detailed data points
   - **Responsive Design**: Layout adapts to different screen sizes
   - **Real-time Updates**: All visualizations refresh when filter changes

3. **Key Dashboard Features**:
   - **Professional Styling**: Clean, business-ready interface with uniform card heights
   - **Trend Indicators**: Color-coded arrows (green ↗ positive, red ↘ negative) with precise percentages
   - **Currency Formatting**: Values displayed as $300K, $2M for easy reading
   - **Interactive Charts**: Plotly-powered visualizations with zoom, pan, and hover capabilities
   - **Error Handling**: Graceful handling of missing data with informative messages

4. **Visual Design**:
   - Blue gradient color schemes for consistency
   - No decorative elements or crowding
   - Professional typography and spacing
   - Consistent chart heights and margins

### Notebook Analysis

1. **Open the refactored notebook**: `EDA_Refactored.ipynb`

2. **Configure analysis parameters** in the first code cell:
   ```python
   ANALYSIS_YEAR = 2023        # Year to analyze
   COMPARISON_YEAR = 2022      # Comparison year (optional)
   ANALYSIS_MONTH = None       # Specific month or None for full year
   DATA_PATH = 'ecommerce_data/'
   ```

3. **Run all cells** to generate the complete analysis

### Advanced Configuration

#### Analyzing Specific Time Periods
```python
# Analyze only Q4 2023
for month in [10, 11, 12]:
    ANALYSIS_MONTH = month
    # Run analysis
```

#### Custom Data Paths
```python
# Use different data location
DATA_PATH = '/path/to/your/data/'
```

#### Filtering by Order Status
```python
# Modify in data_loader.py create_sales_dataset method
status_filter = 'delivered'  # or 'shipped', 'processing', etc.
```

### Module Usage

#### Data Loading Module
```python
from data_loader import EcommerceDataLoader, load_and_process_data

# Quick start
loader, processed_data = load_and_process_data('ecommerce_data/')

# Advanced usage
loader = EcommerceDataLoader('ecommerce_data/')
loader.load_raw_data()
processed_data = loader.process_all_data()

# Create filtered dataset
sales_data = loader.create_sales_dataset(
    year_filter=2023,
    month_filter=None,
    status_filter='delivered'
)
```

#### Business Metrics Module
```python
from business_metrics import BusinessMetricsCalculator, MetricsVisualizer

# Calculate metrics
metrics_calc = BusinessMetricsCalculator(sales_data)
report = metrics_calc.generate_comprehensive_report(
    current_year=2023,
    previous_year=2022
)

# Create visualizations
visualizer = MetricsVisualizer(report)
revenue_fig = visualizer.plot_revenue_trend()
category_fig = visualizer.plot_category_performance()
```

## Key Business Metrics

### Revenue Metrics
- **Total Revenue**: Sum of all delivered order item prices
- **Revenue Growth Rate**: Year-over-year percentage change
- **Average Order Value (AOV)**: Average total value per order
- **Monthly Growth Trends**: Month-over-month performance

### Product Performance
- **Category Revenue**: Revenue by product category
- **Market Share**: Percentage of total revenue by category
- **Category Diversity**: Distribution across product lines

### Geographic Analysis
- **State Performance**: Revenue and order count by state
- **Market Penetration**: Number of active markets
- **Regional AOV**: Average order value by geographic region

### Customer Experience
- **Review Scores**: Average satisfaction rating (1-5 scale)
- **Satisfaction Distribution**: Percentage of high/low ratings
- **Delivery Performance**: Average delivery time and speed metrics

## Output Examples

### Console Output
```
BUSINESS METRICS SUMMARY - 2023
============================================================

REVENUE PERFORMANCE:
  Total Revenue: $3,360,294.74
  Total Orders: 4,635
  Average Order Value: $724.98
  Revenue Growth: -2.5%

CUSTOMER SATISFACTION:
  Average Review Score: 4.10/5.0
  High Satisfaction (4+): 84.2%

DELIVERY PERFORMANCE:
  Average Delivery Time: 8.0 days
  Fast Delivery (≤3 days): 28.5%
```

### Generated Visualizations
- Monthly revenue trend line charts
- Top product category horizontal bar charts
- Interactive US state choropleth maps
- Customer satisfaction distribution charts

## Customization Options

### Adding New Metrics
1. Extend the `BusinessMetricsCalculator` class in `business_metrics.py`
2. Add visualization methods to `MetricsVisualizer` class
3. Update the notebook to display new metrics

### Custom Visualizations
```python
# Example: Custom visualization
def plot_custom_metric(self, data):
    fig, ax = plt.subplots(figsize=(12, 6))
    # Your visualization code
    return fig
```

### Data Source Modifications
- Modify `data_loader.py` to handle different CSV structures
- Update column mappings in the `EcommerceDataLoader` class
- Add new data validation rules

## Troubleshooting

### Common Issues

1. **Module Import Errors**:
   - Ensure all files are in the same directory
   - Check Python path configuration

2. **Missing Data Files**:
   - Verify CSV files are in the `ecommerce_data/` directory
   - Check file naming matches expected patterns

3. **Empty Results**:
   - Verify date filters match available data
   - Check order status filtering

4. **Visualization Issues**:
   - Ensure all required packages are installed
   - Check Plotly version compatibility for interactive maps

### Performance Optimization
- For large datasets, consider chunked processing
- Use data sampling for initial exploration
- Implement caching for repeated analysis

## Dashboard Features

### Layout Structure
- **Header**: Title with year selection filter (applies globally)
- **KPI Row**: 4 metric cards with trend indicators
  - Total Revenue, Monthly Growth, Average Order Value, Total Orders
  - Color-coded trends (green for positive, red for negative)
- **Charts Grid**: 2x2 interactive visualization layout
  - Revenue trend (current vs previous year)
  - Top 10 product categories bar chart
  - US state choropleth map
  - Customer satisfaction vs delivery time analysis
- **Bottom Row**: Customer experience metrics
  - Average delivery time with trend
  - Review score with star rating

### Technical Features
- **Real-time Filtering**: All visualizations update automatically
- **Professional Styling**: Business-ready interface with uniform card heights
- **Plotly Charts**: Interactive, publication-quality visualizations
- **Responsive Design**: Adapts to different screen sizes
- **Error Handling**: Graceful handling of missing data

## Future Enhancements

### Planned Features
- Real-time data connections
- Predictive analytics and forecasting
- Customer segmentation analysis
- A/B testing framework
- Automated report scheduling
- Export functionality (PDF reports)

### Extension Ideas
- Integration with business intelligence tools
- API endpoints for metrics access
- Machine learning model integration
- Advanced statistical analysis
- Mobile-responsive improvements

## Contributing

To extend this analysis framework:

1. Follow the existing code structure and documentation patterns
2. Add comprehensive docstrings to new functions
3. Include unit tests for new business logic
4. Update this README with new features

## License

This project is provided as-is for educational and business analysis purposes.

---

**Note**: This framework is designed to be easily maintained and extended for ongoing business intelligence needs. The modular architecture ensures that updates to data sources or metric calculations can be made without affecting the overall analysis structure.