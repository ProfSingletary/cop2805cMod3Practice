cop2805cMod3Practice

Practice Exercise for COP2805C Module 3

Write a multi-threaded Java program named "TimerThread" which prompts the user for 3 space separated integers. The program should then spawn one thread for each integer; each thread must loop 5 times, sleeping for n seconds between iterations, where n is the integer associated with the thread. Each thread should display identifying information about itself (which number it is associated with, which iteration it is currently processing). Use a join statement in your main method which joins with each thread to verify they have exited before exiting your main method.

Hints:

- Define a class which extends the Thread class so you can store the number associated with that thread.
- Override the run method in your extended class to perform the sleep/delay/repeat operation.
- Provide a constructor for your extended class which sets the integer as a parameter and starts the thread.
- Store the instantiated thread objects (your extended class) in an array in your main method.
- Call the start method in the constructor to start the object's run method as a thread as shown here:
 
    class MyObject extends Thread {
    
        int myNumber;
        
        public MyObject(int myNumber) {
            this.myNumber = myNumber;
            start();        
        }
        void run() {}
    }
 
- You can call join() on the elements of the thread array using a loop, e.g.

        for (int i = 0; i < ARRAYSZ; i++)
        {
            try {
                threads[i].join();
                log("thread[" + i + "] joined");
            } catch (InterruptedException e) {
                log("join on thread " + i + " interrupted!");
            }
        }
        
Remember that Thread.sleep works in milliseconds, and that you must catch or throw InterruptedException in order to use Thread.sleep().
A static helper method which sleeps with the necessary try/catch can save some code lines, e.g.

    static void sleep(int msecs)
    {
        try {
            Thread.sleep(msecs);
        } catch (InterruptedException e) {
            log("interrupted");
        }   
    }


Expected (but not necessarily in the same order) output:

        Please enter 3 integers separate by a space: 2 4 6
        Timer thread for value 2, iteration 1
        Timer thread for value 6, iteration 1
        Timer thread for value 4, iteration 1
        Timer thread for value 2, iteration 2
        Timer thread for value 2, iteration 3
        Timer thread for value 4, iteration 2
        Timer thread for value 6, iteration 2
        Timer thread for value 2, iteration 4
        Timer thread for value 4, iteration 3
        Timer thread for value 2, iteration 5
        Timer thread for value 2 is exiting!
        thread[0] joined
        Timer thread for value 6, iteration 3
        Timer thread for value 4, iteration 4
        Timer thread for value 4, iteration 5
        Timer thread for value 6, iteration 4
        Timer thread for value 4 is exiting!
        thread[1] joined
        Timer thread for value 6, iteration 5
        Timer thread for value 6 is exiting!
        thread[2] joined
        main thread is exiting!
