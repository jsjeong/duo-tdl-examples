
# Milk-V Duo series TDL-SDK examples
English | [简体中文](./README-zh.md)

## Introduction to TDL-SDK

Cvitek provides TDL integration algorithms to reduce the time required for application development. This architecture realizes the algorithm required by TDL, including its pre and post processing, and provides a unified and convenient programming interface.

Reference Links: [https://github.com/sophgo/tdl_sdk](https://github.com/sophgo/tdl_sdk)

## Introduction to this repository

This repository is based on [tdl_sdk](https://github.com/sophgo/tdl_sdk) and is created for the Milk-V Duo series development board, so that users can use each example separately for verification testing or develop related applications.

**The examples in this repository need to be tested in the V2 version of the firmware, image address:** [Relese](https://github.com/milkv-duo/duo-buildroot-sdk-v2/releases)。

## Development Environment

Use a Ubuntu system, `Ubuntu 22.04 LTS` is recommended.

You can also use an Ubuntu system in a virtual machine, Ubuntu installed in WSL in Windows, or an Ubuntu system based on Docker.

Install the compilation dependent tools:
```
sudo apt-get install wget git make
```

Get the repository code:
```
git clone https://github.com/milkv-duo/duo-tdl-examples.git
```

## Compile Example

The following takes the compilation of face detection program as an example to introduce the compilation process.

Enter the code directory:
```
cd duo-tdl-examples
```

Prepare the compilation environment:
```
source envsetup.sh
```
The first time you source it, the required toolchain will be automatically downloaded. The downloaded directory is named `host-tools`. When source it next time, if the directory already exists, it will not be downloaded again.

In the source process, you need to enter the required compilation target as prompted:
```
Select Product:
1. Duo (CV1800B)
2. Duo256M (SG2002) or DuoS (SG2000)
```
If the target board is Duo, select `1`, if the target board is Duo256M or DuoS, select `2`. Since Duo256M and DuoS support both RISCV and ARM architectures, you need to continue to select as prompted:
```
Select Arch:
1. ARM64
2. RISCV64
Which would you like:
```
If the test program needs to be run on a ARM system, select `1`, if it is an RISCV system, select `2`.

**In the same terminal, you only need to source it once.**

The sample program for face detection is `sample_vi_fd`. Enter the sample_vi_fd directory:
```
cd sample_vi_fd
```
Compile using the `make` command:
```
make
```
Send the `sample_vi_fd` program generated in the current directory to the Duo series board via `scp` or other methods for testing. If you need to clear the generated program, you can execute `make clean` to clear it.

Programs directly transferred to the Duo development board through `scp` may not have execution permissions. You need to add executable permissions in the development board's system using the `chmod` command:
```
chmod +x sample_vi_fd
```

The command to test the face detection example in DuoS is `sample_vi_fd + face detection model file`:
```
./sample_vi_fd /mnt/cvimodel/scrfd_768_432_int8_1x.cvimodel
```
At this time, point the camera at the face, and the terminal log will print the number of faces currently detected. If you need to preview the video screen in real time on a computer, please refer to [Face Detection Documentation](https://milkv.io/docs/duo/application-development/tdl-sdk/tdl-sdk-face-detection).


## Examples Documentation

For more examples and detailed instructions, please refer to the [Milk-V Documentation](https://milkv.io/docs/duo/application-development/tdl-sdk/tdl-sdk-introduction).

## Model support list

### TDL-SDK Model Data Types

[https://doc.sophgo.com/cvitek-develop-docs/master/docs_latest_release/CV180x_CV181x/en/01.software/TPU/TDL_SDK_Software_Development_Guide/build/html/6_Data_Types.html](https://doc.sophgo.com/cvitek-develop-docs/master/docs_latest_release/CV180x_CV181x/en/01.software/TPU/TDL_SDK_Software_Development_Guide/build/html/6_Data_Types.html)

### TDK-SDK Model Download

[https://github.com/sophgo/tdl_models/tree/main](https://github.com/sophgo/tdl_models/tree/main)

## Reference Documentation

<table>
<thead>
  <tr>
    <td>Chinese Version(中文版)</td>
    <td colspan="2">格式</td>
    <td>English Version</td>
    <td colspan="2">Format</td>
  </tr>
</thead>
<tbody>
  <tr>
    <td>深度学习SDK软件开发指南</td>
    <td><a href="http://doc.sophgo.com/cvitek-develop-docs/master/docs_latest_release/CV180x_CV181x/zh/01.software/TPU/TDL_SDK_Software_Development_Guide/build/html/index.html">html</a></td>
    <td><a href="https://doc.sophgo.com/cvitek-develop-docs/master/docs_latest_release/CV180x_CV181x/zh/01.software/TPU/TDL_SDK_Software_Development_Guide/build/TDLSDKSoftwareDevelopmentGuide_zh.pdf">pdf</a></td>
    <td>TDL SDK Software Development Guide</td>
    <td><a href="http://doc.sophgo.com/cvitek-develop-docs/master/docs_latest_release/CV180x_CV181x/en/01.software/TPU/TDL_SDK_Software_Development_Guide/build/html/index.html">html</a></td>
    <td><a href="http://doc.sophgo.com/cvitek-develop-docs/master/docs_latest_release/CV180x_CV181x/en/01.software/TPU/TDL_SDK_Software_Development_Guide/build/TDLSDKSoftwareDevelopmentGuide_en.pdf">pdf</a></td>
  </tr>
  <tr>
    <td>YOLO系列开发指南</td>
    <td><a href="http://doc.sophgo.com/cvitek-develop-docs/master/docs_latest_release/CV180x_CV181x/zh/01.software/TPU/YOLO_Development_Guide/build/html/index.html">html</a></td>
    <td><a href="http://doc.sophgo.com/cvitek-develop-docs/master/docs_latest_release/CV180x_CV181x/zh/01.software/TPU/YOLO_Development_Guide/build/YOLODevelopmentGuide_zh.pdf">pdf</a></td>
    <td>YOLO Development Guide</td>
    <td><a href="http://doc.sophgo.com/cvitek-develop-docs/master/docs_latest_release/CV180x_CV181x/en/01.software/TPU/YOLO_Development_Guide/build/html/index.html">html</a></td>
    <td><a href="http://doc.sophgo.com/cvitek-develop-docs/master/docs_latest_release/CV180x_CV181x/en/01.software/TPU/YOLO_Development_Guide/build/YOLODevelopmentGuide_en.pdf">pdf</a></td>
  </tr>
</tbody>
</table>

## FAQs

### What is the difference between this repository and the Sophgo TDL SDK repository?

The compilation of the original [tdl_sdk](https://github.com/sophgo/tdl_sdk) repository depends on the buildroot SDK [duo-buildroot-sdk-v2](https://github.com/milkv-duo/duo-buildroot-sdk-v2), and the compilation process is slightly more complicated. This repository separates the sample code from tdl_sdk, so users who only care about AI program development can compile and test directly. The source code of the examples in this repository is consistent with tdl_sdk, and the updates of the relevant code in tdl_sdk will be synchronized regularly.

### Are the dynamic library so files in the libs directory open source?

To simplify the compilation of the sample programs, the libs directory contains the precompiled dynamic library so files that the samples depend on. Most of the source code of these libraries can be found in [tdl_sdk](https://github.com/sophgo/tdl_sdk) and [cvi_mpi](https://github.com/sophgo/cvi_mpi). For the source code files corresponding to each library, please refer to the README file in the libs directory of this repository.
