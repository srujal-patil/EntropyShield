# EntropyShield: AI-Driven Anti-Ransomware Prototype

## Overview
EntropyShield is a conceptual Next-Generation Antivirus (NGAV) and Endpoint Detection and Response (EDR) prototype. It relies on behavioral machine learning rather than outdated virus signatures to detect and neutralize ransomware in real-time. 

This project was built from scratch in Google Colab to simulate the complete architecture of a modern cybersecurity defense pipeline.

## System Architecture

* **Phase 1: Real-Time File I/O Watchdog** Utilizes the `watchdog` library to monitor a local directory. It intercepts file modifications and calculates the Shannon Entropy of the binary payload in real-time to detect cryptographic patterns.
* **Phase 2: Behavioral Feature Pipeline** Uses `pandas` to aggregate raw system logs into sliding time-series windows, tracking file modification velocity and mean entropy shifts to separate normal user behavior from bulk encryption loops.
* **Phase 3: Scikit-Learn Classifier (The AI Brain)** A Scikit-Learn Random Forest model trained on synthetic kernel-level data. It uses Advanced Feature Engineering (Process Lineage and Magic Number alterations) to eliminate False Positives (like a user zipping a folder).
* **Phase 4: Defensive Responder Daemon** An automated response loop that simulates the `psutil` and `subprocess` libraries to hunt down malicious Process IDs (PIDs) and terminate them at the OS level in milliseconds.

## Technical Skills Demonstrated
- Python Systems Programming
- Machine Learning (`scikit-learn`)
- Data Aggregation (`pandas`, `numpy`)
- OS Process Management Simulation

## Note
*This is a simulated environment built for educational purposes in Google Colab. In a real-world enterprise deployment, Phase 1 would be replaced by an eBPF (Extended Berkeley Packet Filter) kernel probe on Linux, or a File System Minifilter Driver on Windows, to ensure the daemon remains invisible to Ring 3 User-Space malware.*
