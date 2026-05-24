# Synchronous_FIFO

This project is a part of IEEE NITK's Envision Project Program and I completed it under the mentorship of my mentors Sai Easwar,Aarav Balaji and AkashManjolil.

1. What is a Synchronous FIFO and why do we need it?
	A Synchronous FIFO(First In,First Out) buffer is a digital memory buffer in which data is read out in the same order as it is written into thebuffer.Both the "read" and "write" operation use the same clock cycle and hence it is called "Synchronous".For better understanding,the FIFO buffer can be understood as a queue at a ticketing counter.The "reading" operation can be understood as a person receiving his/her ticket and the "write" operation can be understood as another person joining the queue.As the first person in the queue receives his/her ticket, he/she leaves the queue and the next person thus becomes the first in the queue.A similar thing happens with data in a FIFO buffer where the data is analogus to people in the queue.

	Synchronous FIFO buffers are used widely in modern digital systems and electonics.Some of its applications are:
	a)Data buffering between modules.
	b)Systems which require high speed data transfer.
	c)UART/Serial Communication.
	d)Packet queues in Netwroking and many more applications.

2. Basic structure of the Synchronous FIFO buffer-
	The Synchronous FIFO buffer contains 5 input ports namely- clk, write enable, read enable, reset, data_input.The data to be input can be of any width like 8,16,32,64 bits and the FIFO buffer can typically store 8,16,32,64 or more of such input data depending upon the use case.
Data can be written into the buffer only when"write enable" is HIGH(1) and written data can only be read when the"read enable" is HIGH(1).All the 
operations happen at the positive or the rising edge of the clock(clk) given to the buffer.If the "reset" pin is HIGH(1) all the data written into thebuffer is cleared and the buffer becomes empty.
	The buffer comprises of 3 output ports namely- full_flag,empty_flag and data_out.The width of data_out is same as the width of data_in.
The "full_flag" and "empty_flag" are rasied when the buffer has reached its full capacity or has no data writeen in it respectively.For writing data into the buffer,the full_flag must be LOW that is the buffer must not be full.Similarly for data to be read out of the buffer,the empty_flag must be 
LOW that is the buffer must not be empty.

3. Verilog Code- 
	The code is divided into 4 seperate modules namely-memory_module,write_module,read_module and top_module.Below is the brief explaination of 
each of the modules.

	a)Memory module-This is the most basic module which consists of the wrt_ptr and rd_ptr and the initialisation of the buffer.It points to the 
location where data is to be written or from where data is to be read and thus increments the wrt_ptr and rd_ptr accordingly.

	b)Write module-This module contains the logic for writing data into the buffer and the logic of full_flag.For a buffer with "n" data slots,
the address of each slot can be taken as a "n+1" bit number to which the wrt_ptr and rd_ptr point to.The "full_flag" is raised when the NOT of MSB of the wrt_ptr(with all other bits as same) is equal to the rd_ptr.
       	~(wrt_ptr[3]),wrt_ptr[2:0] == rd_ptr[3:0].

	c)Read module-This module contains the logic for reading data out of the buffer and the logic of empty_flag.For a buffer similar to that of 
write logic,the "empty_flag" is raised when the wrt_ptr and rd_ptr point to the same memory address.
	wrt_ptr[3:0]==rd_ptr[3:0]

	d)Top module-This module connects all the 3 above mentioned modules into one.All the modules are instantiated in this module and each port of each module is mapped by the method of instantiation and this is the module which is finally tested with a appropriate testbench.













B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
	b)Write module-This module contains the logic for writing of data into the buffer.It mainly gives the logic of full_flag and its relation withthe wrt_ptr and the rd_ptr.

