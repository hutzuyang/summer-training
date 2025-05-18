# week2-bst

This project implements a **Binary Search Tree (BST) for module placement** while utilizing **Simulated Annealing (SA) to optimize placement efficiency**. The primary objective is to achieve **optimized module placement within a fixed outline** by **minimizing Half-Perimeter Wire Length (HPWL)**.

### **Key Features:**
1. **Parsing input files for circuit module data**.
2. **BST-based module insertion with contour tracking**.
3. **Operations: Rotation, Deletion, Swap, and Placement Adjustments**.
4. **Simulated Annealing (SA) for optimal placement search**.
5. **Output files for visualization and validation**.

## 📄 Input Format

This project follows a specific **YAL-based input format**:
- **.yal** - Contains circuit modules and dimensions.

📄 **Example Input File**
```
MODULE bk1 DIMENSIONS 100 200
MODULE bk2 DIMENSIONS 150 100
...
```

## 📄 Output Format

After execution, the program generates **BST-based placement results**:
- **.m** - MATLAB script for visualization.

## 🧰 Project Structure

📂 orientation-week2-bst/  
│── 📂 src/ # (fm.cpp, fm.h, parser.cpp, parser.h, and main.cpp)  
│── 📂 obj/  
│── 📄 benchmark.yal  
│── 📄 benchmark.m  
│── 🖥️ BST  
│── 🔧 Makefile  
│── 📜 README.md  
│── 📜 .gitignore  

## 🔹 **BST Operations & SA Optimization**

### **1. BST-based Module Insertion**
- Parses `.yal` file to extract module dimensions.
- Constructs **BST hierarchy** based on predefined placement logic.

### **2. Module Operations**
- **Rotation**: Allows modules to be rotated **90 degrees**.
- **Deletion**: Removes a specific module from the BST.
- **Swap**: Exchanges two modules' positions in the BST.

### **3. Simulated Annealing (SA) Optimization**
- **Initial temperature-based placement exploration**.
- **Cooling schedule to refine the placement solution**.
- **Acceptance probability function to escape local optima**.

## ⚡ **Example Execution**

```bash
./BST input.yal output.m
```

## 🖼️ Generated Plots
Below are the generated plots from the `matlab` output: 

**init**  
![initial](https://github.com/user-attachments/assets/9fc6dba6-4e92-478f-8bbc-7dd48dccb0c2)  
**sa**  
![sa2](https://github.com/user-attachments/assets/11e01aec-11b2-4d90-bc43-764f43d55d6a)  
