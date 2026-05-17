
# ⚛️ Quantum-Enabled SQL Query Optimizer

> A SQL query analysis engine that bridges classical query optimization and quantum computing — built with Python, Streamlit, and QAOA-inspired logic.

---

## 🧠 What It Does

Most databases treat all SQL queries the same way at the parser level. This project doesn't.

The **Quantum-Enabled Query Optimizer** analyzes incoming SQL queries, scores their structural complexity, and prepares them for quantum-assisted execution planning — simulating what next-generation database engines (like Snowflake's future quantum backends) may do.

It answers two questions:
- *How complex is this query, really?* (beyond just counting lines)
- *How many qubits would a quantum engine need to optimize it?*

---

## 🚀 Live Demo

> 🖥️ **Dashboard shows:** SQL input box → real-time complexity score → feature breakdown (JOINs, subqueries, aggregations detected) → normalized quantum state vector → estimated qubit count.


---

## ✨ Features

| Feature | Description |
|---|---|
| **Query Classification** | Detects *Simple* vs *Complex* queries automatically |
| **Complexity Scoring** | Numerical score based on structural features of the SQL |
| **Feature Extraction** | Identifies JOINs, subqueries, aggregations, GROUP BY, HAVING, and window functions |
| **Quantum State Vector** | Normalizes features into a quantum-ready state vector using NumPy |
| **Qubit Estimation** | Predicts approximate qubits needed for quantum computation via QAOA |
| **Real-Time Dashboard** | Clean dark-themed Streamlit UI with live results |

---

## 🏗️ Architecture

```
SQL Query Input
      │
      ▼
┌─────────────────────┐
│   sqlparse Parser   │  ← tokenizes and structures the raw SQL
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│  Feature Extractor  │  ← detects JOINs, subqueries, aggregations, etc.
└────────┬────────────┘
         │
      ┌──┴──────────────────────┐
      ▼                         ▼
┌──────────────┐     ┌──────────────────────┐
│  Complexity  │     │   Quantum Prep Stage  │
│   Scorer     │     │  (NumPy normalisation │
│              │     │   → state vector)     │
└──────┬───────┘     └──────────┬───────────┘
       │                        │
       ▼                        ▼
┌─────────────────────────────────────┐
│         Streamlit Dashboard         │
│  Score · Class · Qubits · Vector    │
└─────────────────────────────────────┘
```

---

## 🧩 Tech Stack

| Layer | Technology |
|---|---|
| Language | Python 3.10+ |
| UI | Streamlit |
| SQL Parsing | sqlparse |
| Quantum Logic | NumPy (vector normalisation) · QAOA (Qiskit — `QAOA.ipynb`) |
| Database | SQLite |
| Version Control | Git / GitHub |

---

## ⚙️ Getting Started

### Prerequisites
- Python 3.10+
- pip

### Installation

```bash
# 1. Clone the repo
git clone https://github.com/pranjalpundeer/Quantum-Enabled-Query-Optimizer.git
cd Quantum-Enabled-Query-Optimizer

# 2. Create a virtual environment (recommended)
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run the app
streamlit run app.py
```

The app opens at `http://localhost:8501` automatically.

---

## 🔬 Sample Queries to Try

```sql
-- Simple → low complexity score, few qubits
SELECT name, salary FROM employees WHERE department = 'Engineering';

-- Complex → high complexity score, more qubits needed
SELECT d.name, AVG(e.salary), COUNT(*) 
FROM employees e
JOIN departments d ON e.dept_id = d.id
WHERE e.salary > (SELECT AVG(salary) FROM employees)
GROUP BY d.name
HAVING COUNT(*) > 5
ORDER BY AVG(e.salary) DESC;
```

---

## 📁 Project Structure

```
Quantum-Enabled-Query-Optimizer/
├── app.py                    # Main Streamlit application
├── quantum_optimizer.py      # Core feature extraction + quantum prep logic
├── QAOA.ipynb                # Jupyter notebook: QAOA circuit experiments
├── database/                 # Sample SQLite databases for testing
├── templates/                # HTML templates (if any)
├── requirements.txt          # Python dependencies
└── README.md
```

---

## 🌱 What I Learned

- How SQL parsers tokenize and represent query structure
- Translating discrete query features into continuous normalized vectors
- QAOA (Quantum Approximate Optimization Algorithm) fundamentals and qubit estimation
- Building interactive data tools with Streamlit
- Bridging classical database concepts with quantum computing theory

---

## 🔭 Future Improvements

- [ ] Integrate with a real Snowflake or PostgreSQL connection to benchmark actual vs predicted optimization
- [ ] Add query rewriting suggestions (e.g., "Replace subquery with JOIN for better performance")
- [ ] Connect to IBM Quantum Experience or Qiskit Runtime for actual quantum execution
- [ ] Support for multiple SQL dialects (MySQL, PostgreSQL, Snowflake SQL)

---

## 👤 Author

**Pranjal Pundeer**
- GitHub: [@pranjalpundeer](https://github.com/pranjalpundeer)
- Email: pranjalpundeer40@gmail.com

---

> ⭐ If you find this project interesting, consider giving it a star — it helps others discover it!
