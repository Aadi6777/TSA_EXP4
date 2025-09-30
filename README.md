# Ex.No:04   FIT ARMA MODEL FOR TIME SERIES
# Reg no: 212224230001



### AIM:
To implement ARMA model in python.
### ALGORITHM:
1. Import necessary libraries.
2. Set up matplotlib settings for figure size.
3. Define an ARMA(1,1) process with coefficients ar1 and ma1, and generate a sample of 1000

data points using the ArmaProcess class. Plot the generated time series and set the title and x-
axis limits.

4. Display the autocorrelation and partial autocorrelation plots for the ARMA(1,1) process using
plot_acf and plot_pacf.
5. Define an ARMA(2,2) process with coefficients ar2 and ma2, and generate a sample of 10000

data points using the ArmaProcess class. Plot the generated time series and set the title and x-
axis limits.

6. Display the autocorrelation and partial autocorrelation plots for the ARMA(2,2) process using
plot_acf and plot_pacf.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.arima.model import ARIMA
from statsmodels.graphics.tsaplots import plot_acf, plot_pacf
from statsmodels.tsa.arima_process import ArmaProcess

# Load dataset
data = pd.read_csv("IMDB Top 250 Movies (1).csv")

# Make a time series: average rating per year
X = data.groupby("year")["rating"].mean()

plt.figure(figsize=(12,6))
plt.plot(X)
plt.title("Average IMDB Rating per Year")
plt.show()

# Plot ACF and PACF
plt.figure(figsize=(12,6))
plt.subplot(2,1,1)
plot_acf(X, lags=len(X)//4, ax=plt.gca())
plt.title("ACF of Ratings per Year")

plt.subplot(2,1,2)
plot_pacf(X, lags=len(X)//4, ax=plt.gca())
plt.title("PACF of Ratings per Year")
plt.tight_layout()
plt.show()


# Simulate ARMA(1,1)
phi_arma11 = arma11_model.params['ar.L1']
theta_arma11 = arma11_model.params['ma.L1']
ar1 = np.array([1, -phi_arma11])
ma1 = np.array([1, theta_arma11])
ARMA_1 = ArmaProcess(ar1, ma1).generate_sample(nsample=500)

plt.plot(ARMA_1)
plt.title("Simulated ARMA(1,1) Process")
plt.show()

plot_acf(ARMA_1)
plt.title("ARMA(1,1) ACF")
plt.show()
plot_pacf(ARMA_1)
plt.title("ARMA(1,1) PACF")
plt.show()


# Simulate ARMA(2,2)
phi1_arma22 = arma22_model.params['ar.L1']
phi2_arma22 = arma22_model.params['ar.L2']
theta1_arma22 = arma22_model.params['ma.L1']
theta2_arma22 = arma22_model.params['ma.L2']
ar2 = np.array([1, -phi1_arma22, -phi2_arma22])
ma2 = np.array([1, theta1_arma22, theta2_arma22])
ARMA_2 = ArmaProcess(ar2, ma2).generate_sample(nsample=500)

plt.plot(ARMA_2)
plt.title("Simulated ARMA(2,2) Process")
plt.show()

plot_acf(ARMA_2)
plt.title("ARMA(2,2) ACF")
plt.show()
plot_pacf(ARMA_2)
plt.title("ARMA(2,2) PACF")
plt.show()
```

OUTPUT:
Orginal:
<img width="1365" height="670" alt="495272390-859923e3-3b58-4b7c-9113-bfc78c0a3dd6" src="https://github.com/user-attachments/assets/dff8dafa-30d5-4013-a3d2-ddb2ab6d4d44" />

SIMULATED ARMA(1,1) PROCESS:
<img width="989" height="556" alt="495272455-c69f9234-e657-4360-91c7-2bed502e89c2" src="https://github.com/user-attachments/assets/e00f76c9-2cdd-4af3-8df7-d8abd1a7cb96" />



Partial Autocorrelation
<img width="1112" height="564" alt="495272555-bf34ee00-4430-4cfe-b3b1-a4806549f24d" src="https://github.com/user-attachments/assets/8d2ca00f-66ce-4e51-8db6-90aa1de289b1" />

Autocorrelation

<img width="939" height="568" alt="495272617-cb4f42f4-432d-4d3d-916a-a3f2532cf24e" src="https://github.com/user-attachments/assets/8127897f-167c-4243-8975-e5fab51a13d0" />


SIMULATED ARMA(2,2) PROCESS:
<img width="926" height="584" alt="495272686-dfefe8ff-d89b-4186-a2f1-8930c3161833" src="https://github.com/user-attachments/assets/8eb45cf2-9492-479c-b32d-b5cec9721865" />

Partial Autocorrelation
<img width="931" height="566" alt="495272768-5b182123-4cce-4cc7-a815-76940259b509" src="https://github.com/user-attachments/assets/14d50aff-0d1f-4c63-bcdc-327bd50f34fb" />



Autocorrelation
<img width="1014" height="566" alt="495272844-6278410c-27dc-4a9f-aaa7-40a71a258a9b" src="https://github.com/user-attachments/assets/77f72799-eb3f-4fab-827e-e8a871f9f98d" />

RESULT:
Thus, a python program is created to fir ARMA Model successfully.
