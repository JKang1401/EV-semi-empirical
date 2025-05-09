# Semi-empirical Aging Model for SOH prediction of EVs

## Project Overview
This repository documents a research project conducted during my internship at the **Center for Automotive Research (CAR)** at **The Ohio State University**, in collaboration with **Ford Motor Company**. The project focused on developing a semi-empirical model to predict the **State of Health (SOH)** of electric vehicle (EV) batteries, a critical component of Battery Management Systems (BMS). The goal was to estimate battery capacity fade over time to enable better durability assessment and operational safety for EVs.

Due to the proprietary nature of the collaboration, specific data and detailed model equations are not included in this repository. This README provides a high-level overview of the project’s objectives, methodology, and outcomes to showcase my contributions and technical skills.

## Problem Statement
Battery capacity in EVs degrades over time due to factors like calendar aging (time-based degradation) and cycling aging (degradation from charge-discharge cycles). Accurate SOH prediction is essential for:
- Estimating the operational range of EVs.
- Ensuring timely battery replacement for safety.
- Optimizing battery performance under varying conditions, such as temperature fluctuations.

The challenge was to create a model that balances physical accuracy with computational efficiency using real-world driving and environmental data while accounting for confidentiality constraints.

## Methodology
The project developed a semi-empirical aging model that combines physics-based principles with empirical data to predict weekly capacity fade. Key aspects of the methodology include:

### 1. Model Structure
The model accounts for two types of capacity fade:
- Calendar Aging: Reflects degradation over time since manufacturing.
- Cycling Aging: Reflects degradation due to Ampere-hour throughput during driving and charging cycles.

The model estimates capacity loss weekly using averaged temperature and State-of-Charge (SOC) data over 7-day periods to capture seasonality and fluctuations without excessive noise. Ambient temperature is a critical factor in overall battery performance and life.

### 2. Data Utilization
The model was trained and tested using 10 years of simulated Battery Management System (BMS) data from 274 customer profiles (182 training, 92 test sets), discretized into weekly intervals, and temperature data reflecting seasonal and daily variations. 


### 3. Parameter Optimization
- **Methods Compared**: Broyden-Fletcher-Goldfarb-Shanno (BFGS) optimization (via scipy.optimize.minimize) and Particle Swarm Optimization (PSO).
- **PSO Configuration**: 100 particles, 1000 iterations, cognitive parameter 0.3, social parameter 0.2, inertia parameter 0.9.
- **Results**: PSO outperformed BFGS, achieving a Mean Absolute Percentage Error (MAPE) of 0.2368 compared to BFGS’s 0.2836 (see Table 2.3 below).
- Calibration: Seven model parameters were optimized using training data, evaluated on 92 test sets.

### 4. Evaluation
- Metrics:
  - MAPE for SOH predictions.
  - Mean Squared Error (MSE) for comparing capacity fade predictions against the original model.
- Visualizations: Histograms and plots were used to analyze prediction accuracy and error patterns (see Figures 2.2, 2.4, 3.1, 4.1 below).

## Key Contributions
- **Model Development**: Designed a semi-empirical model that incorporates temperature variability and weekly data aggregation.
- **Optimization**: Implemented and compared BFGS and PSO, demonstrating PSO’s superior ability to capture data fluctuations and seasonal trends.
- **Error Analysis**: Identified relationships between prediction errors and variables (temperature, SOC, Ampere-hour throughput), revealing insights for future refinements.
- **Collaboration**: Worked closely with Ford and CAR researchers to align the model with industry needs while adhering to data confidentiality requirements.

## Results
- **Model Performance**:
  - The proposed model outperformed the baseline, with MSEs concentrated between **0 and 5** (vs. **5–15** for the baseline) (see Figure 3.1).
  - Over **50% of test cases** achieved a MAPE below **0.25**, indicating robust SOH prediction accuracy (see Figure 2.4).
  - The model captured seasonal trends and small fluctuations in capacity fade, suitable for real-world EV applications.
- **Example Prediction**:
  - For a randomly selected customer from the highest-density MAPE bin, the PSO-calibrated model accurately followed the original data’s fluctuations, including seasonal trends (see Figure 2.4).
- **Error Analysis**:
  - Higher temperatures, lower SOC, and increased Ampere-hour throughput correlated with larger errors (see Figure 4.1).
  - The new model’s error distribution in log scale showed a triangular shape, while the original model’s error vs. Ampere-hour throughput had a bow shape, suggesting distinct error patterns.
 
### Visual Results
Below are descriptions of key figures referenced in the project. *Note*: Due to confidentiality, placeholder images or descriptions are provided. Actual images would be included in a non-confidential setting.

- **Figure 2.1: Weekly Average Temperature**
  - *Description*: A line plot showing the weekly average temperature over 10 years, capturing seasonal trends (e.g., summer peaks, winter lows) and daily fluctuations with reduced noise compared to raw data.
  - *Purpose*: Demonstrates the effectiveness of weekly averaging for temperature data in the model.
  - *Placeholder*: [To be added as `figures/fig2_1_temperature.png` in the repository.]

- **Figure 2.2: MAPE Histogram for BFGS**
  - *Description*: A histogram of MAPE values for 92 test customers using BFGS, with 20 bins. The distribution peaks around 0.2836, indicating moderate prediction accuracy but limited ability to capture fluctuations.
  - *Placeholder*: [To be added as `figures/fig2_2_bfgs_mape_histogram.png`.]

- **Figure 2.4: MAPE Histogram and Prediction Plot for PSO**
  - *Description*: 
    - *Histogram*: Shows MAPE distribution for 92 test customers using PSO, with ~30% of cases below 0.225 and over 50% below 0.25, indicating strong prediction accuracy.
    - *Prediction Plot*: A line plot comparing predicted vs. actual capacity fade for a randomly selected customer, showing close alignment with seasonal trends and small fluctuations.
  - *Placeholder*: [To be added as `figures/fig2_4_pso_mape_and_prediction.png`.]

- **Figure 3.1: MSE Histogram for Model Comparison**
  - *Description*: A histogram comparing MSEs of capacity fade predictions for the new and original models. The new model’s MSEs are concentrated between 0 and 5, while the original model’s are between 5 and 15, demonstrating superior performance.
  - *Placeholder*: [To be added as `figures/fig3_1_mse_histogram.png`.]

- **Figure 4.1: Error Pattern Analysis**
  - *Description*: Scatter plots (normal and log scale) showing MSE vs. temperature, SOC, and Ampere-hour throughput for both models. Key observations:
    - Higher temperatures and lower SOC increase errors.
    - The new model’s log-scale errors form a triangular distribution.
    - The original model’s errors vs. Ampere-hour throughput form a bow shape.
  - *Placeholder*: [To be added as `figures/fig4_1_error_analysis.png`.]

### Parameter Comparison
| Method | Param1 | Param2 | Param3 | Param4 | Param5 | Param6 | Param7 | MAPE |
|--------|--------|--------|--------|--------|--------|--------|--------|------|
| BFGS   | -1746.41 | -137920 | 0.55 | -11600.92 | 11016.87 | 1.0 | 24644.41 | 0.2836 |
| PSO    | -3352.43 | -33422.41 | 0.58 | -5587.31 | 7397 | 0.999 | 27091.64 | 0.2368 |

*Table 2.3: Comparison of optimized parameters and MAPE for BFGS and PSO.*

## Technical Skills
- **Programming**: Python for model development, optimization, and data analysis.
- **Optimization Techniques**: BFGS (via `scipy.optimize.minimize`), Particle Swarm Optimization.
- **Battery Modeling**: Semi-empirical modeling, calendar and cycling aging.
- **Data Analysis**: Error pattern analysis, statistical evaluation (MAPE, MSE).
- **Tools**: MATLAB/Simulink (assumed for vehicle simulation), Python libraries (NumPy, SciPy for optimization, Matplotlib for visualization).

## Repository Contents
Due to confidentiality, this repository does not include:
- Proprietary datasets or specific equations.
- Detailed code implementations or parameter values.

Instead, it contains:
- This README, which summarizes the project.

## Acknowledgements
- **Center for Automotive Research, The Ohio State University** for providing research facilities and guidance.
- **Ford Motor Company** for collaboration and industry insights.
- Project advisors and team members for their support.

## References
- Cordoba-Arenas, A. (2013). Aging Propagation in Advanced Battery Systems: Preliminary Results.
- Naumann, M. (2018). Analysis and modeling of calendar aging of a commercial /graphite cell.
- Lin, S. (2008). Particle swarm optimization for parameter determination and feature selection of support vector machines.

##
*Note: This project is part of my portfolio to demonstrate my experience in battery modeling and optimization. For inquiries about the project or collaboration opportunities, please contact me via edenwldms@gmail.com*
