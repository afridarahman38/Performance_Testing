### Introduction
This document explains how to run a performance test with JMeter against an https://restful-booker.herokuapp.com/

### Install
- Java
https://www.oracle.com/java/technologies/downloads/

- JMeter
https://jmeter.apache.org/download_jmeter.cgi

Click 
- Binaries
- apache-jmeter-5.6.2.zip

Used BlazeMeter to generate JMX files
https://chrome.google.com/webstore/detail/blazemeter-the-continuous/mbopgmdnpcbohhpnfglgohlbhfongabi?hl=en

### Prerequisites
As of JMeter 5.6, Java 8 and above are supported.
Suggest multicore cpus with 4 or more cores.
Memory 16GB RAM is a good value.

### Elements of a minimal test plan
- Thread Group

- The root element of every test plan. Simulates the (concurrent) users and then run all requests. Each thread simulates a single user.

- HTTP Request Default (Configuration Element)

- HTTP Request (Sampler)

- Summary Report (Listener)

### Test Plan
Testplan > Add > Threads (Users) > Thread Group (this might vary dependent on the JMeter version you are using)

- Name: Users

- Number of Threads (users): 10

- Ramp-Up Period (in seconds): 1

- Loop Count: 1

The general setting for the tests execution, such as whether Thread Groups will run simultaneously or sequentially, is specified in the item called Test Plan.

All HTTP Requests will use some default settings from the HTTP Request, such as the Server IP, Port Number, and Content-Encoding.

Each Thread Group specifies how the HTTP Requests should be carried out. To determine how many concurrent "users" will be simulated, one must first know the number of threads. The number of actions each "user" will perform is determined by the loop count.

The HTTP Header Manager, which allows you to provide the Request Headers that will be utilized by the upcoming HTTP Requests, is the first item in Thread Groups.

### Collection of API
- Run BlazeMeter

- Collect Frequently used API

- Save JMX file then paste => apache-jmeter-5.6.2\bin

#### List of API
https://restful-booker.herokuapp.com/
OR

#### Load the JMeter Script
- File > Open (CTRL + O)
- Locate the "Restful-Booker.jmx" file contained on this repo
- Open those file
- The Test Plan will be loaded

### Test execution (from the Terminal)
- JMeter should be initialized in non-GUI mode.
- Make a report folder in the bin folder.
- Run Command in jmeter\bin folder.

Make jtl file
  jmeter -n -t Restful-Booker.jmx -l Restful-Booker.jtl
Then continue to upgrade Threads(200 to 400) by keeping Ramp-up Same.

After completing this command

Make html file
jmeter -g Report\Restful-Booker.jtl -o Restful-Booker.html
- g: jtl results file

- o: path to output folder

### HTML Report
