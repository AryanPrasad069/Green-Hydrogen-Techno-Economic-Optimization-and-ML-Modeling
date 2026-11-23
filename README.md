# Techno-Economic Optimization and ML Modelling of a Solar-Powered Alkaline Electrolyzer

A techno-economic and environmental assessment of a standalone solar photovoltaic (PV) system coupled to a pressurised alkaline electrolyzer for green hydrogen production in **Jodhpur, Rajasthan, India**.

The project combines hourly energy-balance modelling, PV–electrolyzer capacity sizing, levelized cost of hydrogen (LCOH) estimation, environmental screening, and machine-learning surrogate modelling.

## Project overview

Solar PV generation varies throughout the day, while an alkaline electrolyzer has minimum-load and rated-capacity operating limits. An undersized PV array can leave electrolyzer capacity underused; an oversized array can increase capital cost and solar curtailment.

This project evaluates the trade-off between PV capacity and electrolyzer capacity for a standalone, off-grid system with no battery or grid backup. The objective is to compare system configurations and identify the lowest calculated LCOH within the tested design grid.

## System boundary and modelling assumptions

The model includes:

- Solar PV electricity generation.
- Electrical performance losses represented through a performance ratio.
- A pressurised alkaline electrolyzer with a 15% minimum-load threshold and rated-power limit.
- Hydrogen production, water consumption, and oxygen co-production.
- Capital expenditure (CAPEX), operating expenditure (OPEX), and discounted LCOH over a 20-year project horizon.
- Indicative lifecycle-emissions screening.

The hourly solar profile is synthetic and calibrated to an assumed annual PV yield of **1,850 kWh/kWp**. It is a modelling input, not measured weather data. The electrolyzer specific energy consumption is assumed to be **52 kWh/kg H₂**, and water consumption is assumed to be **11.25 L/kg H₂**.

## Methodology

### 1. Hourly energy modelling

An hourly PV generation profile is used to estimate the power available to the electrolyzer. The model applies the minimum-load and rated-capacity constraints, calculates accepted electricity, and accounts for curtailed PV energy.

### 2. Hydrogen and material balances

Annual hydrogen production is calculated from accepted electrolyzer electricity and specific energy consumption. The model also estimates water demand and oxygen co-production using the stated stoichiometric and operating assumptions.

### 3. Techno-economic assessment

The project estimates system CAPEX, annual OPEX, hydrogen output, and discounted LCOH. Six representative configurations are compared, followed by a wider PV/electrolyzer capacity grid.

### 4. Machine-learning surrogate

A dataset of 700 sampled parameter combinations is generated from the engineering model. Linear Regression is used as a baseline and Random Forest Regression as the nonlinear surrogate. The data are split into 80% training and 20% testing, with five-fold cross-validation on the training set.

The model predicts the engineering model's LCOH; it does not independently validate the physical system or replace site-specific engineering data.

### 5. Environmental assessment

The report provides an indicative lifecycle-emissions assessment and evaluates water demand. The environmental results are screening estimates and depend on the system boundary and emission-factor assumptions.

## Key results

### Lowest-LCOH configuration in the tested grid

| Metric | Result |
|---|---:|
| PV capacity | 14.0 MWp |
| Electrolyzer capacity | 7.5 MW |
| Annual hydrogen production | 452.9 tonnes/year |
| Initial CAPEX | ₹1,192.5 million |
| Annual OPEX | ₹26.83 million |
| Calculated LCOH | ₹350.9/kg H₂ |

This is the lowest-LCOH point in the tested capacity grid, not proof of a global optimum outside the investigated range.

### Base-case configuration

| Metric | Result |
|---|---:|
| PV capacity | 10 MWp |
| Electrolyzer capacity | 5 MW |
| Annual hydrogen production | 311.0 tonnes/year |
| Capacity factor | 36.9% |
| PV curtailment | 12.6% |
| Annual water demand | Approximately 3,498 m³ |
| Calculated LCOH | ₹352.0/kg H₂ |

### Random Forest surrogate performance

| Metric | Test result |
|---|---:|
| R² | 0.777 |
| MAE | ₹35.5/kg H₂ |
| RMSE | ₹47.7/kg H₂ |

The Random Forest improves on the linear baseline in reproducing the engineering-model outputs. These scores represent surrogate-model agreement with generated data, not validation against measured plant performance.

## Repository contents

The repository includes the project report, calculation workbook with optimization, course project work plan, and final presentation. Open the files listed in the repository to access the detailed calculations, assumptions, figures, and discussion.

- **Project report:** `HME PROJECT REPORT(B23CH1007).pdf`
- **Calculation and optimization workbook:** Green Hydrogen workbook (Excel file in this repository)
- **Project work plan:** `Green_Hydrogen_Course_Project_Work_Plan.pdf` (if retained under this filename)
- **Presentation:** `HME_Presentation_Final.pdf`

If filenames are changed on GitHub, update this list to match the exact filenames.

## Tools and methods

- Python for numerical modelling and data analysis
- Excel for engineering calculations and scenario comparison
- Linear Regression and Random Forest Regression
- Hourly energy-balance modelling
- Techno-economic analysis and discounted LCOH calculation
- PV/electrolyzer capacity-grid optimization

## Limitations

The findings are screening-level results rather than a commercial feasibility study. Key limitations include:

- Synthetic hourly solar data rather than measured or validated site-specific weather data.
- Constant electrolyzer specific energy consumption.
- Simplified start-up, ramping, turndown, and degradation behaviour.
- Simplified cost and environmental inventories.
- No battery storage or grid backup.
- No independent validation against measured plant data.

The reported lowest LCOH is limited to the tested grid and assumptions. Before investment decisions, the model should be updated with site-specific hourly weather, current vendor quotations, realistic electrolyzer performance and degradation, and a fuller lifecycle inventory.

## Future scope

- Replace the synthetic solar profile with validated hourly weather data for a selected Jodhpur site.
- Include load-dependent electrolyzer efficiency, start-up energy, ramping, and degradation.
- Evaluate battery storage and hybrid renewable configurations.
- Improve CAPEX/OPEX estimates using current vendor quotations.
- Expand lifecycle assessment to include equipment manufacture, replacement, water treatment, recycling, and hydrogen leakage.
- Validate the ML surrogate using independent simulation cases or measured plant data.
- Extend the optimization to consider LCOH, hydrogen output, curtailment, water use, and emissions together.

## Author

**Aryan Prasad**  
B.Tech, Chemical Engineering  
Indian Institute of Technology Jodhpur

---

*This repository documents an academic course project. Results are based on stated modelling assumptions and should not be interpreted as a vendor quotation or bankable project feasibility assessment.*
