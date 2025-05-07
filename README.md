# 📦 Manufacturing System Modeling with Colored Petri Nets  
<p align = "center">  
<img src="execucao_cpn.gif" height="400"  />  
</p>  

This project models a **factory with 4 manufacturing cells** using **Colored Petri Nets (CPNs)** in the **CPN Tools** environment. The goal is to represent the product flow, the behavior of transport robots, and the processing of products by machines, while respecting constraints such as limited buffer capacity and specific production routes.  

## 🔧 About the System  

The factory consists of:  
- A **general input warehouse** with two product types: `item_i` and `item_j`.  
- **Four manufacturing cells**, each responsible for processing products.  
- An **output warehouse** where finished products are stored.  

Each manufacturing cell contains:  
- An **input buffer and an output buffer**  
- Three **machines**  
- Three **robots**  

## 🎯 Modeling Objective  

The modeling aims to:  
- Control the product flow through the cells.  
- Ensure correct processing of each product type according to its route.  
- Simulate capacity constraints and resource availability.  

## 🧠 Modeling Approach  

The modeling uses:  
- **Colored Petri Nets (CPNs)**: to represent different product types and system states.  
- **Hierarchical pages**: to modularize the system into cells, machines, and the overall system.  
- **Colored tokens**: represent distinct product types (`item_i` and `item_j`).  
- **Transition guards**: define the conditions for system transitions to occur.  

## 🧩 System Components  

### ✅ Products  
- `item_i`: Type I product  
- `item_j`: Type J product  

### ✅ Robots  
- `Robot 1`: Transports products from the cell's input buffer to machine M1.  
- `Robot 2`: Moves products from M1's output to either M2 (for `item_i`) or M3 (for `item_j`).  
- `Robot 3`: Takes products from M2/M3 output to the cell's output buffer.  

Each robot's availability is modeled using boolean tokens (`true` = available, `false` = busy).  

### ✅ Machines  
- **Machine 1**: Processes both product types (I and J).  
- **Machine 2**: Exclusive to `item_i` products.  
- **Machine 3**: Exclusive to `item_j` products.  

Each machine has:  
- An **input buffer (capacity: 4 items)**  
- An **output buffer (capacity: 4 items)**  
- A **processing transition** with represented time or delay.  

### ✅ Manufacturing Cells  
Each cell contains its own instance of the above components, modeled as a **hierarchical subpage**.  

## 📌 System Behavior  

1. **Product Request**:  
   - The cell requests a product from the factory's input warehouse, which sends either an `item_i` or `item_j` to its input buffer.  

2. **Internal Movement**:  
   - Robots control the transport of products between machine input and output buffers, respecting availability.  

3. **Processing**:  
   - Products follow their specific route: M1 → M2 or M1 → M3.  
   - After final processing, they are sent to the cell's output buffer and then to the factory's output warehouse.  

## 📁 File Structure of `smartfactory.cpn`  

- `Smart Factory Page`: Connects all cells, input warehouse, and output warehouse.  
- `Cell Page`: Defines the components of a single cell.  
- `Machine Page`: Defines the operation of each machine (including buffers and processing transitions).  

## 🚀 Requirements  

- [CPN Tools](https://cpntools.org/)  

## Project Video  

For more details, check out the [explanation video](https://drive.google.com/file/d/1Fq92dcAyffwg1yq9Lrnh6UqAtt3kXBVu/view?usp=sharing).  

## 👨‍🔬 Author  

This project was developed by **Mateus Pincho** as part of the evaluation for the Discrete Event Systems course, taught by Prof. Dr. Kyller Costa Gorgônio.  

---
