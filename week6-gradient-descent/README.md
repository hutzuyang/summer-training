# week6-gradient-descent

This project implements **gradient descent optimization** for **circuit placement** by minimizing:

\[ \min WL(x) + \lambda D(x) \]

where:
- **WL(x)** represents **wirelength** minimization (using Log-Sum-Exponential model).
- **D(x)** represents **density** minimization (using Electrostatic Force model).
- **λ (lambda)** is a tunable parameter balancing wirelength and density constraints.

### **Key Features:**
1. **Parsing circuit layout data from input files (`test.txt`).**
2. **Using gradient descent optimization for placement refinement.**
3. **Calculating gradients for wirelength and density functions.**
4. **Writing final placement results to output files (`output.dpx`).**

## 📄 Input Format

The program requires a single input file (`test.txt`) which describes the placement area, components, and netlist connectivity.

📄 **Example test.txt**
```
PlacementArea: 1000 1000
Component: C1 50 50
Component: C2 60 40
Net: N1 C1 C2
...
```

## 📄 Output Format

The program generates a placement result file:
- **output.dpx** - Final placement solution, visualized as a graphical plot.

📄 **Example output.dpx**
```
COLOR gray
SR 0 0 120 120
COLOR green
SRF 10 10 60 60
COLOR cyan
SRF 80 80 140 140
...
```

## 🧰 Project Structure

```
📂 week6-gradient-descent/  
│── 📂 src/  
│   ├── main.cpp  
│   ├── parser.h  
│   ├── parser.cpp  
│   ├── alg.ch  
│   ├── alg.cpp  
│── 📄 test.txt  
│── 📄 output.dpx  
│── 🔧 Makefile  
│── 📜 README.md  
│── 📜 .gitignore
```

## 🔹 **Gradient Descent Optimization Flow**

### **1. Read Input Files**
- Parses `test.txt` for **circuit components, placement area, and netlist data**.
- Initializes **component positions and connectivity**.

### **2. Compute Initial Wirelength and Density**
- **Wirelength Calculation**: Uses **Log-Sum-Exponential (LSE) model**.
- **Density Calculation**: Uses **Electrostatic Force model**.

### **3. Gradient Calculation & Update**
- Computes **gradients for WL and D**.
- Updates component positions iteratively **until convergence**.

### **4. Output Final Placement Results**
- Saves final placement in `output.dpx`.

## ⚡ **Example Execution**

```bash
make
./exe
./display.x out.dpx
```

## 🖼️ Generated Plots

Below are the generated plots from the `matlab` and `gnuplot` output:

  - init
  <img src="https://github.com/user-attachments/assets/2a62e3de-2c6b-42fa-9aaa-a3dbde8f64cd" width="50%" height="50%">  

  - out
  <img src="https://github.com/user-attachments/assets/1c68a53a-c719-418f-a94c-e21c7d1b59a9" width="50%" height="50%">  
