# EntropyShield: AI-Driven Anti-Ransomware Prototype

## Overview
EntropyShield is a conceptual Next-Generation Antivirus (NGAV) and Endpoint Detection and Response (EDR) prototype. It relies on behavioral machine learning rather than outdated virus signatures to detect and neutralize ransomware in real-time. 

This project was built from scratch in Google Colab to simulate the complete architecture of a modern cybersecurity defense pipeline.

## System Architecture

* **Phase 1: Real-Time File I/O Watchdog** Utilizes the `watchdog` library to monitor a local directory. It intercepts file modifications and calculates the Shannon Entropy of the binary payload in real-time to detect cryptographic patterns.
* **Phase 2: Behavioral Feature Pipeline** Uses `pandas` to aggregate raw system logs into sliding time-series windows, tracking file modification velocity and mean entropy shifts to separate normal user behavior from bulk encryption loops.
* **Phase 3: Scikit-Learn Classifier (The AI Brain)** A Scikit-Learn Random Forest model trained on synthetic data. It uses Advanced Feature Engineering (Process Lineage and Magic Number alterations) to eliminate False Positives (like a user zipping a folder).
* **Phase 4: Defensive Responder Daemon** An automated response loop that simulates the `psutil` and `subprocess` libraries to hunt down malicious Process IDs (PIDs) and terminate them at the OS level in milliseconds.

## Technical Skills Demonstrated
- Python Systems Programming
- Machine Learning (`scikit-learn`)
- Data Aggregation (`pandas`, `numpy`)
- OS Process Management Simulation

## 🚀 Future Roadmap: Kernel-Level Integration
The current Phase 1 implementation uses a User-Space (`Ring 3`) watchdog monitor. A planned future upgrade involves migrating the filesystem monitoring directly into the OS Kernel (`Ring 0`) to prevent advanced malware from tampering with the security daemon. 

**Planned Architecture Upgrade:**
* **eBPF (Extended Berkeley Packet Filter):** Deploying a C-based kernel probe via the Python `bcc` library on a dedicated Linux environment to hook into the `vfs_write` system call. 
* **Process ID Tracking:** This will allow the pipeline to definitively link high-entropy file modifications to specific executable names and PIDs, granting the AI model perfect context before triggering an active response.

## Note
*This is a simulated environment built for educational purposes in Google Colab.*
