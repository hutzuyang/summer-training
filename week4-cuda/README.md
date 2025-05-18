# week4-cuda

This project implements **CUDA parallel computing** for **matrix operations** to demonstrate GPU acceleration. The primary objective is to perform the following iterative computation on two 1000 × 1000 matrices `A` and `B`:

\[ A_{k+1} = (A_k + B_k) (A_k - B_k) \]
\[ B_{k+1} = A_{k+1} + B_k \]

The program includes both **CPU and GPU implementations** and compares their execution times.

### **Key Features:**
1. **Parsing matrix files (`A.txt` and `B.txt`) as input**.
2. **Using CUDA to perform parallel matrix computation**.
3. **Comparing CPU and GPU execution times**.
4. **Writing results to output files (`A_cuda.txt` and `B_cuda.txt`)**.

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
- **A_cuda.txt** - Final matrix A after CUDA computation.
- **B_cuda.txt** - Final matrix B after CUDA computation.

📄 **Example A_cuda.txt / B_cuda.txt**
```
2.5 6.8 10.2 ...
15.6 18.2 20.9 ...
...
```

## 🧰 Project Structure
```
📂 week4-cuda/  
│── 📂 include/  
│   ├── cuda_kernel.cuh  
│── 📂 source/  
│   ├── cuda_kernel.cu  
│   ├── main.cpp  
│── 📄 A.txt  
│── 📄 B.txt  
│── 📄 A_cuda.txt  
│── 📄 B_cuda.txt  
│── 📄 CUDA_Runtime.txt  
│── 🔧 Makefile  
│── 📜 README.md  
│── 📜 .gitignore
```

## 🔹 **CUDA Implementation Flow**

### **1. Read Input Files**
- Reads `A.txt` and `B.txt` to extract matrix values.
- Stores them as **1D vectors**.

### **2. Initialize CUDA Execution**
- Allocates GPU memory (`cudaMalloc`).
- Copies matrix data from **CPU to GPU** (`cudaMemcpy`).

### **3. Kernel Execution**
- Launches **CUDA kernel functions** for matrix operations.
- Uses **parallel threads** for computation.

### **4. Copy Results Back to CPU**
- Retrieves computed matrices from **GPU to CPU** (`cudaMemcpy`).
- Frees GPU memory (`cudaFree`).

### **5. Write Output Files**
- Saves the final results in `A_cuda.txt` and `B_cuda.txt`.

## ⚡ **Example Execution**

```bash
make               # Compile the program
make run           # Run the execution
make clean         # Remove temporary files
```
