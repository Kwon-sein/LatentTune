# LatentTune: Efficient Tuning of High Dimensional Database Parameters via Latent Representation Learning


🥳 Accepted at **2025 IEEE 32nd International Conference on High Performance Computing, Data, and Analytics (HiPC 2025)** 🥳

## Abstract
Modern DBMS tuning is limited by expensive data collection, subset-only tuning in high-dimensional spaces, and reliance on similar workloads. LatentTune addresses these by **(i) augmenting training data, (ii) compressing all parameters into a latent space** to optimize the full configuration, and **(iii) injecting target workload metrics** for precise, workload-specific tuning. Experimental results demonstrate that LatentTune outperforms baseline models across four workloads on MySQL and RocksDB, achieving up to **1332% improvement for RocksDB** and **11.82% throughput gain with 46.01% latency reduction for MySQL**.

## Method

![Image](https://github.com/user-attachments/assets/eccee407-5ea8-42e3-bfe5-cd2ad6f52969)


LatentTune consists of four modules:

1. **Data Augmentation**  
   Expand a small set of measured configuration–metric pairs into a larger training set.

2. **Latent Space Learning (Encoder–Decoder)**  
   Train an encoder to map a high-dimensional configuration to a low-dimensional latent vector, and a decoder to reconstruct the full configuration.

3. **Latent-Space Bayesian Optimization**  
   Run BO directly in the latent space to efficiently explore promising regions under high dimensionality.

4. **Decoding & Deployment**  
   Decode the optimized latent vector back to a complete DB configuration and apply it to the DBMS for evaluation/deployment.

## Experiment

This is our experiment workload information.  
### MySQL Workload Information

| Workload Index | Scale Factor | Data Size | Read  | Insert | Scan | Update | Read Modify Write |
| -------------- | ------------ | --------- | ----- | ------ | ---- | ------ | ----------------- |
| A              | 12000        | 15GB      | 50%   | -      | -    | -      | 50%               |
| B              | 12000        | 15GB      | 95%   | -      | -    | 5%     | -                 |
| E              | 12000        | 15GB      | -     | -      | 5%   | 95%    | -                 |
| F              | 12000        | 15GB      | 50%   | -      | -    | -      | 50%               |


### RocksDB Workload Information

| Workload Index | Value Size | # of Entry | READ  | WRITE | UPDATE |
| -------------- | ---------- | ---------- | ----- | ----- | ------ |
| R90W10         | 16384      | 65472      | 90%   | 10%   | X      |
| R50W50         | 16384      | 65472      | 50%   | 50%   | -      |
| R10W90         | 16384      | 65472      | 10%   | 90%   | -      |
| UPDATE         | 16384      | 65472      | -     | -     | O      |

## Result

- Our experiment on MySQL.
<p align="left">
  <a href="https://github.com/user-attachments/assets/ab705c7f-f7bf-40a9-93a6-c885eb509fa1">
    <img src="https://github.com/user-attachments/assets/ab705c7f-f7bf-40a9-93a6-c885eb509fa1" width="500" />
  </a>
</p>


- Our experiment on RocksDB.
<p align="left">
  <a href="https://github.com/user-attachments/assets/a96c23af-ba4c-41fa-ba21-6d2ab5d8271f">
    <img src="https://github.com/user-attachments/assets/a96c23af-ba4c-41fa-ba21-6d2ab5d8271f" width="700" />
  </a>
</p>


## Dataset

We generated a dataset of 1,000 configuration–performance pairs by sampling configurations using Latin Hypercube Sampling (LHS) and evaluating each configuration with BenchBase.
Due to infrastructure constraints (the dataset was generated on our internal servers and is not directly redistributable), we do not release the raw dataset publicly. If you need access for research purposes, please contact us via email at seinkwon97@yonsei.ac.kr.
