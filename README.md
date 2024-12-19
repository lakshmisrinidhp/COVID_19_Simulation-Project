# COVID-19 Simulation Project

This project simulates the spread of COVID-19 in specified countries using demographic data and a Markov chain model. The simulation generates detailed and aggregated results, which are visualized in a bar chart to show the progression of infection states over time.

---

## How the Project Works

### 1. **Input Data**
- **Demographic Data (`a3-countries.csv`)**:
  - Contains information about each country's population, median age, and age group distributions.
  - Columns: `country`, `population`, `median_age`, `less_5`, `5_to_14`, `15_to_24`, `25_to_64`, `over_65`.
- **Simulation Parameters (`sim_parameters.py`)**:
  - `TRASITION_PROBS`: Transition probabilities for state changes based on age groups.
  - `HOLDING_TIMES`: Number of days individuals remain in a specific state.

### 2. **Simulation Workflow**
1. **Setup**:
   - Read demographic data from `a3-countries.csv`.
   - Generate sample populations for each country using their population and age group distributions.
2. **State Transitions**:
   - Use a Markov chain to simulate daily health state changes for each individual over the specified date range.
   - States include `Healthy (H)`, `Infected (I)`, `Symptomatic (S)`, `Deceased (D)`, and `Immune (M)`.
3. **Outputs**:
   - **Simulated Time Series (`a3-covid-simulated-timeseries.csv`)**:
     - Contains detailed state transitions for each individual.
   - **Summary Time Series (`a3-covid-summary-timeseries.csv`)**:
     - Aggregates state counts by country and date.
   - **Visualization (`a3-covid-simulation.png`)**:
     - A stacked bar chart showing infection progression for specified countries.

### 3. **Visualization**
- The bar chart is created using the `create_plot()` function provided in `helper.py`.
- Displays state distributions (`Healthy`, `Infected`, `Symptomatic`, etc.) for each country over time.

---

## Python Libraries Used

- **`pandas`**: For data manipulation and storage.
- **`matplotlib`**: For creating the visualization.
- **`numpy`**: For numerical computations.
- **`csv`**: For reading and writing CSV files.
- **`random`**: For generating random transitions in the Markov chain.
- **`unittest`**: For testing the implementation.
- **`os`** and **`pathlib`**: For file path operations.

---

## How to Run the Project

1. **Install Dependencies**:
   Install the required Python libraries using pip:
   ```bash
   pip install pandas matplotlib
   ```

2. **Prepare Input Files**:
   - Ensure `a3-countries.csv` is in the working directory.
   - The file must follow the specified format with demographic data.

3. **Run the Simulation**:
   - Implement the `run()` function in `assignment3.py`.
   - Use the following arguments:
     - `countries_csv_name`: Name of the CSV file (e.g., `a3-countries.csv`).
     - `countries`: List of countries to simulate (e.g., `['Afghanistan', 'Sweden', 'Japan']`).
     - `start_date` and `end_date`: Date range for the simulation (e.g., `2021-04-01` to `2022-04-30`).
     - `sample_ratio`: Number of individuals per million population (e.g., `1e6`).
   - Example usage:
     ```python
     from assignment3 import run
     run(countries_csv_name='a3-countries.csv', countries=['Afghanistan', 'Sweden'], start_date='2021-04-01', end_date='2022-04-30', sample_ratio=1e6)
     ```

4. **Validate Results**:
   - Use `test.py` to verify the implementation:
     ```bash
     python test.py
     ```

5. **View Outputs**:
   - Check the generated files:
     - `a3-covid-simulated-timeseries.csv`
     - `a3-covid-summary-timeseries.csv`
     - `a3-covid-simulation.png`

---

## Project Outputs

1. **Simulated Time Series (`a3-covid-simulated-timeseries.csv`)**:
   - Columns: `person_id`, `age_group_name`, `country`, `date`, `state`, `staying_days`.
   - Tracks individual state transitions over time.

2. **Summary Time Series (`a3-covid-summary-timeseries.csv`)**:
   - Columns: `date`, `country`, `H`, `I`, `S`, `D`, `M`.
   - Aggregates state counts by date and country.

3. **Visualization (`a3-covid-simulation.png`)**:
   - Stacked bar chart showing infection progression by state.

---

## Future Enhancements

- Add support for country-specific and date-specific transition probabilities.
- Include vaccination effects and other real-world factors.
- Implement additional visualizations (e.g., line charts, heatmaps).

---

Enjoy simulating and analyzing the progression of COVID-19 in different countries! 🌍
