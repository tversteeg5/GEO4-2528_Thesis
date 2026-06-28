# Methodology Notebooks for District Heating Network and TES Analysis

This repository contains the Jupyter notebooks used to support the methodology of the MSc thesis:

**Decentralized thermal energy storage in district heating for supply temperature reduction**
*A case study of the Arnhem district heating system*

The notebooks document the modelling and analysis workflow used to evaluate whether decentralized short-term thermal energy storage (TES) at substation level can help reduce supply temperatures in an existing second- and third-generation district heating network.

The code is shared to provide transparency on the calculation logic, assumptions, and workflow structure. It is not intended as a directly reproducible package.

## Important note

The original analysis was developed for the Arnhem district heating network, using operational data, network characteristics, and project-specific parameter values provided by Vattenfall.

These data are not included in this repository.

To protect sensitive and proprietary information:

* input files were renamed to placeholders such as `XX.xlsx` or `xx.xlsx`;
* project-specific parameters were replaced with placeholders such as `XX`;
* generated outputs, figures, and result files were removed;
* some cells contain placeholder values and therefore require manual completion before execution.

As a result, the notebooks will not reproduce the thesis results without the original data and parameter set.

## What is included

The repository contains the following notebooks:

### `pressure_loss_max_m.ipynb`

Calculates pressure losses and maximum allowable mass flow in a simplified pipe network.

This notebook supports the hydraulic part of the methodology by using pipe lengths, diameters, demand fractions, friction-factor assumptions, and minor-loss factors to estimate pressure drops in the primary district heating network. It also includes pressure-profile calculations and Monte Carlo-style variation of demand fractions.

### `thermal_storage.ipynb`

Demonstrates the thermal energy storage heat-loss model.

The notebook converts a state-of-charge-like variable into a simplified layered cylindrical tank representation. It then estimates hourly TES heat losses based on storage volume, tank geometry, hot and cold layer temperatures, ambient temperature, insulation properties, and state of charge.

The file should be named `thermal_storage.ipynb` in the repository, because the main notebook imports the TES heat-loss function from this notebook.

### `Thesis_code_main.ipynb`

Contains the main thesis workflow.

This notebook combines the broader analysis steps used in the thesis, including:

* hourly demand and temperature data processing;
* heat-loss separation;
* minimum supply temperature estimation;
* decentralized TES sizing and dispatch logic;
* comparison of scenarios with and without TES;
* 6-hour and carryover TES operating strategies;
* simplified pressure-loss and pumping-power calculations;
* heat-loss and TES heat-loss calculations;
* heat pump performance calculations;
* economic calculations, including CAPEX and delta LCOH;
* emission calculations;
* uncertainty and sensitivity analysis;
* plots of the main results.

## Thesis context

The thesis investigates how decentralized short-term TES can support lower supply temperature operation in existing district heating networks.

The main research question is:

**To what extent can decentralized short-term TES at the substation level enable lower supply temperature operation in existing second- and third-generation district heating networks?**

The methodology was applied to the Arnhem district heating system. The analysis focused on the primary network and evaluated how TES near a hydraulically constrained downstream demand area can reduce peak transport requirements, lower required supply temperatures, and affect heat losses, source dispatch, emissions, heat pump performance, pumping energy, and levelized cost of heat.

## Repository purpose

The purpose of this repository is to make the modelling approach transparent at a methodological level.

It is intended for:

* documenting the calculation logic behind the thesis;
* showing how the simplified thermo-hydraulic and TES models were structured;
* providing insight into the assumptions and workflow used in the analysis.

## Requirements

The notebooks use standard scientific Python packages.

A basic Python environment can be created with:

```bash
pip install -r requirements.txt
```

The current notebooks use packages such as:

* `pandas`
* `numpy`
* `matplotlib`
* `openpyxl`
* `ipykernel`

The main notebook also uses `import_ipynb` to import functions from other notebooks. If the notebooks are executed in this structure, the package `import-ipynb` should also be available in the Python environment.

## Limitations

The notebooks are simplified research models and should not be interpreted as operational district heating software.

Important limitations include:

* the model represents the primary network in a simplified way;
* demand is aggregated at network nodes;
* the calculations are based on hourly quasi-steady assumptions;
* TES operation is represented through simplified charging and discharging logic;
* pressure-loss and pumping calculations are based on simplified hydraulic assumptions;
* the original Vattenfall data and parameter values are not included;
* results depend strongly on local network characteristics and input assumptions.

## Notes

* No proprietary input files are included.
* No generated figures or result files are included.
* Placeholder values must be replaced before the notebooks can be used.
* The notebooks are provided for methodological transparency and documentation of the thesis workflow.
