# econ3916-lab14-ols-diagnostics
OLS Diagnostics: When the Standard Error Is Lying
Objective
I used simulated and California Housing data to see how unequal error spread, unusual observations, and omitted variables affect an OLS regression.
Methodology
- I fitted the same simulated regression with classical and HC3 robust standard errors, then checked interval coverage across 400 samples.
- I read four residual plots alongside Breusch-Pagan and Jarque-Bera tests.
- I used Cook’s distance to find influential observations and compared regressions with and without them.
- I fitted a California Housing regression and wrote hc3_se() to get the HC3 standard error for a chosen coefficient and dataset.
- I compared standard errors after removing districts recorded at the value ceiling and completed a simulation with an omitted confounder.
Key findings
- Both methods gave the same simulated slope, 2.0147. The classical standard error was 0.0264, and the HC3 standard error was 0.0290.
- The classical 95% interval covered the true slope in 91.8% of samples, with a Monte Carlo standard error of 1.4%. The HC3 interval covered it in 93.5%, with a Monte Carlo standard error of 1.2%.
- Removing one row out of 600 moved the slope by 0.58 of its standard error and lowered the standard error by 33%.
- In the California Housing regression, the HC3 standard error for AveRooms was 5.02 times the classical one. My function returned 0.0121 with all districts and 0.0082 without the 965 districts at the 5.0 ceiling.
- The five most influential districts accounted for 92% of the total Cook’s distance.
- In my challenge simulation, the x-only regression estimated 2.476 even though the true effect was 1.500. Its diagnostic checks passed, so they did not reveal the omitted confounder.
