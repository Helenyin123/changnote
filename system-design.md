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
3. Ignore the problem:  deadlock is very rare, let it happen and reboot the system.\(Both windows and UNIX take this method\)

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

### Computer Network:

TCP and UDP are protocols used to send bits of data, known as packets over the Internet. They both build on top of internet protocol\(IP\), so the packets are send to an IP address. TCP/IP means TCP over IP, UDP/IP too.

**TCP\(Transmission Control Protocol\)**: TCP is the most commonly used protocol on the Internet. TCP guarantees the recipient will receive the packets in order by numbering them. The recipient sends messages back to the sender saying it received the messages. If the sender does not get a correct response, it will resend the packets to ensure the recipient received them. Packets are also checked for errors. Packets sent with TCP are tracked so no data is lost or corrupted in transit. This is why file downloads do not become corrupted even if there are network hiccups.  
**UDP\(User Datagram Protocol\)**: After send packages to the recipient. The sender will not wait to make sure the recipient received the packages. It will continue to send next packages. If you are recipient and you miss a package, there is no way to ask for it again. It make the communication more quickly. It's often used in live broadcast or online games.

### Database

**Replication: **refers to frequently copying data cross multiple machines. Multiple copies of data exists across machines. It helps in case one or more machines die due to failure.

**Master and Slave Database:** master database receive data from application, slave database receive a stream of updates from master in nearly real-time. Slave apply the changes that master validated and  approved. Master database is less burdened by query and slave is less burdened by writes. From application point of view, slaves are read only and masters are read-write.

Writes are more expensive than reads. Most web application requires a much high ratio of reads to writes. So set up master-slave database could make an application distribute its queries efficiently.

**Sharding:** for some huge system, data doesn't fit into one machine. Splitting the very large database into smaller, faster and more manageable parts called data shards.

**Horizontal Scaling:** add more servers to the system to improve the performance.

**Vertical Scaling: **increase the resources\(CPU, RAM, storage\) of the server to improve the performance

For example, Let's say you own a restaurant which is now exceeding its seating capacity. One way of accommodating more people \(scaling\) would be to add more and more chairs \(scaling vertically\). However since the space is limited, you won’t be able to add more chairs once the space is full.  Another way of scaling would be to open new branches of the restaurant \(horizontal scaling\).

**CAP Theorem: **In a distributed system, it's impossible to guarantee all of three properties, we can only guarantee two out of three, which is consistency, availability, partition-tolerance.

**Consistency: **In a distribute system with many machines, data is the same in every machines.

**Eventually Consistency: **At some point, the data may have many versions in different machines, but eventually, they will reach a state where all data are the same.

**Availability**: the ability to always respond to queries irrespective nodes going down.

**Partition-Tolerance: **The cluster continues to function even if there is communication break\(partition\) between nodes.

#### Memory Estimation

| Bit Size | Estimate Exponential to 10 | Estimate Exponential to 2 |
| :---: | :---: | :---: |
| 1 KiloBytes\(KB\) | 1024 ~ 10^3 | 2^10 |
| 1 MegaBytes\(MB\) | 1048576 ~ 10^6 | 2^20 |
| 1 GigaByte\(GB\) | ~10^9 | 2^30 |
| 1 TeraByte\(TB\) | ~10^12 | 2^40 |

### Steps to approach a problem

Feature Expectation\(2 min\):  Try to list down all the features you can think of which the system should support.

Estimation\(2-5min\): come up with the estimated numbers of how scalable our system should be. Important parameters includes number of queries per second and the data which the system will be required to handle. If the total data required for the system fits on a single machine, we might not need to go into sharding. If the most frequently used data fits on a single machine, then caching could be done on a single machine.

Design Goal\(1min\):

Skeleton of the Design\(\)

Deep Dive\(20- 30min\)

Design a Distributed Key Value Caching System![Cache](https://dajh2p2mfq4ra.cloudfront.net/assets/site-images/system_design/cache_introduction.jpg)A cache has to be inherently of low latency. Which means all cache data has to reside in main memory, can't stored in disk. A production level caching machine would be 72G/144G of RAM,.

To cache on the scale of Google or Twitter, the total size of the cache would be a few TBs. if we assume total cache size is 30TB, the number of queries per second is 10M QPS and one cache machine has 72G of RAM. Then the number machines required to cache is 30TB/72GB = 420 machine.

**Cache Eviction Strategy:** determines when do we evict entries from cache and which specific entries to evict. Evict strategies includes least recently used\(LRU\), least frequently used\(LFU\), first in first out\(FIFO\), time-based\(entries that weren't touched for a period of time are cleared\).

**Cache System Access Pattern:**

* **Write Through Cache**: write is confirmed as success only if  writes to both DB and cache succeed. It's useful for applications which write and re-read information quickly. But write latency will be higher because need to write to both DB and cache.
* **Write Around Cache: **write goes directly to DB. Cache read data from DB. It ensures lower write load and faster writes.
* **Write Back Cache**: write is conformed as soon as the write to cache completes. The cache then asynchronously syncs this write to DB. This leads to quick write latency and high write throughput. But we stand the risk of losing data in case the caching layer dies. We can introduce more than one replica acknowledging the writes. 



