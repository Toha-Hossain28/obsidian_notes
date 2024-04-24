
#JAVA #multi-threading
## What is multi programming? 
 Running more than one program in a single computer is called multi programming.
	Two types of multi programming :
		1.  ___Multi user___ - *single computer multiple user*
		2. ___Multitasking___ -  *single user running multiple program simultaneously*
			 Multi-threading - *multiple thread is working simultaneously for a single program*
## What is multi threading?
Multiple thread is working simultaneously for a single program
like in a YouTube chrome tab one thread is playing video, maybe another one is loading and showing live comment, another one may be loading and showing ads
## Control flow of a program
 I know it
## Thread in JAVA
 2 ways to achieve multi-threading in JAVA.
	 1. Using ___Thread class___
	 2. using ___Runnable Interface___

1. Extending Thread class	
```java
class MyThread extends Thread
{
	@override
	public void run()
	{
		int i = 1;
		while( true ) 
		{
			System.out.println("Hello " + i);
			i++;
		}
	}
}
class test 
{
	public static void main ( String[] argv)
	{
		MyThread t = new MyThread();
		t.start();
		int i = 1;
		while( true )
		{
			System.out.println("World " + i );
			i++;
		}
	}
}
```
2. Implementing Runnable Interface
```java
class runThread implements Runnable
{
	public void run () 
	{
		int i = 1;
		while (true) 
		{
			System.out.println(i + "Hello");
			i++;
		}
	}
}
class test 
{
	public static void main (String[] args)
	{
		runThread r = new runThread();
		Thread t = new Thread(r);
		t.start();
		int i = 1;
		while( true )
		{
			System.out.println(i + "World");
			i++;
		}	
	}
}
```
## States of Thread
 
 ![[IMGS/Pasted image 20240424112525.png]]
 ![[Thread status.png]]
 - if a thread has finished it task you can't restart the thread you have to create a new thread.

## Thread Priority


## Constructors

- Thread ( );
- Thread ( String name );
- Thread ( Runnable r);
- Thread ( Runnable r, String name);
- Thread ( ThreadGroup g, String name);
	#### - getter and setter methods
		- long getid();
		- String getName();
		- int getPriority();
		- ThreadState getState();
		- ThreadGroup getThreadGroup();
		- void setName ( String name );
		- void setPriority( int p );
		- void setDaemon ( boolean b); 
			 to set the thread as background thread (least thread priority)
		
	#### - Inquiry
		- boolean isAlive();
		- boolean isDaemon();
		- boolean isInterrupted();
		
	#### - Instance method
		- void interrupt();
			- to stop the thread from doing what is was doing. this method 
			 can be called by itself or other thread 
		- void join();
			- wait for other thread to complete instead of terminating
		- void join( long millis);
		- void run();
		- void start();
		
	#### - Static methods
		- int activeCount();
			- gives how many threads are active in a group
		- Thread currentThread();
			- gives the reference of current thread 
		- void yield();
			- starvation: if a thread is having way to high priority and other
			 threads are waiting for a long time.
			 this method will tell the JVM to hold the higher priority thread
			 and give some time to the low priority thread
		- void dumpStack();


## Synchronization

1.  ___Resource Shearing___ : 
     more than one thread is sharing some object or variable
2.  ___Critical Section___ :
     that part of code of thread where a shared resource is being accessed
3. ___Mutual Exclusion___ :
     happening of one prevents happening of another. Means if a thread is accessing some shared resource another thread must not access that resource. If that happens then we may have mixed result.  
1. ___Locking/Mutex___ :
2. ___Semaphore___ :
3. ___Monitor___ :
4. ___Race Condition___ :
5. ___Inter-Thread Communication___ :