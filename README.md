# RESBASE

RESBASE is a database of nuclear resonance-parameter information used by the [AUTOTALYS](https://github.com/arjankoning1/autotalys) system for automated nuclear-data evaluation and processing.

This repository contains data files rather than a standalone application. Resonance-related inputs, evaluated-data components, and associated calculation results are organized by nuclide.

## Repository structure

The top-level directories are named after individual nuclides, for example `Ag107`, `Al027`, and `Am241`. Metastable states are distinguished where applicable, for example `Ag108m`.

A typical directory has the following structure (using `Ag107` as an example):

```text
resbase/
└── Ag107/
    ├── input/
    │   ├── tares.inp
    │   └── tares.out
    ├── files/
    │   ├── n-Ag107.mf1
    │   ├── n-Ag107.mf2
    │   ├── n-Ag107.mf32c
    │   ├── n-Ag107.mf33
    │   └── ...
    └── random/
        ├── n-Ag107.mf1.0000
        ├── n-Ag107.mf1.0001
        └── ...
```

The contents vary between nuclides.

- **`input/`** contains input and output files for resonance-related calculations, including `tares.inp` and `tares.out` in the example above.
- **`files/`** contains nuclide-specific data components, including files named according to ENDF material-file conventions. For example, MF2 is associated with resonance parameters, while MF32 and MF33 concern covariance data.
- **`random/`** contains numbered data-file variants, which can be used for sampled or randomized resonance-data workflows.

These descriptions characterize the repository organization; the precise interpretation of a particular file depends on the program that reads or produces it.

## Obtaining the database

Clone the repository with Git:

```bash
git clone https://github.com/arjankoning1/resbase.git
```

To update an existing clone:

```bash
cd resbase
git pull
```

Alternatively, download a source archive from the repository's GitHub page.

## Use with AUTOTALYS

RESBASE is intended to serve as a resonance-data resource within the wider AUTOTALYS workflow. The AUTOTALYS setup should obtain RESBASE alongside the other required software and data repositories, and the relevant programs should be configured to locate the installed `resbase/` directory.

The location of RESBASE is installation-dependent; it need not be in the user's home directory. Consult the AUTOTALYS installation scripts for the data-directory layout expected by the installed version.

## Data provenance and updates

Resonance parameters and their covariance information can be evaluation-dependent. When using or modifying these files, retain the original source information and document any changes to the evaluation, parameter set, or sampling procedure. Not all nuclides necessarily have the same set of files.

## Related repositories

- [AUTOTALYS](https://github.com/arjankoning1/autotalys) — setup scripts for the complete system
- [TALYS](https://github.com/arjankoning1/talys) — nuclear reaction modelling
- [TEFAL](https://github.com/arjankoning1/tefal) — evaluated nuclear-data file processing
- [TASMAN](https://github.com/arjankoning1/tasman) — nuclear-model sensitivity and uncertainty analysis

## Author

Arjan Koning
