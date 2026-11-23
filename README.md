# Green-Hydrogen-Techno-Economic-Optimization-and-ML-Modeling

## Techno-Economic Optimization and Environmental Assessment of a Solar-Powered Pressurised Alkaline Electrolyser System

**Study location:** Jodhpur, Rajasthan, India\
**Project:** Hydrogen and Methanol Economy --- Course Project, IIT
Jodhpur\
**Model run:** 26 October 2026

## Project Overview

This project develops a calculation-based techno-economic model for a
standalone solar photovoltaic (PV) system supplying a pressurised
alkaline water electrolyser for green hydrogen production in Jodhpur,
Rajasthan.

The system is modelled without battery storage or grid backup. The
electrolyser follows the available solar power, subject to a 15%
minimum-load threshold and its rated power limit. The study evaluates PV
and electrolyser sizing together because the selected capacities affect
electrolyser utilisation, solar-energy curtailment, hydrogen output and
the levelized cost of hydrogen (LCOH).

The workflow combines hourly energy modelling, hydrogen and utility
balances, discounted cash-flow analysis, sensitivity analysis,
environmental screening and machine-learning-based approximation of the
engineering model.

## Project Objectives

-   Model hourly PV electricity generation and the power accepted by the
    electrolyser.
-   Compare PV and electrolyser capacity combinations.
-   Estimate annual hydrogen production, water demand, oxygen
    co-production, operating hours and curtailment.
-   Calculate CAPEX, annual OPEX and discounted LCOH over a 20-year
    project life.
-   Examine the sensitivity of LCOH to key technical and economic
    assumptions.
-   Estimate indicative greenhouse-gas emissions while documenting the
    limitations of the environmental boundary.
-   Train and evaluate Linear Regression and Random Forest models as
    surrogate predictors of engineering-model LCOH.

## System Configuration and Modelling Approach

The model represents a standalone PV--pressurised alkaline electrolyser
system.

1.  **Solar PV model:** An 8,760-hour synthetic PV generation profile is
    constructed and calibrated to an annual specific yield of 1,850
    kWh/kWp.
2.  **Power-management logic:** Electrolyser input is zero below 15% of
    rated power, follows available PV power between the minimum-load and
    rated-power limits, and is capped at rated power. Excess PV energy
    is treated as curtailed.
3.  **Hydrogen and utility balances:** Hydrogen production is calculated
    using a system specific energy consumption (SEC) of 52 kWh/kg H₂.
    Water use is estimated at 11.25 L/kg H₂, and oxygen co-production at
    approximately 8 kg O₂/kg H₂.
4.  **Economic model:** CAPEX, annual OPEX, water costs and a year-10
    stack replacement allowance are included in a discounted 20-year
    LCOH calculation.
5.  **Scenario and capacity-grid analysis:** Multiple PV/electrolyser
    configurations are compared, followed by a capacity-grid search to
    identify the lowest calculated LCOH within the tested range.
6.  **Machine-learning surrogate:** Linear Regression is used as a
    baseline and Random Forest as a nonlinear surrogate. Models are
    evaluated using a held-out test set and five-fold cross-validation.

## Key Results

### Base-case configuration

  Parameter                                                         Result
  -------------------------------------- ---------------------------------
  PV capacity                                                       10 MWp
  Electrolyser capacity                                               5 MW
  Annual hydrogen production                             311.0 tonnes/year
  Annual PV generation                                      18.50 GWh/year
  Electricity accepted by electrolyser                      16.17 GWh/year
  Curtailed PV electricity                                   2.33 GWh/year
  Electrolyser capacity factor                                       36.9%
  Annual water requirement                     Approximately 3,498 m³/year
  Annual oxygen co-production              Approximately 2,488 tonnes/year
  Initial CAPEX                                          INR 825.0 million
  Annual OPEX                                            INR 18.35 million
  Calculated LCOH                            Approximately INR 352.0/kg H₂

### Lowest-LCOH configuration in the tested capacity grid

  Parameter                                             Result
  ---------------------------- -------------------------------
  PV capacity                                         14.0 MWp
  Electrolyser capacity                                 7.5 MW
  Annual hydrogen production                 452.9 tonnes/year
  Initial CAPEX                            INR 1,192.5 million
  Annual OPEX                                INR 26.83 million
  Calculated LCOH                Approximately INR 350.9/kg H₂

The capacity-grid result is the lowest calculated LCOH among the
configurations tested; it should not be interpreted as a global optimum
beyond the tested range. The difference between the base-case and
lowest-grid LCOH is small under the stated assumptions.

### Machine-learning results

The Random Forest surrogate achieved the following held-out test
performance when predicting LCOH generated by the engineering model:

  Model                 Test R²      Test MAE     Test RMSE
  ------------------- --------- ------------- -------------
  Linear Regression       0.221   INR 64.7/kg   INR 89.2/kg
  Random Forest           0.777   INR 35.5/kg   INR 47.7/kg

Random Forest performed better than the linear baseline on the generated
dataset. These metrics indicate how closely the surrogate reproduces the
engineering model; they do **not** represent validation against measured
industrial-plant data.

## Sensitivity and Environmental Assessment

The sensitivity analysis examines the effects of PV CAPEX, electrolyser
CAPEX, annual solar yield, specific energy consumption and discount rate
on LCOH. The results show that equipment costs, financing assumptions
and electrolyser energy consumption can materially influence the
calculated hydrogen cost.

For the base case, the report estimates an indicative footprint of
approximately **3.28 kg CO₂e/kg H₂**. This is a screening estimate based
on simplified emissions factors, not a complete life-cycle assessment.
The base-case water requirement is approximately 3,498 m³/year, making
water sourcing and treatment important considerations for a Jodhpur
application.

## Important Modelling Assumptions and Limitations

-   The hourly solar profile is synthetic, not measured hourly weather
    or irradiance data.
-   Annual PV yield is assumed to be 1,850 kWh/kWp.
-   Electrolyser SEC is held constant at 52 kWh/kg H₂.
-   The electrolyser minimum-load threshold is 15% of rated capacity.
-   The model assumes no battery storage and no grid backup.
-   The economic model uses screening-level equipment costs and a
    20-year project life.
-   Detailed start-up and ramp-rate effects, temperature-dependent
    efficiency, degradation, taxes, subsidies and financing fees are not
    fully represented.
-   The environmental estimate is not a complete life-cycle assessment.
-   ML performance is assessed against model-generated targets, not real
    plant measurements.

Accordingly, results should be interpreted as a comparative course-level
screening study, not as a bankable project estimate or vendor quotation.

## Future Scope

-   Replace the synthetic PV profile with site-specific hourly solar
    data for Jodhpur.
-   Incorporate load-dependent electrolyser efficiency, start-up losses,
    ramping and stack degradation.
-   Use current vendor quotations and more detailed balance-of-plant
    cost estimates.
-   Investigate battery storage, hybrid renewable supply and
    grid-connected configurations.
-   Expand the environmental assessment into a detailed life-cycle
    inventory.
-   Test surrogate predictions against additional engineering-model
    cases and, where available, measured plant data.
-   Extend the optimisation to multiple objectives such as LCOH,
    hydrogen output, curtailment, water use and emissions.

## Technologies and Skills

Python · NumPy · Pandas · Matplotlib · Scikit-learn · Linear Regression
· Random Forest · Techno-Economic Modelling · Renewable Energy Systems ·
Alkaline Water Electrolysis · Sensitivity Analysis · Optimisation ·
Environmental Assessment

------------------------------------------------------------------------

**Academic context:** Hydrogen and Methanol Economy course project,
Indian Institute of Technology Jodhpur.
