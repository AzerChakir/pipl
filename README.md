# PIPL — Parallel Image Processing Lab

**A modular C++ laboratory for image processing, parallel computing, and CPU/GPU performance benchmarking.**

![C++](https://img.shields.io/badge/C++-17-blue?logo=cplusplus)
![CMake](https://img.shields.io/badge/CMake-Build_System-064F8C?logo=cmake)
![OpenMP](https://img.shields.io/badge/OpenMP-Parallel_Computing-5586A4)
![OpenCL](https://img.shields.io/badge/OpenCL-Heterogeneous_Computing-ED6C00)
![CUDA](https://img.shields.io/badge/CUDA-NVIDIA_GPU-76B900?logo=nvidia)
![Status](https://img.shields.io/badge/Status-In_Development-orange)

---

## Overview

PIPL (Parallel Image Processing Lab) is an educational and experimental C++ project designed to explore parallel computing through practical image processing applications.

The project aims to implement common image processing algorithms using different execution strategies, ranging from traditional sequential CPU execution to parallel CPU processing and GPU acceleration.

By comparing multiple implementations of the same algorithms, PIPL provides a practical environment for studying parallelization techniques, computational efficiency, memory management, and hardware performance.

The main objective is not only to process images, but also to understand **how, when, and why parallel computing improves performance.**

## Objectives

- Implement fundamental image processing algorithms from scratch.
- Establish a sequential CPU implementation as a performance baseline.
- Explore CPU parallelization using OpenMP.
- Investigate heterogeneous computing using OpenCL.
- Develop GPU-accelerated implementations using NVIDIA CUDA.
- Compare execution time, speedup, efficiency, and scalability.
- Study memory transfers, workload distribution, and parallelization overhead.
- Validate the correctness of parallel implementations against sequential results.
- Produce reproducible benchmark results and performance visualizations.

## Technology Stack

| Technology | Purpose |
|---|---|
| C++17 | Core implementation |
| GCC / G++ | Compilation |
| CMake | Build configuration |
| Ninja | Build system |
| OpenMP | Shared-memory CPU parallelism |
| OpenCL | Cross-platform heterogeneous computing |
| CUDA | NVIDIA GPU programming |
| libpng / libjpeg | Image decoding and encoding |
| Python / Matplotlib | Benchmark analysis and visualization |
| Git / GitHub | Version control |

## Target Hardware

The development environment includes:

- **CPU:** AMD Ryzen 7 7840HS (8 cores / 16 threads)
- **Integrated GPU:** AMD Radeon 780M
- **Dedicated GPU:** NVIDIA GeForce RTX 3050 Laptop GPU (6 GB VRAM)
- **Operating System:** Ubuntu 26.04 LTS

The project will use the available hardware to investigate different parallel execution models. Actual backend availability will depend on the installed drivers, compilers, libraries, and runtime support.

## Image Processing Algorithms

The planned algorithm implementations include:

| Algorithm | Description | Status |
|---|---|---|
| Grayscale | RGB-to-grayscale conversion | Planned |
| Gaussian Blur | Image smoothing using Gaussian convolution | Planned |
| Sobel Edge Detection | Gradient-based edge detection | Planned |
| Histogram Equalization | Contrast enhancement | Planned |
| Sharpening | Image detail enhancement | Planned |
| Median Filter | Non-linear noise reduction | Planned |
| Image Resizing | Image scaling and interpolation | Planned |
| Thresholding | Binary image segmentation | Planned |

Each algorithm will progressively receive multiple backend implementations.

## Execution Backends

PIPL is designed around a modular execution architecture.

| Backend | Description |
|---|---|
| Sequential CPU | Reference implementation using a single execution thread |
| OpenMP | Multi-threaded CPU execution |
| OpenCL | Heterogeneous execution across supported devices |
| CUDA | NVIDIA GPU-accelerated execution |

The sequential implementation serves as the correctness and performance reference for subsequent implementations.

## Architecture

The project follows a modular architecture separating image processing algorithms, execution backends, image I/O, and benchmarking.

```text
                 PIPL Application
                        |
                Benchmark Controller
                        |
                Image Processing API
                        |
              Processing Algorithms
                        |
          +-------------+-------------+
          |             |             |
       Sequential     OpenMP       GPU APIs
          CPU           CPU            |
                                   +----+----+
                                   |         |
                                 OpenCL    CUDA
                                   |         |
                              Supported  NVIDIA GPU
                               Devices
                        |
                Validation & Benchmarking
                        |
                 CSV / Performance Data
                        |
                 Analysis & Visualization
```

## Project Structure

```text
PIPL/
├── CMakeLists.txt
├── include/
├── src/
│   ├── main.cpp
│   ├── image_io/
│   ├── algorithms/
│   ├── backends/
│   │   ├── sequential/
│   │   ├── openmp/
│   │   ├── opencl/
│   │   └── cuda/
│   └── benchmark/
├── kernels/
│   ├── opencl/
│   └── cuda/
├── tests/
├── images/
├── results/
├── scripts/
└── docs/
```

## Performance Evaluation

An important part of PIPL is the quantitative evaluation of parallel implementations.

The following metrics will be investigated:

**Execution Time**

The time required to execute an image processing operation.

**Speedup**


>S(p) = T_sequential / T_p


**Parallel Efficiency**


>E(p) = S(p) / p


**Amdahl's Law**


>S(p) = 1 / ((1 - f) + f/p)


Where:

- T_sequential: sequential execution time.
- T_p: execution time using p processing units.
- f: parallelizable fraction of the workload.
- p: number of processing units.
GPU experiments will distinguish between host-to-device transfer time, kernel execution time, device-to-host transfer time, and total execution time.

Experiments will investigate:

- Different image resolutions.
- Different thread counts.
- Different convolution kernel sizes.
- OpenMP scheduling strategies.
- GPU memory transfers and kernel execution overhead.
- Scalability and parallelization limits.

## Building the Project

### Requirements

- Ubuntu Linux
- GCC or Clang with C++17 support
- CMake
- Ninja
- Git

### Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/pipl.git
cd pipl
```

### Configure

```bash
cmake -S . -B build -G Ninja -DCMAKE_BUILD_TYPE=Release
```

### Build

```bash
cmake --build build
```

### Run

```bash
./build/pipl
```

Additional dependencies and backend-specific build requirements will be documented as their implementations are introduced.

## Development Roadmap

- [x] Initialize project structure.
- [x] Configure the C++ development environment.
- [x] Configure the initial CMake build.
- [x] Initialize local Git repository and GitHub remote.
- [ ] Implement image representation and memory management.
- [ ] Implement image loading and saving.
- [ ] Develop sequential image processing algorithms.
- [ ] Implement automated correctness tests.
- [ ] Introduce OpenMP parallelization.
- [ ] Develop OpenCL kernels.
- [ ] Develop CUDA kernels.
- [ ] Implement benchmarking and performance analysis.
- [ ] Analyze scalability and optimization opportunities.
- [ ] Publish experimental results and documentation.

## Additional Learning Objectives

Beyond image processing, PIPL will serve as a practical environment for exploring concepts related to:

- Parallel programming models.
- CPU and GPU architectures.
- Cache behavior and memory hierarchy.
- Data parallelism and workload partitioning.
- Synchronization and race conditions.
- Real-time scheduling fundamentals.
- Performance profiling and optimization.

A separate real-time scheduling simulator may be developed to investigate scheduling algorithms such as Rate Monotonic (RM) and Earliest Deadline First (EDF). These experiments will remain independent of GPU benchmarking and will not be presented as hard real-time guarantees.

## Project Philosophy

PIPL is developed incrementally, with an emphasis on understanding the underlying mechanisms rather than relying exclusively on high-level libraries.

The project prioritizes:

- Modular and maintainable code.
- Correctness before optimization.
- Measurable performance improvements.
- Reproducible experiments.
- Clear technical documentation.
- Understanding hardware-software interactions.

---

**PIPL — Parallel Image Processing Lab**

*Exploring parallelism. Understanding performance. Learning through implementation.*
