# week3-plot

This project parses **YAL format circuit placement files**, extracts **module positions and dimensions**, and generates **MATLAB scripts for visualization**.

### **Key Features:**
- **Parses `.yal` files to extract module information.**
- **Reads `.out` files for placement coordinates.**
- **Generates a `.m` MATLAB script for visualization.**
- **Plots circuit layout with labeled modules.**

## 📄 Input Format

The program requires the following input files:
- **`.yal`** - Defines circuit modules and dimensions.
- **`.out`** - Contains placement results (x, y, rotation).

📄 **Example `.yal` File**
```
MODULE M1 DIMENSIONS 100 200
MODULE M2 DIMENSIONS 150 100
...
```

📄 **Example `.out` File**
```
M1 50 60 0
M2 200 100 1
...
```

## 📄 Output Format

The program generates a MATLAB script:
- **`yal_parser.m`** - Plots circuit placement results.

📄 **Example `yal_parser.m`**
```matlab
axis equal;
hold on;
grid on;
fill([50 50 150 150 50], [60 260 260 60 60], 'c');
text(100, 160, 'M1');
...
```

## 🧰 Project Structure

```
📂 orientation-week3-plot/
│── 📂 src/  
│   ├── main.cpp  
│   ├── yal_parser.cpp  
│   ├── yal_parser.h  
│── 📄 ami49.yal   
│── 📄 ami49_1_10.out   
│── 📄 yal_parser.m  
│── 🖥️ yal_parser  
│── 🔧 Makefile  
│── 📜 README.md  
│── 📜 .gitignore  
```

## 🔹 **YAL Parsing & Plotting Flow**

### **1. Read YAL and OUT Files**
- Extracts **module names, dimensions, and positions**.

### **2. Parse Placement Results**
- Reads `.out` file and applies **rotation transformations**.

### **3. Generate MATLAB Script**
- Constructs MATLAB `fill()` and `text()` commands for visualization.

## ⚡ **Example Execution**

```bash
make
./yal_parser ami49.yal ami49_1_10.out yal_parser.m
```

## 🖼️ Generated Plots
Below are the generated plots from the `matlab` output: 

**ami49**  
![yal](https://github.com/user-attachments/assets/4a1ef2ba-c893-449f-b900-3164878cf7ce)  
