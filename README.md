# LNG Pricing Automation

A comprehensive Python-based system for automating LNG(Liquefied Natural Gas) pricing sheet construction and analysis.

## Overview

This project automates the extraction of LNG futures prices from Barchart.com and constructs comprehensive pricing sheets with:
- Flat price curves for multiple LNG benchmarks
- Time spreads (M1/M2)
- Seasonal spreads (Summer/Winter)
- Quarterly strips and spreads
- Calendar year averages and spreads
- Geographical arbitrage calculations

## Features

### Data Sources
- **Henry Hub (NG)**: Natural gas futures from CME
- **Brent (QA)**: Oil futures for energy correlation
- **TTF (INK)**: European gas hub futures
- **JKM (JKM)**: Asian LNG benchmark
- **NBP (NF)**: UK gas hub with FX conversion

### Output Sheets
1. **Flat Prices**: Clean price curves for all commodities
2. **Spread Summary**: Comprehensive spread analysis including:
   - Monthly time spreads
   - Quarterly strips
   - Seasonal contracts
   - Calendar year averages.

### Automation Features
- Automatic data fetching from Barchart.com
- Dynamic contract symbol generation
- Forward FX rate integration for NBP pricing
- Excel export with professional formatting
- Email distribution system

## Requirements

### Python Dependencies
```
selenium
beautifulsoup4
requests
pandas
numpy
xlsxwriter
python-dateutil
```

### Environment Variables
- `EMAIL_PASSWORD`: Gmail password for automated email sending

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/lng-pricing-automation.git
cd lng-pricing-automation
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Set up environment variables:
```bash
export EMAIL_PASSWORD="your_gmail_password"
```

## Usage

### Basic Execution
```bash
python LNG_pricing_sheet_construction.py
```

### Jupyter Notebook
Open `LNG_curve_building_guidance.ipynb` for interactive development and testing.

## Configuration

The system is configurable through the `commodity_config` dictionary in the main script:

```python
commodity_config = {
    'NG': {'label': "Henry Hub ($/MMBtu)", 'base_code': 'NG', 'years': 12, 'has_cash': True, 'cash_symbol': 'NGY00'},
    'QA': {'label': "Brent ($/bbl)", 'base_code': 'QA', 'years': 8, 'has_cash': True, 'cash_symbol': 'QAY00'},
    'INK': {'label': "TTF ($/MMBtu)", 'base_code': 'INK', 'years': 3, 'has_cash': False},
    'JKM': {'label': "JKM ($/MMBtu)", 'base_code': 'JKM', 'years': 5, 'has_cash': False},
    'NF': {'label': "NBP (p/th)", 'base_code': 'NF', 'years': 7, 'has_cash': False}
}
```

## Output

The system generates an Excel file with the naming convention:
```
LNG_Pricing_Sheet_YYYY-MM-DD.xlsx
```

### Sheet 1: Flat Prices
- Clean price curves for all commodities
- FX rates for NBP conversion
- Geographical spreads

### Sheet 2: Spread Summary
- Monthly time spreads
- Quarterly strips and spreads
- Seasonal contracts (Summer/Winter)
- Calendar year averages and spreads

## Email Distribution

The system automatically emails the generated pricing sheet to specified recipients with configurable CC and BCC lists.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is proprietary and confidential. All rights reserved.

## Support

For questions or support, please contact the development team.

## Disclaimer

This tool is for internal use only. Please ensure compliance with all applicable data usage policies and terms of service for external data sources.
