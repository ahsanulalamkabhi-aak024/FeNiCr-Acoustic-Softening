# FeNiCr-Acoustic-Softening

This repository contains the LAMMPS input files, interatomic potentials, structure files, processed results, and manuscript figures for the molecular dynamics study of acoustic softening in Fe-Ni-Cr alloys under simple shear deformation.

## Repository Structure

```text
FeNiCr-Acoustic-Softening/
│
├── LAMMPS_SCRIPTS/
│   ├── in.acoustic_ss
│   └── in.create_alloy
│
├── POTENTIALS_&_DATAFILES/
│   ├── MEAM_POTENTIAL_MAIN_SIMULATION/
│   └── EAM_POTENTIAL_HIGH_TEMPERATURE/
│
├── RESULTS/
│   ├── ELASTIC_RESULTS/
│   ├── FLOW_STRESS_RESULTS/
│   ├── SENSITIVITY_RESULTS/
│   └── DXA_RESULTS/
│
└── FIGURES/
```

## LAMMPS Scripts

### `in.acoustic_ss`

Main LAMMPS input file used for the simple-shear and vibration-assisted simulations.

The main vibration parameters can be changed directly in the script, including:

* vibration amplitude
* vibration frequency
* simulation temperature
* duration of the loading stages

The simulations consist of three stages:

1. Shear before vibration
2. Shear with vibration
3. Shear after vibration

### `in.create_alloy`

LAMMPS input file used to generate the FCC Fe-Ni-Cr alloy structures.

The composition and simulation-cell size can be modified directly in the script.

---

## Potentials and Data Files

### `MEAM_POTENTIAL_MAIN_SIMULATION`

Contains the files used for the main simulations:

```text
data.FeNiCr
library.meam
NiCrFe.meam
```

### `EAM_POTENTIAL_HIGH_TEMPERATURE`

Contains the files used for the temperature-sensitivity simulations:

```text
FeNiCr.t
data.Fe60Ni15Cr25_t_30
```

---

## Results

### `ELASTIC_RESULTS`

Contains the processed results for vibration applied in the elastic deformation regime.

### `FLOW_STRESS_RESULTS`

Contains the processed results for vibration applied during established plastic flow.

### `SENSITIVITY_RESULTS`

Contains the results for:

* composition sensitivity
* simulation-size sensitivity
* temperature sensitivity

### `DXA_RESULTS`

Contains the Dislocation Extraction Algorithm, DXA, results used for the dislocation-density and defect-evolution analysis.

---

## Figures

The `FIGURES` folder contains the final figures corresponding to the manuscript results.

---

## Running the Main Simulation

Place the following files in the same working directory:

```text
in.acoustic_ss
data.FeNiCr
library.meam
NiCrFe.meam
```

Then run LAMMPS using:

```bash
lmp -in in.acoustic_ss
```

Simulation parameters can be changed directly near the beginning of the input file.

For different alloy compositions or simulation sizes, first modify and run:

```bash
lmp -in in.create_alloy
```

and then use the generated `data.FeNiCr` file for the main simulation.

---

## Notes

The supplied result files contain the processed numerical data used in the manuscript.

Each simulation condition should preferably be run in a separate folder to avoid overwriting output files.

For questions regarding the repository or reproduction of the simulations, please contact the authors.

