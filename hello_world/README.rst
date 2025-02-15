Hello World (HLS C/C++ Kernel)
==============================

This is simple example of vector addition to describe how to use HLS kernels in Vitis Environment.

**KEY CONCEPTS:** HLS C Kernel, OpenCL Host APIs

**KEYWORDS:** gmem, #pragma HLS INTERFACE, m_axi, s_axilite

EXCLUDED PLATFORMS
------------------

Platforms containing following strings in their names are not supported for this example :

::

   nodma

DESIGN FILES
------------

Application code is located in the src directory. Accelerator binary files will be compiled to the xclbin directory. The xclbin directory is required by the Makefile and its contents will be filled during compilation. A listing of all the files in this example is shown below

::

   src/host.cpp
   src/vadd.cpp
   
COMMAND LINE ARGUMENTS
----------------------

Once the environment has been configured, the application can be executed by

::

   ./hello_world <vadd XCLBIN>

DETAILS
-------

This example a simple hello world example to explain the Host and Kernel
code structure. Here a simple ``vadd`` kernel is used to explain the
same.

Vitis kernel can have one s_axilite interface which will be used by host
application to configure the kernel. All the global memory access arguments are associated to m_axi(AXI
Master Interface). All these settings are automatically done by Vitis. Multiple interfaces can be
created based on the requirements. For example when multiple memory
accessing arguments need access to global memory simultaneously, user
can create multiple master interfaces and can connect to different
arguments.

Rather than reading individual items for addition, local buffers are
created in kernel local memory and multiple items are read in a single
burst. This is done to achieve low memory access latency and also for
efficient use of bandwidth provided by the m_axi interface.

Similarly, results are stored in a buffer and are written to global
memory in a burst. The for loops used have the following requirements to
implement burst read/write:

-  Pipeline the loop : Loop pipeline must have ``II`` (Initiation
   interval) = 1

-  contiguous memory : Memory addresses for read/write should be
   contiguous.

.. code:: cpp

       read1: for (int j = 0 ; j < chunk_size ; j++){
           #pragma HLS PIPELINE II=1
               v1_buffer[j] = in1[i + j];
           }
       write: for (int j = 0 ; j < chunk_size ; j++){
           #pragma HLS PIPELINE II=1
               out_r[i + j] = vout_buffer[j];
           }    

For more comprehensive documentation, `click here <http://xilinx.github.io/Vitis_Accel_Examples>`__.