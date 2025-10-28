# SRAM-Cell-Design-Cadence
Design, layout, and analysis of 6T, 7T, and 8T SRAM cells in 180nm technology using Cadence Virtuoso.
# Design and Comparison of 6T, 7T, and 8T SRAM Cells

** Tisha Sardana (tishas.vl.23@nitj.ac.in)**

### ## 1. Abstract

This project presents the design, layout, and comparative analysis of 6T, 7T, and 8T Static Random Access Memory (SRAM) cells. The cells were designed in Cadence Virtuoso using a 180nm CMOS technology. Each design was fully verified with DRC (Design Rule Check) and LVS (Layout vs. Schematic) checks to ensure correctness.

The goal was to analyze the fundamental trade-offs between cell size, power consumption, and stability.
* **6T SRAM:** Achieves the most compact cell size but has lower read stability.
* **7T SRAM:** Improves read stability and power consumption by adding a seventh transistor.
* **8T SRAM:** Offers the highest performance and stability by completely separating the read and write ports, at the cost of a larger cell area.

This analysis helps in selecting the optimal SRAM architecture for a given application, whether it's for high-density, low-power, or high-performance systems.

---

### ## 2. Methodology

* **Tools Used:** Cadence Virtuoso
* **Technology:** 180nm CMOS
* **VDD:** 1.8 V
* **Verification:** Cadence Calibre for DRC and LVS

---

### ## 3. Cell Architectures and Layouts

#### 3.1 6T SRAM Cell
The 6T cell consists of two cross-coupled inverters and two access transistors. While it is the most area-efficient design, it suffers from read stability challenges because the read and write paths are shared.

| 6T Schematic (Fig. 1) | 6T Layout (Fig. 2) |
| :--------------------: | :----------------: |
| ![6T Schematic](images/6T_schematic.png) | ![6T Layout](images/6T_layout.png) |

#### 3.2 7T SRAM Cell
The 7T cell adds an extra transistor to the 6T design, which helps to isolate the read path from the storage nodes. This addition partially decouples the read and write operations, improving read stability and power efficiency.

| 7T Schematic (Fig. 3) | 7T Layout (Fig. 4) |
| :--------------------: | :----------------: |
| ![7T Schematic](images/7T_schematic.png) | ![7T Layout](images/7T_layout.png) |

#### 3.3 8T SRAM Cell
The 8T cell uses two additional transistors to create a dedicated read port (RWL and RBL), completely separating the read and write paths. This design eliminates the read-disturb issue, offering the highest stability and more reliable data access, though it consumes the largest area.

| 8T Schematic (Fig. 5) | 8T Layout (Fig. 6) |
| :--------------------: | :----------------: |
| ![8T Schematic](images/8T_schematic.png) | ![8T Layout](images/8T_layout.png) |

---

### ## 4. Analysis & Results

Post-layout simulations were performed to compare the key performance metrics of each cell.

#### Static Noise Margin (SNM) Analysis
The "butterfly curve" was generated to analyze the read stability of the cell. The Static Noise Margin (SNM) is the side length of the largest square that can fit inside the "eyes" of the curve. It represents the cell's tolerance to noise before it accidentally flips its stored data.

![SNM Butterfly Plot for 6T Cell](images/graph.jpg)

#### Physical Verification (Table 1)
All cell layouts were successfully verified with zero DRC errors and zero LVS mismatches.

| Cell Type | DRC Errors | LVS Mismatches |
| :-------- | :--------: | :------------: |
| 6T        |     0      |       0        |
| 7T        |     0      |       0        |
| 8T        |     0      |       0        |

#### Performance Comparison (Table 2)
This table summarizes the key trade-offs between the three designs. The average power was normalized to micro-watts (µW) for a clear comparison.

| Cell Type | Transistors | Area (μm²) | Avg. Power (µW) | Read/Write Isolation |
| :-------- | :---------: | :--------: | :-------------: | :------------------: |
| **6T SRAM** |      6      |   426.63   |     1190.0      |        Shared        |
| **7T SRAM** |      7      |   559.12   |      799.8      |       Partial        |
| **8T SRAM** |      8      |   747.58   |       1.08      |         Full         |

*(Note: Area and power values are from post-layout simulation.)*

---

### ## 5. Conclusion

This project successfully demonstrated the design and verification of 6T, 7T, and 8T SRAM cells. The analysis clearly shows the trade-offs between cell area, power, and stability.

* The **6T cell** is the most area-efficient, making it ideal for high-density applications.
* The **7T cell** offers a good balance of improved stability and power efficiency with a moderate area increase.
* The **8T cell** provides the highest read stability by using a separate read port, making it the best choice for high-performance or low-voltage applications where data integrity is critical.
