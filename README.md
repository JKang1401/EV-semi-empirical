# Semi-empirical Aging Model for SOH prediction of EVs

## Project Overview
This repository documents a research project conducted during my internship at the **Center for Automotive Research (CAR)** at **The Ohio State University**, in collaboration with **Ford Motor Company**. The project focused on developing a semi-empirical model to predict the **State of Health (SOH)** of electric vehicle (EV) batteries, a critical component of Battery Management Systems (BMS). The goal was to estimate battery capacity fade over time to enable better durability assessment and operational safety for EVs.

Due to the proprietary nature of the collaboration, specific data and detailed model equations are not included in this repository. This README provides a high-level overview of the project’s objectives, methodology, and outcomes to showcase my contributions and technical skills.

## Problem Statement
Battery capacity in EVs degrades over time due to factors like calendar aging (time-based degradation) and cycling aging (degradation from charge-discharge cycles). Accurate SOH prediction is essential for:
- Estimating the operational range of EVs.
- Ensuring timely battery replacement for safety.
- Optimizing battery performance under varying conditions, such as temperature fluctuations.

The challenge was to create a model that balances physical accuracy with computational efficiency, using real-world driving and environmental data while accounting for confidentiality constraints.

## Methodology
The project developed a semi-empirical aging model that combines physics-based principles with empirical data to predict weekly capacity fade. Key aspects of the methodology include:

**1. Model Structure**: The model accounts for two types of capacity fade:
- Calendar Aging: Degradation over time, influenced by ambient temperature and State-of-Charge (SOC).
- Cycling Aging: Degradation due to Ampere-hour throughput during driving and charging cycles.

**2. Data Utilization**: The model was trained and tested using 10 years of simulated driving cycle data, discretized into weekly intervals, and temperature data reflecting seasonal and daily variations. (Specific datasets are proprietary and not shared.)

**3. Parameter Optimization**:
- Two optimization methods were compared: Gradient Descent (GD) and Particle Swarm Optimization (PSO).
- PSO was selected for its superior performance, achieving a lower Mean Absolute Percentage Error (MAPE) of approximately 0.2368 compared to GD’s 0.2836.
- Optimization was performed on a dataset of 274 customer profiles, split into 182 training and 92 test sets.

**4. Evaluation**: The model’s performance was assessed using MAPE for SOH predictions and Mean Squared Error (MSE) for comparing capacity fade predictions against a baseline model.

## Key Contributions
- Model Development: Designed a semi-empirical model that incorporates temperature variability and weekly data aggregation, improving prediction accuracy over the baseline model.
- Optimization: Implemented and compared GD and PSO, demonstrating PSO’s ability to better capture data fluctuations and seasonal trends.
- Error Analysis: Analyzed error patterns to identify relationships between prediction errors and variables like temperature, SOC, and Ampere-hour throughput, revealing insights for future model refinements.
- Collaboration: Worked closely with Ford and CAR researchers to align the model with industry needs while adhering to data confidentiality requirements.

## Results
- The proposed model outperformed the baseline model, with a significantly lower MSE distribution (concentrated between 0 and 5 compared to 5–15 for the baseline).
- Over 50% of test cases achieved a MAPE below 0.25, indicating robust SOH prediction accuracy.
- The model successfully captured seasonal trends and small fluctuations in capacity fade, making it suitable for real-world EV applications.
- Error analysis revealed that higher temperatures, lower SOC, and increased Ampere-hour throughput were associated with larger prediction errors, providing actionable insights for model improvement.

## Technical Skills
- Programming: Python for model development, optimization, and data analysis.
- Optimization Techniques: Gradient Descent, Particle Swarm Optimization.
- Battery Modeling: Semi-empirical modeling, calendar and cycling aging.
- Data Analysis: Error pattern analysis, statistical evaluation (MAPE, MSE).
- Tools: MATLAB/Simulink (for vehicle simulation, assumed based on CAR’s typical workflow), Python libraries (e.g., NumPy, SciPy for optimization).

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
