# Introduction to Compiler Reference Guide

ROCmCC is a Clang/LLVM-based compiler. It is optimized for high-performance computing on AMD GPUs and CPUs and supports various heterogenous programming models such as HIP, OpenMP, and OpenCL.

ROCmCC is made available via two packages: rocm-llvm and rocm-llvm-alt. The differences are shown in this table:

| <b>Table 1. rocm-llvm vs. rocm-llvm-alt</b>|
| rocm-llvm | rocm-llvm-alt |
| ----------- | ----------- |
| Installed by default when ROCm™ itself is installed | An optional package |
| Provides an open-source compiler | Provides an additional closed-source compiler for users interested in additional CPU optimizations not available in rocm-llvm |

For more details, follow this table:

| <b>Table 2. Details Table</b>|
| For | See |
| ----------- | ----------- |
| The latest usage information for AMD GPU |[https://llvm.org/docs/AMDGPUUsage.html](https://llvm.org/docs/AMDGPUUsage.html) |
|Usage information for a specific ROCm release | [https://llvm.org/docs/AMDGPUUsage.html] (https://llvm.org/docs/AMDGPUUsage.html)|
| Source code for rocm-llvm | [https://github.com/RadeonOpenCompute/llvm-project](https://github.com/RadeonOpenCompute/llvm-project) |

## ROCm Compiler Interfaces
ROCm currently provides two compiler interfaces for compiling HIP programs:
- /opt/rocm/bin/hipcc
- /opt/rocm/bin/amdclang++

Both leverage the same LLVM compiler technology with the AMD GCN GPU support; however, they offer a slightly different user experience. The hipcc command-line interface aims to provide a more familiar user interface to users who are experienced in CUDA but relatively new to the ROCm/HIP development environment. On the other hand, amdclang++ provides a user interface identical to the clang++ compiler. It is more suitable for experienced developers who want to directly interact with the clang compiler and gain full control of their application’s build process.

The major differences between hipcc and amdclang++ are listed below:

| <b>Table 3. Differences Between hipcc and amdclang++</b>|
|| Hipcc | amdclang++ |
| ----------- | ----------- | ----------- |
| Compiling HIP source files | Treats all source files as HIP language source files | Enables the HIP language support for files with the “.hip” extension or through the -x hip compiler option |
| Automatic GPU architecture detection | Auto-detects the GPUs available on the system and generates code for those devices when no GPU architecture is specified | Has AMD GCN gfx803 as the default GPU architecture. The --offload-arch compiler option may be used to target other GPU architectures |