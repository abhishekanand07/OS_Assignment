Starve-free Reader's writers problem:

The First Readers-Writers problem gives priority to the reader processes so because  of this it results in the starvation of the writers.As there is the possibility that new readers always coming in, and the writer processes get starved. Similarily, in the Second Readers Writers problem priority is given to the writers. And in this, there is also a  possibility of readers getting starved. Aim is to provide solution that is starve-free for both Reader and Writer processes.

The Solution idea:

Let's first consider a writer process. First the process will check the number of active and waiting readers. If both, the number of waiting readers and number of active readers are not zero, then it will wait until a reader process signals and allows that writer to enter. Otherwise ,if its zero then it will read away directly.Once the writer process is done, if it is the last writer, then it will signal and allow all the writers "waiting" readers process to enter. Similarily, the last reader process will signal and allow the "waiting" writers processes to enter.


The solution can be visulised by imagining a room and two benches outside the room one for waiting reader and other for writer process. Suppose we are a writer, if there is no reader inside and no reader on the bench, then we can enter. If there are readers inside, then the last reader before leaving will allow all the writers on the bench to enter in the room. Similarily, the last writer to leave the room will allow all the readers on the bench to enter.

Psuedo code:

Reader Processes:

if(active and waiting writers are zero)
	signal and enter the process
else 
	wait for signal
	
//Read

if( is the last reader)
	signal the waiting writers
  
  
  
  
  The writer process will be analogous to the reader process.

In file Starve_free_RW_code.txt is the code for the Reader's writers problem that is deadlock-free and starvation free.

In the following solution, three semaphores are used as explained below:

1) get_set : it is a semaphore that reading processes sleep upon. A Reading process starts reading in the critical section only when get_set signals, until then it waits.
2)out_set : it is a semaphore that writing processes sleep upon. A writing process starts reading in the critical section only when out_set signals, until then it waits.
3)ind : it a mutex semaphore for controlled access to the following variables --> liv_writers, const_writers, liv_readers, const_readers.


The variables of liv_writers, const_writers, liv_readers, const_readers are used for counting the number of currently waiting and active processes.
