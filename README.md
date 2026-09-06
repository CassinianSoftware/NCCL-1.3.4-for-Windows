# NCCL for Windows
Windows buildable version of NVIDIA's NCCL ("Nickel") v1.3.4 library (originally for Linux) for multi-GPU acceleration. Please see https://github.com/NVIDIA/nccl for the latest source files. Note, this version of NCCL is NOT the most current version of the library. 
<h3>Supported Development Environments:</h3>

* Visual Studio 2026 (platform toolset v14.5) & CUDA Computing Toolkit v13.4 (current)  

* Visual Studio 2019 (platform toolset v14.2) & CUDA Computing Toolkit v13.3 (previous)
<h3>Target CUDA Architecture:</h3>
Change this to match your hardware. This build supports Blackwell Ultra (CUDA 12.9 and later, consumer & workstation version of Blackwell): GeForce RTX 5090, RTX 5080, RTX 5070 Ti, RTX 5070, RTX 5060 Ti, RTX PRO 6000 Blackwell (GB202, GB203, GB205, GB206, GB207). For GeForce RTX cards, consider using compute_120a and sm_120a, which adds specialized accelerated features but is not forward compatible; for RTX 5090, RTX 5080, RTX 5070 Ti, RTX 5070, RTX 5060 Ti, and RTX PRO 6000.
<h3>Test Results:</h3>
This version of NCCL has been tested on a Dell Precision T7920 running Windows 11, with 2 NVIDIA GeForce RTX 5060 Ti 16GB GPU cards installed, using the following test apps: all_gather_test.exe, all_reduce_test.exe, broadcast_test.exe, reduce_scatter_test.exe, and reduce-test.exe. There is no guarantee this build of NCCL will function correctly for any particular purpose under Windows.
<h4>reduce_test 67108864 2 (64MB data size, 2 GPUs) results:</h4>
Using devices

Rank  0 uses device  0 [0x73] NVIDIA GeForce RTX 5060 Ti  
Rank  1 uses device  1 [0xa6] NVIDIA GeForce RTX 5060 Ti  

                                                        out-of-place                    in-place
      bytes             N    type      op  root    time  algbw  busbw      res     time  algbw  busbw      res
    67108864      67108864    char     sum    0   11.534   5.82   5.82    0e+00   11.570   5.80   5.80    0e+00
    67108864      67108864    char     sum    1   11.569   5.80   5.80    0e+00   11.617   5.78   5.78    0e+00
    67108864      67108864    char    prod    0   11.482   5.84   5.84    0e+00   11.602   5.78   5.78    0e+00
    67108864      67108864    char    prod    1   11.424   5.87   5.87    0e+00   11.486   5.84   5.84    0e+00
    67108864      67108864    char     max    0   11.588   5.79   5.79    0e+00   16.622   4.04   4.04    0e+00
    67108864      67108864    char     max    1   11.483   5.84   5.84    0e+00   11.523   5.82   5.82    0e+00
    67108864      67108864    char     min    0   11.716   5.73   5.73    0e+00   11.686   5.74   5.74    0e+00
    67108864      67108864    char     min    1   11.768   5.70   5.70    0e+00   11.788   5.69   5.69    0e+00
    67108864      16777216     int     sum    0   11.242   5.97   5.97    0e+00   11.438   5.87   5.87    0e+00
    67108864      16777216     int     sum    1   11.391   5.89   5.89    0e+00   11.437   5.87   5.87    0e+00
    67108864      16777216     int    prod    0   11.491   5.84   5.84    0e+00   11.455   5.86   5.86    0e+00
    67108864      16777216     int    prod    1   11.301   5.94   5.94    0e+00   11.493   5.84   5.84    0e+00
    67108864      16777216     int     max    0   11.470   5.85   5.85    0e+00   11.868   5.65   5.65    0e+00
    67108864      16777216     int     max    1   11.390   5.89   5.89    0e+00   11.455   5.86   5.86    0e+00
    67108864      16777216     int     min    0   11.563   5.80   5.80    0e+00   11.679   5.75   5.75    0e+00
    67108864      16777216     int     min    1   11.386   5.89   5.89    0e+00   11.453   5.86   5.86    0e+00
    67108864      33554432    half     sum    0   11.485   5.84   5.84    0e+00   11.476   5.85   5.85    0e+00
    67108864      33554432    half     sum    1   11.397   5.89   5.89    0e+00   11.661   5.75   5.75    0e+00
    67108864      33554432    half    prod    0   11.507   5.83   5.83    0e+00   11.472   5.85   5.85    0e+00
    67108864      33554432    half    prod    1   11.403   5.89   5.89    0e+00   11.457   5.86   5.86    0e+00
    67108864      33554432    half     max    0   11.500   5.84   5.84    0e+00   12.021   5.58   5.58    0e+00
    67108864      33554432    half     max    1   11.401   5.89   5.89    0e+00   11.444   5.86   5.86    0e+00
    67108864      33554432    half     min    0   11.527   5.82   5.82    0e+00   11.848   5.66   5.66    0e+00
    67108864      33554432    half     min    1   11.539   5.82   5.82    0e+00   11.465   5.85   5.85    0e+00
    67108864      16777216   float     sum    0   11.954   5.61   5.61    0e+00   12.091   5.55   5.55    0e+00
    67108864      16777216   float     sum    1   11.811   5.68   5.68    0e+00   11.671   5.75   5.75    0e+00
    67108864      16777216   float    prod    0   11.464   5.85   5.85    0e+00   11.788   5.69   5.69    0e+00
    67108864      16777216   float    prod    1   11.636   5.77   5.77    0e+00   11.488   5.84   5.84    0e+00
    67108864      16777216   float     max    0   11.476   5.85   5.85    0e+00   11.593   5.79   5.79    0e+00
    67108864      16777216   float     max    1   11.755   5.71   5.71    0e+00   11.802   5.69   5.69    0e+00
    67108864      16777216   float     min    0   11.476   5.85   5.85    0e+00   15.997   4.20   4.20    0e+00
    67108864      16777216   float     min    1   11.425   5.87   5.87    0e+00   11.483   5.84   5.84    0e+00
    67108864       8388608  double     sum    0   11.625   5.77   5.77    0e+00   11.588   5.79   5.79    0e+00
    67108864       8388608  double     sum    1   11.402   5.89   5.89    0e+00   11.436   5.87   5.87    0e+00
    67108864       8388608  double    prod    0   11.474   5.85   5.85    0e+00   11.623   5.77   5.77    0e+00
    67108864       8388608  double    prod    1   11.326   5.93   5.93    0e+00   11.435   5.87   5.87    0e+00
    67108864       8388608  double     max    0   11.459   5.86   5.86    0e+00   16.093   4.17   4.17    0e+00
    67108864       8388608  double     max    1   11.397   5.89   5.89    0e+00   11.481   5.85   5.85    0e+00
    67108864       8388608  double     min    0   11.530   5.82   5.82    0e+00   11.483   5.84   5.84    0e+00
    67108864       8388608  double     min    1   11.426   5.87   5.87    0e+00   11.472   5.85   5.85    0e+00
    67108864       8388608   int64     sum    0   11.498   5.84   5.84    0e+00   11.885   5.65   5.65    0e+00
    67108864       8388608   int64     sum    1   11.403   5.89   5.89    0e+00   11.433   5.87   5.87    0e+00
    67108864       8388608   int64    prod    0   11.543   5.81   5.81    0e+00   11.564   5.80   5.80    0e+00
    67108864       8388608   int64    prod    1   11.554   5.81   5.81    0e+00   11.965   5.61   5.61    0e+00
    67108864       8388608   int64     max    0   11.446   5.86   5.86    0e+00   11.575   5.80   5.80    0e+00
    67108864       8388608   int64     max    1   11.179   6.00   6.00    0e+00   11.474   5.85   5.85    0e+00
    67108864       8388608   int64     min    0   11.447   5.86   5.86    0e+00   11.893   5.64   5.64    0e+00
    67108864       8388608   int64     min    1   11.410   5.88   5.88    0e+00   11.467   5.85   5.85    0e+00
    67108864       8388608  uint64     sum    0   11.489   5.84   5.84    0e+00   11.446   5.86   5.86    0e+00
    67108864       8388608  uint64     sum    1   11.395   5.89   5.89    0e+00   11.446   5.86   5.86    0e+00
    67108864       8388608  uint64    prod    0   11.678   5.75   5.75    0e+00   11.570   5.80   5.80    0e+00
    67108864       8388608  uint64    prod    1   11.402   5.89   5.89    0e+00   11.695   5.74   5.74    0e+00
    67108864       8388608  uint64     max    0   11.492   5.84   5.84    0e+00   11.522   5.82   5.82    0e+00
    67108864       8388608  uint64     max    1   11.403   5.89   5.89    0e+00   11.368   5.90   5.90    0e+00
    67108864       8388608  uint64     min    0   11.460   5.86   5.86    0e+00   11.424   5.87   5.87    0e+00
    67108864       8388608  uint64     min    1   11.184   6.00   6.00    0e+00   11.418   5.88   5.88    0e+00

Out of bounds values : 0 OK  
Avg bus bandwidth    : 5.77463  

<h3>Final Note:</h3>
This Windows build of NCCL v1.34 is intended for use with llama.cpp, to accelerate model performance when running a single model across multiple GPU cards using the "tensor parallel" option for the <b>--split-mode</b> command line argument. See https://github.com/ggml-org/llama.cpp/blob/master/docs/multi-gpu.md for further details. You must build llama.cpp to support NCCL, and make certain the environment variables NCCL_LIBRARY and NCCL_INCLUDE_DIR are set. If NCCL cannot be located at build time, you will see the message: "Warning: NCCL not found, performance for multiple CUDA GPUs will be suboptimal."
