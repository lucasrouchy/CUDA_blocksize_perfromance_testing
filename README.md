# CUDA Blocksize Performance Testing

## Background

This project is an extension to my original monte carlo simulation using openMP(repo)[https://github.com/lucasrouchy/Monte_Carlo_Sim]. The goal was do some performance testing on a known simulation using CUDA code with a focus on evaluating the impact of block size and the number of trials on the performance of DGX OSU servers. The testing was carried out with SSH connections.
DGX server specs:
• 16 NVidia Tesla V100 GPUs
• 28TB of disk, all SSD
• two 24-core Intel Xeon 8168 Platinum 2.7GHz CPUs
• 1.5TB of DDR4-2666 System Memory
• Runs the CentOS 7 Linux operating system
Overall compute power:
• Each V100 NVidia Tesla card has 5,120 CUDA Cores and 640 Tensor Cores
• This gives each16-V100 DGX server a total of 81,920 CUDA cores and 10,240 Tensor cores

## Data Table for DGX Results

| Num of Trials | Blocksize | Performance (Megatrials/second) | Probability |
|---------------|-----------|--------------------------------|-------------|
| 1024          | 8         | 30.3030                        | 27.73       |
| 1024          | 32        | 31.2500                        | 26.07       |
| 1024          | 64        | 29.4118                        | 25.68       |
| 1024          | 128       | 30.3030                        | 25.78       |
| 4096          | 8         | 117.6471                       | 26.32       |
| 4096          | 32        | 117.6471                       | 26.78       |
| 4096          | 64        | 121.2121                       | 28.86       |
| 4096          | 128       | 121.2121                       | 26.25       |
| 16384         | 8         | 444.4444                       | 26.57       |
| 16384         | 32        | 470.5882                       | 27.29       |
| 16384         | 64        | 470.5882                       | 26.43       |
| 16384         | 128       | 470.5882                       | 26.68       |
| 65536         | 8         | 1389.4165                      | 26.77       |
| 65536         | 32        | 1737.0653                      | 26.71       |
| 65536         | 64        | 2085.5397                      | 27.04       |
| 65536         | 128       | 1858.4392                      | 26.93       |
| 262144        | 8         | 2832.6419                      | 26.87       |
| 262144        | 32        | 4686.4988                      | 26.84       |
| 262144        | 64        | 4815.9905                      | 26.95       |
| 262144        | 128       | 4710.7534                      | 26.87       |
| 1048576       | 8         | 4000.4885                      | 26.85       |
| 1048576       | 32        | 9489.7191                      | 26.98       |
| 1048576       | 64        | 9691.8074                      | 26.88       |
| 1048576       | 128       | 9660.3774                      | 26.88       |
| 2097152       | 8         | 4342.7208                      | 26.88       |
| 2097152       | 32        | 11153.1653                     | 26.89       |
| 2097152       | 64        | 11876.7667                     | 26.88       |
| 2097152       | 128       | 12093.7441                     | 26.91       |


## Graphs

<img width="932" alt="Screenshot 2023-10-22 at 11 26 16 AM" src="https://github.com/lucasrouchy/CUDA_blocksize_perfromance_testing/assets/55973521/ce563cd0-22a2-4be1-949e-840bd6292eb9">

<img width="1136" alt="Screenshot 2023-10-22 at 11 26 54 AM" src="https://github.com/lucasrouchy/CUDA_blocksize_perfromance_testing/assets/55973521/580f4186-0c52-4233-bbf9-8646c1788d9b">

