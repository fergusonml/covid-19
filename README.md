## COVID-19 Modeling and Prediction using SIR Model
by Matthew L Ferguson

Associate Professor of Physics, Boise State University

updated: 20200328

SIR and SEIR in python. Working on Bayesian parameter fitting and sampling of the parameter posterior distribution using the emcee Markov Chain Monte Carlo package and CSSE data with lmfit. https://lmfit.github.io/lmfit-py/fitting.html#minimizer-emcee-calculating-the-posterior-probability-distribution-of-parameters

Parameters:
#important part
Ro = 5.1
Tr = 12.9
Ta = 1.

start = 0.
end = 365.

e = 0.0      # Initial Exposed
i = 10.0     # Initial Infectious
s = 1e5 - i  # Initial Susceptible
r = 0.0      # Initial Recovered
N = s + e + i + r  # Initial population

alpha = 1/Ta
beta = Ro/Tr/N   #COVID-19,14days,100k
gamma = 1/Tr

### SIR Model
https://en.wikipedia.org/wiki/Compartmental_models_in_epidemiology#The_SIR_model_without_vital_dynamics

$$
\frac{dS}{dt}= -\beta I S \\
\frac{dI}{dt}= \beta I S -\gamma I=(\beta S - \gamma) I\\
\frac{dR}{dt}= \gamma I \\
$$

![Image of SIR](SIR Model.png)

### SEIR Model
https://en.wikipedia.org/wiki/Compartmental_models_in_epidemiology#The_SEIR_model

$$
\frac{dS}{dt}= -\alpha I S \\
\frac{dE}{dt}= \beta I S -\alpha E\\
\frac{dI}{dt}= \alpha E -\gamma I\\
\frac{dR}{dt}= \gamma I \\
$$

![Image of SIR](SEIR Model.png)

### Q? How does Mitigation (like Social Distancing, School Closer and Total Shutdown) effect the solution to the SIR Model?
### A. ${\beta}$
https://en.wikipedia.org/wiki/Compartmental_models_in_epidemiology#The_SIR_model_without_vital_dynamics

$$
\frac{dS}{dt}= -\beta I S  \\
\frac{dI}{dt}= \beta I S -\gamma I=(\beta S - \gamma) I\\
\frac{dR}{dt}= \gamma I \\
$$

### Parameters of the model
$$
\beta=\frac{R_0}{N T_r}=\frac{5.1 ~\mathrm people}{12.9 ~\mathrm days}\\
\gamma=\frac{1}{T_r}=\frac{1}{12.9  ~\mathrm days}\approx 0.08 ~\mathrm{ / day}\\
$$

![SIR Model Series](SIR Model Series.png)

![Mitigation parameter table](Mitigation parameter table.png)

# The Timing of the COVID-19 Peak in the SIR Model
Matthew L Ferguson,
Associate Professor of Physics, 
Boise State University

with

Bruce N Miller,
Emeritus Professor of Physics, 
Texas Christian University

March 26, 2020

https://en.wikipedia.org/wiki/Compartmental_models_in_epidemiology#Exact_analytical_solutions_to_the_SIR_model
Following notation from the above linked page.

At the peak:
$ \frac{dI}{dt}=\left(R_0 \frac{S}{N}-1\right)\gamma I=0$
therefore
$S_{max}=\frac{N}{R_0}$
is the value of $S$ at maximum.

Following the analytical solution of Harko et al.(2014)

$t_{max}=\int_{u_{max}}^1\frac{N}{\gamma R_0 s \left(N-R(0)+\frac{N}{R_0} ln(s) - S(0) s\right)}ds$ where $u_{max}=\frac{S_{max}}{S(0)}=\frac{N}{R_0 S(0)}$

$I_{max}=I(0)+S(0)-\frac{1+log(R_0 S(0))}{R_0}$

 Harko, Tiberiu; Lobo, Francisco S. N.; Mak, M. K. (2014). "Exact analytical solutions of the Susceptible-Infected-Recovered (SIR) epidemic model and of the SIR model with equal death and birth rates". Applied Mathematics and Computation. 236: 184–194. arXiv:1403.2160. Bibcode:2014arXiv1403.2160H. doi:10.1016/j.amc.2014.03.030.
 
 ![ID SIR Imax](ID SIR Imax.png)
