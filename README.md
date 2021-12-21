# cupThreadBlocking

## Sleep()  
This method is defined in Thread class. sleep() sends the current thread into the “Not Runnable” state for some amount of time. The thread keeps the monitors it has acquired This Method is used to pause the execution of current thread for a specified time in Milliseconds. Here, Thread does not lose its ownership of the monitor and resume’s it’s execution. no consuming cpu cycles.
let say you are buying a ticket from booth. it's your turn you talk to the seller "I want to take a nap"
also see https://stackoverflow.com/questions/13680512/does-endless-while-loop-take-up-cpu-resources#:~:text=The%20short%20answer%20is%20yes,a%20file%20or%20network%20operation).

## Wait()  
This method is defined in object class. put thread in WAIT state. It tells the calling thread (a.k.a Current Thread) to wait until another thread invoke’s the notify() or notifyAll() method for this object, `The thread waits until it reobtains the ownership of the monitor and Resume’s Execution.` A thread that has called Thread.join() is waiting for a specified thread to terminate. no consuming cpu cycles. In the WAITING state, a thread is waiting for a signal from another thread. This happens typically by calling Object.wait(), or Thread.join(). The thread will then remain in this state until another thread calls Object.notify(), or dies.
same example, not your turn in wait in the queue, the one head of you completed the purchase, shake your head say "it's your turn" 

## sleep vs wait 

A big difference between sleep() method and wait() method is that sleep() method causes a thread to sleep for a specified amount of time while wait() causes the thread to sleep until notify() and notifyAll() are invoked. 

## BLOCKED  
A thread that is blocked waiting for a monitor lock is in this state.In the BLOCKED state, a thread is about to enter a synchronized block, but there is another thread currently running inside a synchronized block on the same object. The first thread must then wait for the second thread to exit its block.


## wait vs blocked   

The thread is WAITING until it is notified. Then it becomes BLOCKED trying to reenter the synchronized region until all other threads have left.
if there is no synchronzation needed then no need to block(BLOCKED)


## I/O blocking
I/O blocking and thread BLOCKED statue are different concepts.  in i/o blocking, thread handle over the job to OS select or poll the thread state is RUNNING.
https://stackoverflow.com/questions/48968984/java-threads-state-when-performing-i-o-operations
what's maybe why people say "I/O blocking is waste cpu cycles". I thought the thread is blocked state which doesn't consume cpu
