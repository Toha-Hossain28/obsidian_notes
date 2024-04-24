
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
2. 