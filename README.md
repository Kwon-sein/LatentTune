# LatentTune
LatentTune: Efficient Tuning of High Dimensional Database Parameters via Latent Representation Learning


🥳 Accepted at **2025 IEEE 32nd International Conference on High Performance Computing, Data, and Analytics (HiPC 2025)** 🥳


As data volumes continue to grow, optimizing database performance has become increasingly critical, making the implementation of effective tuning methods essential. Among various approaches, database parameter tuning has proven to be a highly effective means of enhancing performance. Recent studies have shown that machine learning techniques can successfully
optimize database parameters, leading to significant performance improvements. However, existing methods still face several limitations. First, they require substantial time to generate large training datasets. Second, to cope with the challenges of highdimensional optimization, they typically optimize only a subset of parameters rather than the full configuration space. Third, they often rely on information from similar workloads instead of directly leveraging information from the target workload. To address these limitations, we propose LatentTune, a novel approach that differs fundamentally from traditional methods. To reduce the time required for data generation, LatentTune incorporates a data augmentation strategy. Furthermore, it constructs a latent space that compresses information from all database parameters, enabling the optimization of the full configuration space. In addition, LatentTune integrates external metric information into the latent space, allowing for precise tuning tailored to the actual target workload. Experimental results demonstrate that LatentTune outperforms baseline models across four workloads on MySQL and RocksDB, achieving up to 1332% improvement for RocksDB and 11.82% throughput gain with 46.01% latency reduction for MySQL.

