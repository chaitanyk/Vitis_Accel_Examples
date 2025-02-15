Host Examples
==================================
OpenCL host code for optimized interfacing with Xilinx Devices.

 __Examples Table__ 

Example        | Description           | Key Concepts / Keywords 
---------------|-----------------------|-------------------------
[concurrent_kernel_execution/][]|This example will demonstrate how to use multiple and out of order command queues to simultaneously execute multiple kernels on an FPGA.|__Key__ __Concepts__<br> - Concurrent execution<br> - Out of Order Command Queues<br> - Multiple Command Queues<br>__Keywords__<br> - CL_QUEUE_OUT_OF_ORDER_EXEC_MODE_ENABLE<br> - setCallback
[copy_buffer/][]|This Copy Buffer example demonstrate how one buffer can be copied from another buffer.|__Key__ __Concepts__<br> - Copy Buffer<br>__Keywords__<br> - cl::CommandQueue<br> - enqueueCopyBuffer<br> - enqueueWriteBuffer<br> - enqueueReadBuffer<br> - enqueueMigrateMemObjects
[data_transfer/][]|This example illustrates several ways to use the OpenCL API to transfer data to and from the FPGA|__Key__ __Concepts__<br> - OpenCL API<br> - Data Transfer<br> - Write Buffers<br> - Read Buffers<br> - Map Buffers<br> - Async Memcpy<br>__Keywords__<br> - enqueueWriteBuffer<br> - enqueueReadBuffer<br> - enqueueMapBuffer<br> - enqueueUnmapMemObject<br> - enqueueMigrateMemObjects
[debug_profile/][]|This is simple example of vector addition and printing profile data (wall clock time taken between start and stop). It also dump a waveform file which can be reloaded to vivado to see the waveform. Run command 'vivado -source ./scripts/open_waveform.tcl -tclargs <device_name>-<kernel_name>.<target>.<device_name>.wdb' to launch waveform viewer. User can also update batch to gui in xrt.ini file to see the live waveform while running application.|__Key__ __Concepts__<br> - Use of Profile API<br> - Waveform Dumping and loading<br>
[device_only_buffer/][]|This example will demonstrate how to create buffers in global memory which are not mapped to host. The device only memory allocation is done through the host code. The kernel can read data from device memory and write result to device memory.|__Key__ __Concepts__<br> - Device only buffer<br>__Keywords__<br> - CL_MEM_HOST_NO_ACCESS
[device_query/][]|This Example prints the OpenCL properties of the platform and its devices using OpenCL CPP APIs. It also displays the limits and capabilities of the hardware.|__Key__ __Concepts__<br> - OpenCL API<br> - Querying device properties<br>
[errors/][]|This example discuss the different reasons for errors in OpenCL and how to handle them at runtime.|__Key__ __Concepts__<br> - OpenCL API<br> - Error handling<br>__Keywords__<br> - CL_SUCCESS<br> - CL_DEVICE_NOT_FOUND<br> - CL_DEVICE_NOT_AVAILABLE
[errors_cpp/][]|This example discuss the different reasons for errors in OpenCL C++ and how to handle them at runtime.|__Key__ __Concepts__<br> - OpenCL C++ API<br> - Error handling<br>__Keywords__<br> - CL_SUCCESS<br> - CL_DEVICE_NOT_FOUND<br> - CL_DEVICE_NOT_AVAILABLE<br> - CL_INVALID_VALUE<br> - CL_INVALID_KERNEL_NAME<br> - CL_INVALID_BUFFER_SIZE
[hbm_bandwidth/][]|This is a HBM bandwidth check design. Design contains 3 compute units of a kernel which has access to all HBM pseudo-channels (0:31). Host application allocate buffer into all HBM banks and run these 3 compute units concurrently and measure the overall bandwidth between Kernel and HBM Memory.|
[hbm_bandwidth_pseudo_random/][]|This is a HBM bandwidth example using a pseudo random 1024 bit data access pattern to mimic Ethereum Ethash workloads. The design contains 3 compute units of a kernel, reading 1024 bits from a pseudo random address in each of 2 pseudo channels and writing the results of a simple mathematical operation to a pseudo random address in 2 other pseudo channels. To maximize bandwidth the pseudo channels are used in  P2P like configuration - See https://developer.xilinx.com/en/articles/maximizing-memory-bandwidth-with-vitis-and-xilinx-ultrascale-hbm-devices.html for more information on HBM memory access configurations. The host application allocates buffers in 12  HBM banks and runs the compute units concurrently to measure the overall bandwidth between kernel and HBM Memory.|__Key__ __Concepts__<br> - High Bandwidth Memory<br> - Multiple HBM Pseudo-channels<br> - Random Memory Access<br> - Linear Feedback Shift Register<br>__Keywords__<br> - HBM<br> - XCL_MEM_TOPOLOGY<br> - cl_mem_ext_ptr_t
[hbm_large_buffers/][]|This is a simple example of vector addition to describe how HBM pseudo-channels can be grouped to handle buffers larger than 256 MB.|__Key__ __Concepts__<br> - High Bandwidth Memory<br> - Multiple HBM Pseudo-channel Groups<br>__Keywords__<br> - HBM
[hbm_rama_ip/][]|This is host application to test HBM interface bandwidth for buffers > 256 MB with pseudo random 1024 bit data access pattern, mimicking Ethereum Ethash workloads. Design contains 4 compute units of Kernel, 2 with and 2 without RAMA IP. Each compute unit reads 1024 bits from a pseudo random address in each of 2 pseudo channel groups and writes the results of a simple mathematical operation to a pseudo random address in 2 other pseudo channel groups. Each buffer is 1 GB large requiring 4 HBM banks. Since the first 2 CUs requires 4 buffers each and are then used again by the other 2 CUs, the .cfg file is allocating the buffers to all the 32 HBM banks.  The host application runs the compute units concurrently to measure the overall bandwidth between kernel and HBM Memory.|__Key__ __Concepts__<br> - High Bandwidth Memory<br> - Multiple HBM Pseudo-channels<br> - Random Memory Access<br> - Linear Feedback Shift Register<br> - RAMA IP<br>__Keywords__<br> - HBM<br> - ra_master_interface
[hbm_simple/][]|This is a simple example of vector addition to describe how to use HLS kernels with HBM (High Bandwidth Memory) for achieving high throughput.|__Key__ __Concepts__<br> - High Bandwidth Memory<br> - Multiple HBM pseudo-channels<br>__Keywords__<br> - HBM<br> - XCL_MEM_TOPOLOGY<br> - cl_mem_ext_ptr_t
[host_global_bandwidth/][]|Host to global memory bandwidth test|
[iops_test/][]|This is simple test design to measure Input/Output Operations per second. In this design, a simple kernel is enqueued many times and measuring overall IOPS.|__Key__ __Concepts__<br> - Input/Output Operations per second<br>__Keywords__<br> - CL_QUEUE_OUT_OF_ORDER_EXEC_MODE_ENABLE
[mult_compute_units/][]|This is simple Example of Multiple Compute units to showcase how a single kernel can be instantiated into Multiple compute units. Host code will show how to use multiple compute units and run them concurrently.|__Key__ __Concepts__<br> - Multiple Compute Units<br>__Keywords__<br> - nk
[multiple_cus_asymmetrical/][]|This is simple example of vector addition to demonstrate how to connect each compute unit to different banks and how to use these compute units in host applications|__Key__ __Concepts__<br> - Multiple Compute Units<br>
[overlap/][]|This examples demonstrates techniques that allow user to overlap Host(CPU) and FPGA computation in an application. It will cover asynchronous operations and event object.|__Key__ __Concepts__<br> - OpenCL API<br> - Synchronize Host and FPGA<br> - Asynchronous Processing<br> - Events<br> - Asynchronous memcpy<br>__Keywords__<br> - cl_event<br> - cl::CommandQueue<br> - CL_QUEUE_OUT_OF_ORDER_EXEC_MODE_ENABLE<br> - enqueueMigrateMemObjects
[p2p_bandwidth/][]|This is simple example to test data transfer between SSD and FPGA.|__Key__ __Concepts__<br> - P2P<br> - SmartSSD<br> - XDMA<br>__Keywords__<br> - XCL_MEM_EXT_P2P_BUFFER<br> - pread<br> - pwrite
[p2p_fpga2fpga/][]|This is simple example to explain P2P transfer between two FPGA devices.|__Key__ __Concepts__<br> - P2P<br> - Multi-FPGA Execution<br> - XDMA<br>__Keywords__<br> - XCL_MEM_EXT_P2P_BUFFER
[p2p_fpga2fpga_bandwidth/][]|This is simple example to explain performance bandwidth for P2P transfer between two FPGA devices.|__Key__ __Concepts__<br> - P2P<br> - Multi-FPGA Execution<br> - XDMA<br>__Keywords__<br> - XCL_MEM_EXT_P2P_BUFFER
[p2p_overlap_bandwidth/][]|This is simple example to test Synchronous and Asyncronous data transfer between SSD and FPGA.|__Key__ __Concepts__<br> - P2P<br> - SmartSSD<br> - XDMA<br>__Keywords__<br> - XCL_MEM_EXT_P2P_BUFFER<br> - pread<br> - pwrite
[p2p_simple/][]|This is simple example of vector increment to describe P2P between FPGA and NVMe SSD.|__Key__ __Concepts__<br> - P2P<br> - NVMe SSD<br> - SmartSSD<br>__Keywords__<br> - XCL_MEM_EXT_P2P_BUFFER<br> - pread<br> - pwrite<br> - O_DIRECT<br> - O_RDWR
[slave_bridge_bandwidth/][]|This is slave bridge bandwidth example to describe host memory and kernel bandwidth test.|__Key__ __Concepts__<br> - slave bridge<br> - bandwidth<br> - address translation unit<br>__Keywords__<br> - XCL_MEM_EXT_HOST_ONLY<br> - HOST[0]
[slave_bridge_copy_buffer/][]|This is simple slave bridge example to describe how host-only memory can be copied to device-only memory and vice-versa.|__Key__ __Concepts__<br> - slave bridge<br>__Keywords__<br> - XCL_MEM_EXT_HOST_ONLY<br> - CL_MEM_HOST_NO_ACCESS<br> - enqueueCopyBuffer
[slave_bridge_copy_kernel/][]|This is a Slave Bridge Example to describe how data can be copied between host-only buffer and device-only buffer using User Copy Kernel.|__Key__ __Concepts__<br> - slave bridge<br>__Keywords__<br> - XCL_MEM_EXT_HOST_ONLY<br> - CL_MEM_HOST_NO_ACCESS<br> - enqueueMapBuffer
[slave_bridge_simple/][]|This is simple slave bridge example to describe how a user kernel can access the host memory. The host memory allocation is done through the host code. The kernel reads data from host memory and writes result to host memory.|__Key__ __Concepts__<br> - slave bridge<br> - address translation unit<br>__Keywords__<br> - XCL_MEM_EXT_HOST_ONLY<br> - HOST[0]
[streaming_free_running_k2k/][]|This is simple example which demonstrate how to use and configure a free running kernel.|__Key__ __Concepts__<br> - Free Running Kernel<br>__Keywords__<br> - ap_ctrl_none<br> - stream_connect
[streaming_k2k_mm/][]|This is a simple kernel to kernel streaming Vector Add and Vector Multiply C Kernel design with 2 memory mapped input to kernel 1, 1 Stream output from kernel 1 to input of kernel 2, 1 memory mapped input to kernel 2, and 1 memory mapped output that demonstrates on how to process a stream of data for computation between two kernels. This design also illustrates how to set FIFO depth for AXIS connections i.e. for the stream connecting the two kernels|__Key__ __Concepts__<br> - Read/Write Stream<br> - Create/Release Stream<br> - AXIS FIFO depth<br>__Keywords__<br> - stream_connect
[streaming_reg_access/][]|This is simple example which demonstrate streaming free-running kernel with scalar input and output.|__Key__ __Concepts__<br> - Free Running Kernel<br>__Keywords__<br> - xclRegRead<br> - xclRegWrite

[.]:.
[concurrent_kernel_execution/]:concurrent_kernel_execution/
[copy_buffer/]:copy_buffer/
[data_transfer/]:data_transfer/
[debug_profile/]:debug_profile/
[device_only_buffer/]:device_only_buffer/
[device_query/]:device_query/
[errors/]:errors/
[errors_cpp/]:errors_cpp/
[hbm_bandwidth/]:hbm_bandwidth/
[hbm_bandwidth_pseudo_random/]:hbm_bandwidth_pseudo_random/
[hbm_large_buffers/]:hbm_large_buffers/
[hbm_rama_ip/]:hbm_rama_ip/
[hbm_simple/]:hbm_simple/
[host_global_bandwidth/]:host_global_bandwidth/
[iops_test/]:iops_test/
[mult_compute_units/]:mult_compute_units/
[multiple_cus_asymmetrical/]:multiple_cus_asymmetrical/
[overlap/]:overlap/
[p2p_bandwidth/]:p2p_bandwidth/
[p2p_fpga2fpga/]:p2p_fpga2fpga/
[p2p_fpga2fpga_bandwidth/]:p2p_fpga2fpga_bandwidth/
[p2p_overlap_bandwidth/]:p2p_overlap_bandwidth/
[p2p_simple/]:p2p_simple/
[slave_bridge_bandwidth/]:slave_bridge_bandwidth/
[slave_bridge_copy_buffer/]:slave_bridge_copy_buffer/
[slave_bridge_copy_kernel/]:slave_bridge_copy_kernel/
[slave_bridge_simple/]:slave_bridge_simple/
[streaming_free_running_k2k/]:streaming_free_running_k2k/
[streaming_k2k_mm/]:streaming_k2k_mm/
[streaming_reg_access/]:streaming_reg_access/
