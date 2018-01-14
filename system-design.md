# System Design

### Concurrency 

**Thread:** is a subset of the process. Thread is an entity within a process that can be scheduled for execution. All thread of a process share its virtual address space and system resource. Each thread maintains exception handlers, thread local storage, a unique thread identifier.

**Process:** is an execute instance of a program. Process provide the resource needed to execute a program. A process has a virtual address space, executable code, a unique process identifier, environment variables, at least one thread of execution of a program. Each process is started with a single thread, often called the primary thread, but can create new threads.

[**Difference Between Thread vs Process:**](https://www.wikiwand.com/en/Thread_%28computing%29)

* thread in the same process run in a shared memory space. process runs in separate address space.
* process are independent, while thread is a subset of a process
* process carry more state information than threads, threads in the same process shared process state and memory.

**Lock/Mutex\(mutual exclusive\)**: Lock allows only one thread enter in the part that is locked. Lock is not shared with any other processes. 

**Spin-lock:** a lock which uses busy waiting. Usually a while loop keep checking the status of lock.

**Deadlock:** A situation where a set of processes are blocked because each process is holding a resource and waiting for another resource acquired by other process. For example, in the below image, Process 1 is holding Resource 1 and waiting for resource 2 which is acquired by process 2, and process 2 is waiting for resource 1.

![deadlock](https://www.geeksforgeeks.org/wp-content/uploads/gq/2015/06/deadlock.png)

**Methods for handling deadlock**
1. Deadlock prevention/avoidance: don't let system intop deadlock state
2. Deadlock detection/recovery: let deadlock occur, then do preemption to handle it once occurred.
3. Ignore the problem:  deadlock is very rare, let it happen and reboot the system.(Both windows and UNIX take this method)

```java
public class MyDeadlock {
    String str1 = "Java";
    String str2 = "UNIX"; 
    Thread trd1 = new Thread("My Thread 1"){
        public void run(){
            while(true){
                synchronized(str1){
                    synchronized(str2){
                        System.out.println(str1 + str2);
                    }
                }
            }
        }
    };
    Thread trd2 = new Thread("My Thread 2"){
        public void run(){
            while(true){
                synchronized(str2){
                    synchronized(str1){
                        System.out.println(str2 + str1);
                    }
                }
            }
        }
    };
}
public static void main(String a[]){
    MyDeadlock mdl = new MyDeadlock();
    mdl.trd1.start();
    mdl.trd2.start();
}

```
**Starvation: **a thread or process can never get the lock to process its work. It can happen when high priority thread continuously uses the resources preventing low priority process to acquire the resource. For example, A high priority process A will run before a low priority process B. If A asks for lock all the time, then B will never be able to gain the lock.






 


