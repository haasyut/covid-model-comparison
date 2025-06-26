# Comparative Analysis of ARIMA and SEIR Models Using COVID-19 Data

This project explores two different modeling approaches for forecasting infectious disease trends: traditional statistical time series modeling and mechanistic epidemiological modeling.

We investigate the performance of the ARIMA model—a widely used tool for time series forecasting—alongside the SEIR model, a compartmental model that extends the classical SIR framework by introducing an Exposed (E) category to capture the incubation phase of infection.

The central question we examine is:

> Can the SEIR model, which incorporates epidemiological structure, offer a more accurate and interpretable fit for infectious disease transmission compared to the purely statistical ARIMA model?


## Installation and Setup

This project was developed using R.

###  R Packages Used

- **General Purpose:** `tidyverse`, `doFuture`
- **Modeling:** `pomp` for stochastic compartmental modeling
- **Time Series:** `forecast` (for `auto.arima()`)
- **Visualization:** `ggplot2`

## Data

This project uses real-world data on the spread of COVID-19 in the United States.

The dataset includes time series of confirmed cases, deaths, and recoveries recorded across different regions. In our exploratory analysis, we focused on three regions significantly affected during the early stages of the pandemic: **Washington State**, **California**, and **New York**.

For the modeling phase, we primarily used case data from **Washington State**, selecting approximately **1,500 daily observations** as input to the ARIMA and SEIR models.

### Source

The original data is derived from public COVID-19 surveillance sources and can be download from [here](https://covid19datahub.io/articles/data.html), and has been preprocessed into a smaller demo file:

- `data/data_demo.csv`: Sample of the full dataset, used for reproducibility and demonstration purposes.

> The COVID-19 pandemic began in early 2020. While vaccination campaigns have reduced severity in many regions, the virus continues to spread globally through emerging variants.

## Project Structure
```
├── data/
│ └── data_demo.csv
├── models/
│ └── simulate_sir_model.R # SIR model using pomp
├── notebooks/
│ └── report.Rmd # ARIMA vs SEIR analysis (R Markdown)
├── reports/
│ └── report.html # Rendered HTML report
├── .gitignore
└── README.md
```

## Results and Evaluation
Both ARIMA and SEIR models were applied to model the transmission dynamics of COVID-19 in Washington State.

- The **ARIMA model** effectively captured short-term fluctuations and subtle variations in the data. However, it underperformed during the 2022 outbreak peak, where nonlinear transmission dynamics became more pronounced.
- The **SEIR model**, grounded in epidemiological theory, naturally modeled the outbreak curve and showed stronger alignment with the actual peak timing. This suggests better interpretability in terms of population-level transmission behavior.

That said, the SEIR model still lagged behind ARIMA in overall fitting precision. Future improvement could involve incorporating additional compartments or features—such as death or hospitalization data—into the SEIR framework.

[Click to view the full report](./reports/report.html)

## Future Work

- Extend the SEIR model by adding more compartments (e.g., SEIRD or SEIRS)
- Explore model calibration techniques to improve fit precision
- Compare with other forecasting models such as Prophet or machine learning-based approaches
- Apply models to more granular or recent datasets with variant-specific trends

## Acknowledgments & References

- [COVID-19 Data Hub](https://covid19datahub.io/articles/data.html) — Original dataset and data dictionary
- [POMP Course Notes](https://kingaa.github.io/sbied/stochsim/notes.pdf)
- [Example Simulation Code](https://kingaa.github.io/sbied/stochsim/main.R)
- [SEIRS Modeling Study (Nature)](https://www.nature.com/articles/s41592-020-0856-2)
- [Project Example: POMP Final Project](https://ionides.github.io/531w22/final_project/project16/blinded.html)
- This project also benefited with [ChatGPT](https://chat.openai.com/)

