# yield-curve-short-rate-models-vasicek-cir
# Short-Rate Modeling in Python — Vasicek, CIR, Ho-Lee, and Hull-White

Pricing and simulating interest-rate instruments using classical **short-rate** models:
**Vasicek**, **Cox–Ingersoll–Ross (CIR)**, **Ho–Lee**, and **Hull–White**. Includes
calibration examples and pricing notebooks.

---

## 🧭 What’s Inside

- `Vasicek_and_Cox_Ingersoll_Ross_Models_in_Python.ipynb` — Simulation & pricing with Vasicek and CIR
- `HoLee_Model_in_Python.ipynb` — Ho–Lee model walkthrough
- `HullWhite_Model_in_Python.ipynb` — One-factor Hull–White pricing & simulation
- `Bond.py` — Convenience routines for discount factors / zero-curve utilities
- `Zeros.csv` — Zero-coupon curve inputs
- `Strips.csv` — STRIPS data for curve construction
- `README.md` — You’re here

> Original base: a public repo demonstrating short-rate models; this version reorganizes
> instructions and adds clearer calibration steps.

---

## 📚 Models Covered

- **Vasicek (1977)**: Mean-reverting Gaussian short rate  
  \( dr_t = a(b - r_t)\,dt + \sigma\,dW_t \)

- **CIR (1985)**: Mean-reverting with state-dependent volatility  
  \( dr_t = a(b - r_t)\,dt + \sigma \sqrt{r_t}\,dW_t \)

- **Ho–Lee (1986)**: No-arbitrage with time-dependent drift  
  \( dr_t = \theta(t)\,dt + \sigma\,dW_t \)

- **Hull–White (1990)**: Extended Vasicek with time-varying mean  
  \( dr_t = [\theta(t) - a r_t]\,dt + \sigma\,dW_t \)

---

## ⚙️ Setup

```bash
python -m venv .venv
source .venv/bin/activate   # (Windows) .venv\Scripts\activate
pip install -r requirements.txt  # if provided; otherwise install numpy pandas scipy jupyter matplotlib

Launch notebooks:
jupyter notebook


🧪 How to Use
Load a curve: Read Zeros.csv or Strips.csv and build discount factors.

Choose a model: Vasicek / CIR / Ho–Lee / Hull–White.

Calibrate: Fit parameters to the input curve (and/or historical rates).

Simulate paths: Generate short-rate paths; compute bond/option prices.

Validate: Compare model implied rates vs. market; check errors.

📝 Notes
Ensure positive rates with CIR (non-negativity by construction).

Hull–White fits term-structure better via time-dependent mean 
𝜃
(
𝑡
)
θ(t).

Use historical rate data for robust parameter estimates; bootstrap for initial curves.

📄 License & Attribution
This repo reorganizes publicly shared notebooks and files for clarity.
Please retain original author credits where applicable.

yaml
Copy code

---

## 2) Option Pricing (Black-Scholes, Binomial, Monte Carlo)

**Proposed repo name:** `option-pricing-streamlit-bsm-binomial-montecarlo`

```markdown
# Option Pricing Models — Black–Scholes, Binomial Tree, Monte Carlo (Streamlit App)

Interactive **Streamlit** web app to price European options using:
1) **Black–Scholes**, 2) **Monte Carlo**, 3) **Binomial Tree**.

Fetches price data, lets you set parameters, and visualizes outcomes.

---

## 🔧 Features

- European call/put pricing with **Black–Scholes**
- **Monte Carlo** path simulation and payoff estimation
- **Binomial Tree** (CRR) valuation
- Parameter inputs: Strike, Risk-free rate, Volatility (σ), Exercise date
- Data fetch with `pandas-datareader` / caching via `requests-cache`
- Streamlit UI with quick scenario testing

---

## 📂 Structure

- `option_pricing/` — Model implementations (BSM / MC / Binomial)
- `streamlit_app.py` — Main web app
- `demo/` — GIFs of the app
- `Requirements.txt` — Python deps
- `Dockerfile` — Containerized run

---

## 🚀 Run Locally

```bash
python -m venv .venv
source .venv/bin/activate    # (Windows) .venv\Scripts\activate
pip install -r Requirements.txt
streamlit run streamlit_app.py --server.port 8080
# open http://localhost:8080
🐳 Run with Docker
bash
Copy code
docker build -t options-pricing:latest .
docker run -p 8080:8080 options-pricing:latest
# open http://0.0.0.0:8080
