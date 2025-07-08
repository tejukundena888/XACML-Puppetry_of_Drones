# XACML-Puppetry of Drones

This repository supports the research paper titled  
**"Puppetry of Drones: A Case Study on Drone Fly-Over Policies Following FAA Regulations"**,  
submitted to CPS-Sec 2025.

## ✨ Overview

Modern Unmanned Aerial Vehicles (UAVs) operate in complex airspaces, requiring dynamic, policy-based access control. While the Federal Aviation Administration (FAA) issues regulations for drone usage, these are written for human interpretation and not readily machine-enforceable.

This project presents an XACML-based framework to automate FAA regulatory compliance checks, simulating access control decisions based on real-time drone attributes such as weight, kinetic energy, remote ID broadcast, purpose of operation, and more.

## 🛠️ Components

### 1. **XACML Policy Files**
- Define fine-grained, attribute-based rules aligned with FAA airspace and safety requirements.
- Structured using:
  - `<PolicySet>`, `<Policy>`, and `<Rule>` elements.
  - Contextual elements like `<Target>`, `<Condition>`, and `<Obligation>`.

### 2. **Request Generator**
- Written in Python.
- Accepts attributes like `weight`, `remote ID`, `commercial purpose`, etc.
- Generates XACML requests based on combinations of attributes (from Excel or manual input).

### 3. **PDP Engine Integration**
- Uses [AuthzForce PDP CLI](https://github.com/authzforce/core) to evaluate requests.
- Executes command-line evaluation using the configured `pdp-config.xml` file.

### 4. **Decision Logging**
- Evaluated results are parsed and logged in a structured CSV format.
- Enables post-analysis and decision auditing.

## 🧪 Use Case Simulation

We simulate scenarios where a drone attempts to fly over restricted zones. The PDP returns `Permit` or `Deny` decisions based on:
- Presence or absence of remote ID.
- Night Operations
- Kinetic energy and exposed rotating parts.
- Whether individuals have been informed.
- Purpose (recreational/commercial) and operational certifications.

## 💡 Research Contribution

- ✅ Translated FAA drone regulations into machine-readable XACML policies.
- ✅ Using the existing system and Developed a modular framework for real-time authorization decision simulation.
- ✅ Demonstrated potential for integrating policy-driven safety in UAV operations.

## 🔗 Folder Structure

```
📁 XACML-Puppetry_of_Drones/
├── policies/                # XACML policy and policy set files
├── requests/                # Sample XACML request files
├── scripts/
│   ├── request_generator.py # Python script for generating requests from Excel
│   └── run_pdp.py           # Script for PDP evaluation and logging
├── pdp-config.xml           # AuthzForce configuration
├── input_data.xlsx          # Excel with scenario data
├── output_decisions.csv     # Result log
└── README.md
```

## 📦 Requirements

- Python 3.7+
- Java 11 or above
- pandas
- AuthzForce PDP CLI (included or linked)

## 🚀 How to Run

1. **Install dependencies**:
   ```bash
   pip install pandas
   ```

2. **Prepare data**:  
   Fill `input_data.xlsx` with scenario attributes.

3. **Run the evaluation**:
   ```bash
   python scripts/run_pdp.py
   ```

4. **View output**:  
   Results will be visible in console.

## 🧭 Future Work

- Extend support to NLP-driven policy extraction from raw FAA documents.
- Integrate a user interface for real-time access decision visualization.
- Explore drone-to-edge computing PDP communication for field use.

## 👩‍💻 Authors

- **Tejaswini Kundena** – Graduate Researcher, Texas A&M University-Corpus Christi  
- **Carlos Rubio-Medrano** – Faculty Guide
- With thanks to the FAA and the AuthzForce community for regulatory and tooling insights.

## 📜 License

This project is for academic and research purposes. Please cite our paper if you use or build on this work.
