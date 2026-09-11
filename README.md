 # Evolution of the Magnetic Field in Disk Galaxies of the IllustrisTNG Simulation

![Project Status](https://img.shields.io/badge/Status-Active%20Development-brightgreen)
![Start Date](https://img.shields.io/badge/Started-March%2026%2C%202026-blue)
![Simulation](https://img.shields.io/badge/Data-TNG50--1%20%7C%20IllustrisTNG-orange)
![Python](https://img.shields.io/badge/Language-Python%203-blue)

### Project Overview
This repository contains the computational pipeline and analytical framework developed for my Bachelor's Thesis in Astronomy at **Universidad de Antioquia**.

The project investigates the temporal evolution and spatial distribution of galactic magnetic fields across cosmic time ($z = 0$ to $z = 12$) using high-resolution cosmological magnetohydrodynamic (MHD) data from the **TNG50-1** run of the **IllustrisTNG** suite. By tracking the main progenitor trees of a sample of **377 star-forming disk galaxies** selected at $z = 0$ ($M_{\text{gas}} \in [10^{9.6}, 10^{12}] \, M_\odot$), we characterize how magnetic field intensity and topology reorganize between the galactic disk and the halo under the influence of gas thermodynamics, star formation, and supermassive black hole (SMBH) feedback.



### Research Team & Supervision
- **Author:** **Brandon Daniel Montoya Ortiz** (Undergraduate Student in Astronomy)
- **Advisor:** **Prof. Dr. Juan Carlos Muñoz Cuartas** (Associate Professor / Computational Cosmology Expert)
- **Institution:** Institute of Physics, Faculty of Exact and Natural Sciences, **Universidad de Antioquia (UdeA)**, Medellín, Colombia.
- **Project Commencement:** March 26, 2026  
- **Current Status:** *In Active Development*



### Key Objectives

### General Objective
To study the evolution of the magnetic field in a sample of disk galaxies from the **TNG50-1** simulation by tracking their progenitor histories across redshifts, characterizing variations in magnetic intensity, spatial distribution $B(R, z)$, and their coupling to host galaxy physical properties.

### Specific Objectives
1. **Temporal & Spatial Characterization:** Map $B(R, z)$ field strength profiles (face-on and edge-on) in 2D cylindrical coordinates across redshift snapshots.
2. **Gas Phase Thermodynamics:** Classify the interstellar and circumgalactic medium (ISM/CGM) into thermal/ionization phases and evaluate magnetic energy partition among them.
3. **SMBH Feedback Coupling:** Correlate magnetic field reorganizations with supermassive black hole activity, accretion rates, and Eddington ratios.
4. **Star Formation Relation:** Analyze the link between Star Formation Rate (SFR) surface density and local magnetic field amplification across cosmological epochs.



### Computational Pipeline & Data Methodology

### 1. Merger Tree Extraction & Multi-Snapshot Evolutionary Tracks (*Completed & Fully Implemented*)
- **Automated SubLink Merger Trees Pipeline:** Fully functional Python pipeline developed to extract the evolutionary main branches across **20 full snapshots** (tracing galaxies continuously from $z = 0$ back to $z = 12$).
- **Complete Feature Extraction per Epoch:** Systematically extracted and validated both primitive gas-cell properties and global subhalo properties for every evolutionary snapshot:
  - *Gas Cell Primitives (PartType0):* `Coordinates`, `Velocities`, `Magnetic_Field` $(B_x, B_y, B_z)$, `Density`, `Internal_Energy`, `Electron_Abundance`, `NeutralHydrogenAbundance`, `GFM_Metals`, `GFM_Metallicity`, `GFM_CoolingRate`, `Masses`, and `Potential`.
  - *Global Subhalo Diagnostics:* Stellar Mass ($M_*$), Gas Mass ($M_{\text{gas}}$), Dark Matter Mass ($M_{\text{DM}}$), Star Formation Rate ($\text{SFR}$), SMBH Mass ($M_{\text{BH}}$), SMBH Accretion Rate, and Eddington Ratio ($\lambda_{\text{Edd}}$).

### 2. Thermodynamic Disk Isolation & Gas Pruning (*Current Working Milestone*)
- **Thermodynamic Pruning Protocol:** Implementing specific internal energy (`Internal_Energy`, $U$) thresholding to isolate the cold, dense rotating disk gas from shock-heated diffuse halo gas and circumgalactic outflows.
- **Methodological Calibration:** The thermodynamic energy cut ($U \le U_{\text{cut}}$) follows and adapts the disk-isolation framework established in **Daniel H. Certuche-Grueso's Bachelor's Thesis (FACom, UdeA, 2025)** under Dr. Juan Carlos Muñoz-Cuartas. This ensures the exclusion of high-temperature/low-density gas phases, retaining strictly the dynamically cold gas that constitutes the disk mid-plane for pristine magnetic field profile reconstruction $B(R, z)$.

### 3. Reference Frame & Kinematic Alignment
- **Dynamic Center Alignment:** Center of mass and velocity transformations relative to the subhalo's central potential minimum.
- **Angular Momentum Normalization:** Computation of the stellar specific angular momentum vector within $2 R_{\text{half}}$ to align the galactic disk normal perpendicular to the $z$-axis, establishing a standardized cylindrical coordinate system $(R, z)$ across all galaxies and redshifts.



### Theoretical & Physical Context
Under ideal magnetohydrodynamics (MHD), magnetic field lines are frozen into the plasma flow:
- **Flux Conservation & Compression:** Isothermal gas collapse amplifies seed magnetic fields ($\sim 10^{-14} \text{ G}$) during structural hierarchy formation up to microgauss $(\mu\text{G})$ levels observed in local disks.
- **Turbulent Dynamo & Rotation:** Shear drives large-scale magnetic field ordering, while stellar feedback drives galactic winds that transport amplified fields into the halo along the minor axis.
- **IllustrisTNG Advantage:** TNG50-1 provides sub-kiloparsec spatial resolution ($m_{\text{baryon}} \approx 8.5 \times 10^4 \, M_\odot$), allowing simultaneous tracking of multiphase gas kinematics, feedback outflows, and magnetic field amplification in disk galaxies.



### Planned Deliverables & Analysis
- **2D Cylindrical Magnetic Maps:** Constructing face-on $B(R)$ and edge-on $B(z)$ intensity maps and dispersion profiles.
- **Evolutionary Database:** Relational dataset containing local gas cell physics and global galaxy evolutionary tracks across cosmological snapshots.
- **Statistical Correlation Matrix:** Quantitative assessment of magnetic field strength versus Eddington ratio, SFR, and thermal gas phase fractions.



### Tech Stack & Dependencies
- **Primary Language:** Python 3
- **Data Handling & I/O:** `h5py` (IllustrisTNG HDF5 snapshot parsing), `numpy`, `pandas`
- **Cosmological Analysis & Trees:** `illustris_python` (SubLink merger tree processing)
- **Coordinate Transformations & Stats:** `scipy.spatial.transform`, `scipy.stats`
- **Visualization:** `matplotlib`, `seaborn`


### References & Background Literature
- **Certuche-Grueso, D. H. (2025)** – *Morphological characterization of spiral arms in disk galaxies from the IllustrisTNG50 simulation and their relation to the properties of their host dark matter halos.* Bachelor's Thesis, Universidad de Antioquia (Advisor: Dr. Juan Carlos Muñoz-Cuartas).
- **Pillepich et al. (2019)** – *First results from the TNG50 simulation: the evolution of stellar and gaseous discs across cosmic time.* MNRAS, 490(3), 3196-3233.
- **Marinacci et al. (2018)** – *First results from the IllustrisTNG simulations: radio haloes and magnetic fields.* MNRAS, 480(4), 5113-5139.
- **Nelson et al. (2019a)** – *First results from the TNG50 simulation: galactic outflows driven by supernovae and black hole feedback.* MNRAS, 490(3), 3234-3261.
- **Ramesh et al. (2023)** – *Azimuthal anisotropy of magnetic fields in the circumgalactic medium driven by galactic feedback processes.* MNRAS, 526(4), 5483-5493.
