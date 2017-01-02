# COMP203-16A-Assignment-Two---queue-simulation-


COMP203-16A — Assignment Two - queue simulation
Due: Monday, May 2nd, 2016 — noon (15%)

Overview: This assignment will give you experience implementing a queue and using it to simulate a single-server queuing system (called an M/M/1 simulation), such as a bank machine or fast-food joint.

For your simulation, clients arrive every 2 +/- 1 time units (i.e. integers 1, 2 or 3, uniformly distributed) and use the server for 2 +/- 1 time units before they depart the system. If the server is busy, clients join a first-in-first-out queue. Because arrivals and departures happen in integer unit times, the system keeps track of simulation time with an integer, starting at time zero. Because nothing changes in the system except when an arrival or a departure happens, simulation time moves forward to the time of the next event (i.e. either the next arrival or the next departure, whichever comes first). Since we are not interested in what happens to the system prior to the first client arriving, the first arrival happens at the start of the simulation (i.e. time zero).

Your simulation needs to keep track of three times: the current simulation time, the time of the next departure, and the time of the next arrival. The next departure time is just the current simulation time plus the amount of time the client at the head of the queue needs to use the server. It is calculated at the moment the current departure is known. Arrivals are independent, so the time of the next arrival is calculated at the moment of the current arrival, and is thus the current time plus a random inter-arrival time of 1, 2 or 3 time units. In the event that the next departure and the next arrival happen simultaneously, the arrival should be processed first in case the queue appears empty. That is, the arrival happens (and the next arrival time is calculated) and the server is immediately engaged by this sole client (and the next departure time is calculated).

Classes: Your queue only holds clients, therefore you need a Client class. We are going to try and establish the average amount of time a client spends in the system. Therefore, your Client needs two integers as member variables: one for its arrival time, and one for how long it will use the server when this Client gets to the head of the queue. These member variables should be private, and their values obtained by public "getter" methods. When a Client leaves the system, the time it spent in there is just the difference between current simulation time and the time it arrived.

When a Client arrives, its arrival time is set to the current simulation time and a random integer between 1 and 3 is generated as its required service time. The Client constructor should take these values as arguments. The Client then joins the queue. The queue is to be a dynamically linked list, so each Client object needs to have a link-reference to the next Client in the queue.

You need a ClientQueue class to manage your Clients while they are in the system. This queue needs to enqueue new Clients and dequeue departing Clients, so having a reference to the first and last Client in the linked list will be useful. An "interface" for your ClientQueue is provided on the course Moodle page and you must implement this. Any other methods you want to implement should be private.

You need a Simulator class that has a ClientQueue as a member variable. It should also keep track of current simulation time, next arrival time and next departure time. It will need a Random object (java.util.Random) to generate service and arrival times. It will also need to keep track of the sum of times Clients spend in the system so that an average can be calculated at the end of the simulation. And it needs to keep track of how many departures have happened. The constructor for your Simulator takes an integer argument specifying how many departures must happen before the simulation stops.

Your Simulator must print (to standard output) two values before it terminates: the simulation time at termination (i.e. how long the simulation ran), and the average wait time for each Client that made it through. These should be an integer and a floating point value on a single line separated by a space.

Finally, you need a program object that takes as a command-line argument one integer: the number of Clients that need to pass through the simulation. Your program object should create a Simulator and set it running. Apart from also making sure the argument is valid, this is all it needs to do.

So, you must define (in separate files) a Client class, a ClientQueue class, a Simulator class, and a program object class which should be called MyQSim.java. Your ClientQueue must implement the CQInterface.java interface available on the course Moodle page.

Run your simulation ten times, starting with 50 departures for the first run and going up by 50 each time such that the last simulation runs for 500 departures. Place your output results in a plain-text README.txt file and include it with your submission. Grading: Your program should run as a console program from the Linux command-line (i.e. no GUI). It must confrom to the specification. To get a grade of C your program must implement the queue correctly and demonstrate that it works. To get an A grade, your simulation must also work properly.

Submission: Make sure your code is properly formatted and well-documented, including your name and student identification number. Submit your source code (no .class files) and README.txt using Moodle.

Tony C. Smith, 11/03/2016
