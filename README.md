
# Database Normalization Project
Team members:
Niharika Gurram [16360904]
Rohith Reddy Yarramreddy [12618055]
---

## Project Overview
This project provides a Python-based tool for decomposing relational databases into various normal forms (1NF, 2NF, 3NF, BCNF, 4NF, and 5NF) based on input functional dependencies (FDs) and multivalued dependencies (MVDs). The tool allows you to:

1. Load relational data from an Excel file.
2. Specify primary keys, functional dependencies, and multivalued dependencies.
3. Automatically decompose tables through normalization levels.
4. Display the resulting tables and schemas after each normalization step.

---


## How to Use

1. **Input Files and Data**
   - Provide an Excel file (e.g., `relationinput.xlsx`) containing the relational data.
   - Specify functional dependencies in a text file (e.g., `FD.txt`) in the format `LHS -> RHS` or `LHS -->> RHS` for FDs and MVDs.

2. **Execution**
   - Run the main script and follow prompts to enter:
     - The file name for the relation.
     - The file name for functional dependencies.
     - Primary keys for the table.
   - Specify the desired level of normalization (1NF to 5NF).

3. **Normalization Workflow**
   - The tool decomposes the input table iteratively through:
     - **1NF:** Ensures atomic values.
     - **2NF:** Eliminates partial dependencies.
     - **3NF:** Removes transitive dependencies.
     - **BCNF:** Ensures that each functional dependency has a superkey on the left.
     - **4NF:** Removes multivalued dependencies.
     - **5NF:** Decomposes tables based on join dependencies, adhering to project-specific business rules.

4. **Output**
   - Each normalization step outputs tables with:
     - Schema structure in SQL `CREATE TABLE` statements.
     - Displayed tables after each decomposition.
     - Information on primary keys and dependencies.

## Example Run

```plaintext
Enter the primary keys, separated by commas:  OrderID,FoodID,DrinkID
Detect Highest Normal form of table: Yes(1), No(0):  1
Highest normal form: 0NF
Select the highest level of normalization you want to achieve:
Select 1 - Normalisation up to 1NF
Select 2 - Normalisation up to 2NF
Select 3 - Normalisation up to 3NF
Select 4 - Normalisation up to BCNF
Select 5 - Normalisation up to 4NF
Select 6 - Normalisation up to 5NF
Enter your option (1-6): 4
```

## Example Output

- **Normalized Tables** in SQL Schema format:
  ```sql
  CREATE TABLE DrinkAllergen (
    OrderID VARCHAR(255),
    FoodID VARCHAR(255),
    DrinkID VARCHAR(255),
    DrinkAllergen VARCHAR(255),
    PRIMARY KEY (OrderID, FoodID, DrinkID, DrinkAllergen),
    FOREIGN KEY (OrderID) REFERENCES BaseRelation(OrderID),
    FOREIGN KEY (FoodID) REFERENCES BaseRelation(FoodID),
    FOREIGN KEY (DrinkID) REFERENCES BaseRelation(DrinkID)
);
  ```
- **Tabular Displays** with fields, data, primary keys, and dependencies after each normalization stage.

## Project Structure

- **Main Script:** Drives the normalization process.
- **Functions:** Separate functions handle each normalization form.
- **Dependencies:** All dependencies, keys, and multivalued constraints are user-defined, enabling flexible schema decompositions based on various data configurations.

---

This README covers initial setup, usage, and expected outputs for efficient database normalization using functional and multivalued dependencies in Python.

