<H2>Installation Instructions</H2>
To build and use <b>NCCL 1.3.4</b> on Windows, you will need to perform the following steps. As a side note, we are using CUDA 13.4 and Visual Studio 2026 Pro on Windows 11 Pro for all of our testing (other CUDA versions, such as 12.x and 13.x should also work).

<H3>1. Install the NVIDIA CUDA Libraries</H3>
Install the NVIDIA CUDA 13.4 Toolkit for Windows from https://developer.nvidia.com/cuda-downloads. 

<H3>2. Building NCCL 1.3.4</H3>

** IMPORTANT **
All NCCL builds are 64-bit builds and are only usable by 64-bit applications.

The NCCL solution is configured to build the Debug and Release versions of NCCL using the specified version of CUDA. The "windows/nccl_v134-c134.sln" solution targets the following NCCL build:

* nccl_v134-c134.vcxproj - targets CUDA 13.4 (requires CUDA 13.4 to be installed)
* Note: Visual Studio 2026 is the current build version.

If you wish to target a different version of CUDA, other than 13.4, you will need to update the Build Customization Files settings in Visual Studio (under Project/Build Customizations...).

The resulting DLLs from the build are placed into either the "NCCL\windows\x64\Release\libs" or "NCCL\windows\x64\Debug\libs" folder, depending
on your build type. Each resulting DLL file name is appended with the CUDA version that it targets; for example the CUDA 13.4 version is named "nccl-x64_v134-c134.dll" (for the Release version).

The resulting EXE's for testing are placed into either the "NCCL\windows\x64\Release\bin" or "NCCL\windows\x64\Debug\bin" folder, depending on your build type. The following test executables are built:

* all reduce_test.exe
* broadcast_test.exe
* reduce_scatter_test.exe
* reduce_test.exe

Note, the build also copies the required "cudart64_xxx.dll" into the same directory where the 'xxx' corresponds to the version of CUDA targeted. So for example, when targeting CUDA 13.4, the "cudart64_13.dll" is copied into the directory.

<H4>Usage:</H4>

The <b>nccl.h</b> file located "NCCL\src" defines the main entry points into the "nccl-x64_v134-cxxx.dll" library, several of which are described as follows:

* ncclCommInitRank - Creates a new communicator (multi process version).
* ncclCommInitAll - Creates a clique of communicators.
* ncclCommDestroy - Frees resources associated with communicator object.
* ncclAllReduce - Reduces data arrays of length count in sendbuff using op operation, and leaves identical copies of result on each GPUs recvbuff.
* ncclBcast - Copies count values from root to all other devices.
* ncclGetErrorString - Returns nice error message.

For more function and parameter descriptions and format, callable by the C language, please see <b>nccl.h</b>.

For more information on programming DLL's in Windows, see https://docs.microsoft.com/en-us/windows/win32/dlls/run-time-dynamic-linking.
