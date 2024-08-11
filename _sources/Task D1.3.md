---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Task D1.3

## Conduct a limited financial statement analysis employing horizontal, vertical and ratio analysis 

Horizontal, vertical and ratio analysis will allow students to practice basic financial statement analysis. Fundamental accounting textbooks demonstrate horizontal, vertical and ratio analysis of financial statements. In addition to textbook examples, YouTube has many demonstrations on how to set up horizontal and vertical analysis.

Video examples of Horizontal and Vertical Analysis in Excel:

[Vertical Analysis of an Income Statement in Excel by Chris Menard](https://www.youtube.com/watch?v=BmpbEVS4cP0)

[Horizontal analysis of financial statements](https://www.youtube.com/watch?v=8hLjVoKbKZ8)

[Excel: Liquidity Ratios - Current Ratio, Quick Ratio, & Cash Ratio](https://www.youtube.com/watch?v=c-YnvjUIwq4)

The SBUX Project requires students to add additional columns and rows in their Excel worksheets to accommodate horizontal and vertical analyses for all possible accounts in the IS and BS. For the CF Statements, we limited the analysis to the line items Net cash provided/used by operating activities, investing activities and financing activities to remain at a more basic level analysis.

Upon completing the horizontal and vertical analysis, students use the data on their spreadsheets to independently calculate all the ratios for each year from Figure 3, Required Common Ratios to Calculate. These common ratios are found in most accounting textbooks. Ratio analysis looks at the relationships of the different parts of financial statements. Combining horizontal and vertical analyses with ratio analysis provides powerful analytical tools to expose risk areas for decision-makers. Students calculate these ratios over at least two to three years (depending on the ratio) to expose more meaningful patterns beyond horizontal and vertical analyses and use the data to create charts to visualize the patterns alongside other ratios. Students are encouraged to use other ratios that they deem may be useful to their analyses.

```{figure} images/Required_Ratios_to_Calculate.jpg
:scale: 35 %
:alt: Required Common Ratios to Calculate

**Required Common Ratios to Calculate.** 
```

Performing horizontal, vertical, and ratio analyses provides an opportunity to achieve more Excel skills. As rows and columns are inserted, students demonstrate their ability to use technological tools to organize, structure, and present complex financial data for analysis through the creation of proper headers and footers, the use of color-coordinated schemes, developing formulas for subtotal and total data, and calculating ratios. 

```{code-cell} ipython3
:tags: [hide-input]

import pandas as pd

# Define the data as a dictionary
data = {
    "Ratio Type": [
        "Liquidity", "Liquidity", "Liquidity",
        "Solvency", "Solvency",
        "Profitability", "Profitability", "Profitability", "Profitability"
    ],
    "Ratio": [
        "Current ratio", "Inventory turnover", "Receivables turnover",
        "Debt to total assets", "Debt service coverage ratio",
        "Gross profit margin", "Profit margin ratio", "Return on assets ratio", "Asset turnover ratio"
    ],
    "Formula": [
        "Current Assets / Current Liabilities", "(Cost of Sales / (Beginning Inventory + Ending Inventory)) / 2", "(Net Sales Revenue / (Beginning Receivables + Ending Receivables)) / 2",
        "Total Liabilities / Total Assets", "Cash Flow from Operations / Total Liabilities",
        "Gross Profit / Net Sales", "Net Income / Net Sales", "(Net Income / (Beginning Assets + Ending Assets)) / 2", "(Net Sales / (Beginning Assets + Ending Assets)) / 2"
    ],
    "YouTube Video": [
        '<a href="https://www.youtube.com/watch?v=BCaoQNkeoy0">Liquidity Ratios | A-Level, IB & BTEC Business</a>',
        '<a href="https://www.youtube.com/watch?v=HqWTVzeVQBU">Inventory Turnover Ratio (Inventory Turns Per Period & Average Days To Sell Inventoy)</a>',
        '<a href="https://www.youtube.com/watch?v=Iz45aaYwnMk">Accounts Receivable Turnover</a>',
        '<a href="https://www.youtube.com/watch?v=vf-g51Br_l0">Long-Term Debt to Total Assets Ratio</a>',
        '<a href="https://www.youtube.com/watch?v=MrlqgSDsSig">Investopedia Video: The Debt-Service Coverage Ratio (DSCR)</a>',
        '<a href="https://www.youtube.com/watch?v=e2Dl6B7BWzs">Gross Profit and Gross Profit Margin | A-Level, IB & BTEC Business</a>',
        '<a href="https://www.youtube.com/watch?v=uYM2YnwO-20">Profit Margin, Gross Margin, and Operating Margin - With Income Statements</a>',
        '<a href="https://www.youtube.com/watch?v=fNXnXOB2CYk">Investopedia Video: Return On Assets (ROA)</a>',
        '<a href="https://www.youtube.com/watch?v=t0nHVLq4Fzk">What is Total Asset Turnover Ratio</a>'
    ]
}

# Create DataFrame
df = pd.DataFrame(data)

# Convert DataFrame to HTML without index
html_output = df.to_html(index=False, escape=False)  # escape=False to render HTML in links


# Styling functions
def style_specific_rows(row):
    if "Liquidity" in row['Ratio Type']:
        color = 'background-color: #86ffd4'  # Very light cyan - lime green for profitability
    elif "Solvency" in row['Ratio Type']:
        color = 'background-color: #d0ffef'  # Very Pale cyan - lime green for solvency
    elif "Profitability" in row['Ratio Type']:
        color = 'background-color: #eafff8'  # Very pale (mostly white) cyan - lime green for liquidity
    else:
        color = ''  # Default no color
    return [color] * len(row)

def header_styling():
    return {
        'selector': 'thead th',
        'props': [
            ('background-color', '#006241'),  # Starbucks Green, Very dark cyan - lime green
            ('color', 'white'),
            ('border-style', 'solid'),
            ('border-width', '1px'),
            ('border-color', 'black')
        ]
    }

# Apply styles
styled_df = df.style.apply(style_specific_rows, axis=1)
styled_df.set_table_styles([header_styling()])


# Display the styled DataFrame
styled_df
```


