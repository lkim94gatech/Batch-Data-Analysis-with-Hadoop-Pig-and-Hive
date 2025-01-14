# Batch-Data-Analysis-with-Hadoop-Pig-and-Hive

This project implements **Batch Data Analysis** using **Hadoop**, **MapReduce**, **Pig**, and **Hive**. The lab provides hands-on experience in setting up a Hadoop cluster, working with distributed data processing frameworks, and performing big data analysis on large datasets.

## Important Notice
**For security reasons, sensitive files such as credentials, keys, and configuration files will NOT be included in this repository.**

---

## Overview

The system includes:
- **Amazon EMR Cluster** for distributed computing.
- **HDFS** for distributed storage.
- **MapReduce** programs for custom big data processing tasks.
- **Pig** for high-level data flow analysis.
- **Hive** for SQL-like querying of big data.

---

## Features

1. **Hadoop Cluster Setup**:
   - Deploy and configure a Hadoop cluster using Amazon EMR.
   - Configure security groups for SSH access and cluster communication.

2. **MapReduce Programs**:
   - **Bigram Analysis**:
     - Emit bigrams coined after 1992.
     - Calculate the average occurrence of bigrams in books.
   - Output formats include `(bigram, year)` and `(bigram, average)`.

3. **Pig Programs**:
   - Compute the most common bigram for a specific year.
   - Find the most common bigram for each year in the dataset.

4. **Hive Queries**:
   - Create a Hive meta-store table from the dataset.
   - Query to find the most popular bigram across all years.

---

## Setup Instructions

### Prerequisites
- Installed tools: `AWS CLI`, `Python 3.x`, `Hadoop`, `Pig`, `Hive`
- Amazon AWS Account with EMR access

### Steps
1. **Set Up a Hadoop Cluster**:
   - Navigate to the **Amazon EMR console**.
   - Create a new cluster with the appropriate configurations.
   - Configure inbound SSH rules for the master node.

2. **Upload Datasets to HDFS**:
   - Enable an SSH tunnel to the master node.
   - Use the **Hue** interface to upload datasets.
   - Adjust port configurations (if required) for dataset accessibility.

3. **Set Up `mrJob` on the Master Node**:
   - Install dependencies:
     ```bash
     sudo yum install python-pip
     sudo pip install mrjob
     ```
   - Create and configure `mrjob.conf`.

4. **Run MapReduce Programs**:
   - Execute MapReduce jobs using:
     ```bash
     python wordcount-mr.py -r hadoop hdfs:///user/<username>/dataset.txt --output-dir=hdfs:///user/<username>/output --conf-path=mrjob.conf
     ```

5. **Run Pig Programs**:
   - Option 1: Submit Pig scripts through the Hue interface.
   - Option 2: Use the Hadoop terminal:
     ```bash
     hadoop jar /path-to-runner/command-runner.jar pig-script --run-pig-script --args -f <s3-bucket-path>/wordcount-pig.txt
     ```

6. **Run Hive Queries**:
   - Create a Hive meta-store table from the dataset.
   - Use the **Hue** interface or terminal to run Hive queries.

---

## Challenges
1. Implement a MapReduce program to emit bigrams coined after 1992.
2. Calculate the average occurrence of bigrams across books using MapReduce.
3. Compute the most common bigram for a specific year using Pig.
4. Determine the most common bigram for each year using Pig.
5. Query the most popular bigram across all years using Hive.

---

## Testing

### Functionalities
- **MapReduce**: Verify outputs for bigram analysis programs.
- **Pig**: Validate scripts for yearly and overall bigram computations.
- **Hive**: Ensure accurate querying of the most popular bigram.
