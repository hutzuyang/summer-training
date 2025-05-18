# week8-congestion-map

This project implements **Congestion Map generation** to evaluate the **routability of a circuit placement**. The process involves:
1. **Partitioning the placement region into uniform G-cells.**
2. **Using FLUTE to decompose multi-pin nets into 2-pin nets.**
3. **Calculating the demand and supply for each routing edge.**
4. **Identifying congested areas where demand exceeds supply.**
5. **Generating visual representations of congestion levels.**

### **Key Features:**
- **Parses placement files (`.aux`, `.nodes`, `.nets`, `.pl`, `.scl`, `.route`).**
- **Uses FLUTE to construct Rectilinear Steiner Minimum Trees (RSMT).**
- **Computes routing demand and supply for each G-cell.**
- **Identifies top 10% most congested G-cells.**
- **Outputs congestion maps as `.dpx` visualization files.**

## 📄 Input Format

The program takes the following input files:
- **.aux** - Entry point linking to other files.
- **.nodes** - Defines circuit components.
- **.nets** - Describes netlist connectivity.
- **.pl** - Specifies initial placement coordinates.
- **.scl** - Defines row placement structure.
- **.route** - Contains routing information (tile size, layers, spacing).

📄 **Example .route File**
```
Grid    100 100 6
MinWireWidth    1 1 1 1 1 1
MinWireSpacing  2 2 2 2 2 2
GridOrigin      0 0
TileSize        10 10
```

## 📄 Output Format

The program generates congestion visualization files:
- **`circuit_ver.dpx`** - Congestion map for vertical edges.
- **`circuit_hor.dpx`** - Congestion map for horizontal edges.
- **`circuit_w_ver.dpx`** - Wire visualization for vertical edges.
- **`circuit_w_hor.dpx`** - Wire visualization for horizontal edges.

📄 **Example circuit_ver.dpx**
```
COLOR pink
SRF 10 20 30 40
COLOR blue
SRF 50 60 70 80
...
```

## 🧰 Project Structure

```
📂 week8-congestion-map/
│── 📂 flute-3.1/  
│── 📂 obj/     
│── 📂 src/ 
│   ├── main.cpp  
│   ├── parser.cpp  
│   ├── alg.cpp  
│── 📄 circuit.aux  
│── 📄 circuit_ver.dpx  
│── 📄 circuit_hor.dpx  
│── 📄 circuit_w_ver.dpx  
│── 📄 circuit_w_hor.dpx  
│── 🔧 Makefile  
│── 📜 README.md  
│── 📜 .gitignore  
```

## 🔹 **Congestion Map Computation Flow**

### **1. Read Input Files**
- Parses `.aux`, `.nodes`, `.nets`, `.pl`, `.scl`, `.route` files.

### **2. Generate Steiner Trees using FLUTE**
- Uses **FLUTE** to decompose **multi-pin nets into 2-pin nets**.

### **3. Compute Routing Demand & Supply**
- **Demand Calculation**: Counts wires crossing each routing edge.
- **Supply Calculation**: Determined by layer widths and spacing constraints.

### **4. Compute Overflow and Identify Congested Areas**
- **Overflow = Demand - Supply**.
- Marks **top 10% most congested G-cells**.

### **5. Generate Congestion Map Visualizations**
- Saves congestion levels in `.dpx` format for visualization.

## ⚡ **Example Execution**

```bash
make
./FLUTE_test circuit.aux circuit_ver.dpx circuit_hor.dpx circuit_w_ver.dpx circuit_w_hor.dpx
./display.x circuit.dpx
```

## 🖼️ Generated Plots

Below are the generated plots from the `display.x` output:

  - congestion map ver
  <img src="https://github.com/user-attachments/assets/a41c8f5a-4bdb-49d0-adac-1551f593663e" width="50%" height="50%">  

  - congestion map hor
  <img src="https://github.com/user-attachments/assets/559662b9-697c-4dd3-acac-8f1e86037e58" width="50%" height="50%">  

  - wire ver
  <img src="https://github.com/user-attachments/assets/3b112b97-4335-4b50-97bc-4221a25f37a3" width="50%" height="50%">  

  - wire hor
  <img src="https://github.com/user-attachments/assets/a4c6aeec-3714-4fa7-8638-2a28244f76ed" width="50%" height="50%">  
