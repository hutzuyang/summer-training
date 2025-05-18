# week5-openmp

This project implements **OpenMP parallel computing** for **matrix operations** on CPU. The primary objective is to perform the following iterative computation on two 1000 × 1000 matrices `A` and `B`:

\[ A_{k+1} = (A_k + B_k) (A_k - B_k) \]
\[ B_{k+1} = A_{k+1} + B_k \]

The program utilizes **OpenMP directives** to parallelize computations and compares execution time with different numbers of threads.

### **Key Features:**
1. **Parsing matrix files (`A.txt` and `B.txt`) as input**.
2. **Using OpenMP to perform parallel matrix computation**.
3. **Optimizing performance with multiple CPU threads**.
4. **Writing results to output files (`A_openmp.txt` and `B_openmp.txt`)**.

## 📄 Input Format

The program requires two input files (`A.txt`, `B.txt`), each containing a **1000 × 1000 matrix** stored in a **1D vector format**.

📄 **Example A.txt / B.txt**
```
1.2 3.4 5.6 ...
7.8 9.1 2.3 ...
...
```

## 📄 Output Format

The program generates two output files after performing the operations for 5 iterations:
- **A_openmp.txt** - Final matrix A after OpenMP computation.
- **B_openmp.txt** - Final matrix B after OpenMP computation.

📄 **Example A_openmp.txt / B_openmp.txt**
```
2.5 6.8 10.2 ...
15.6 18.2 20.9 ...
...
```

## 🧰 Project Structure

```
📂 week5-openmp/
│── 📂 src/
│   ├── main.cpp  
│── 📄 A.txt  
│── 📄 B.txt  
│── 📄 A_openmp.txt  
│── 📄 B_openmp.txt   
│── 🔧 Makefile  
│── 📜 README.md  
│── 📜 .gitignore  
```

## 🔹 **OpenMP Implementation Flow**

### **1. Read Input Files**
- Reads `A.txt` and `B.txt` to extract matrix values.
- Stores them as **1D vectors**.

### **2. Initialize OpenMP Execution**
- Sets **number of threads (`omp_set_num_threads`)**.
- Allocates memory for temporary vectors.

### **3. Parallel Execution**
- Uses `#pragma omp parallel for` to parallelize computations.
- Implements **multi-threaded loop optimizations**.

### **4. Write Output Files**
- Saves the final results in `A_openmp.txt` and `B_openmp.txt`.

## ⚡ **Example Execution**

```bash
make                # Compile the program
make run           # Run the execution
make clean         # Remove temporary files
```
