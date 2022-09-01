# Bahmni Performance Tester
This test is performed with the sole purpose of stress-testing Bahmni itself with certain specs of the VM where it is hosted in order to find out how it behaves (in terms of resource consumption, performance, etc.) when multiple concurrent users (up to 150).

## Tools used to perform the test
 - **JMeter** was used as an Apache project that can be used as a load testing tool for analyzing and measuring the performance of Bahmni (https://jmeter.apache.org/)

 - **Blazemeter** as a load testing platform as a service, which is compatible with open-source Apache JMeter (https://www.blazemeter.com/)
 
 ## VM Specs
Bahmni is hosted in a VM and for this test, this VM consists of the specs stated below:

 - **CPU**: 8 CPU(s) 
 - **RAM**: 16GB
 - **Hard disk 1**: 100GB 
 - **Hard disk 2**: 100GB

## Installing Tools

### Install Blazemeter
For performing the tests a VM was used. Therefore, BlazeMeter as well is installed in Chrome there.
After recording the script itself we need to export it as a **JMX** file because JMeter consumes such file as a basis for then conducting the test.
Thus,

1. I opened a Gmail account to log in to Chrome

2. Installed BlazeMeter as a Google Extension: https://support.google.com/chrome_webstore/answer/2664769?hl=en

3. I logged in BlazeMeter (because can't export a recording as a JMX without being logged in) with the Chrome account.

4. I started recording a scenario in Bahmni with BlazeMeter (e.g. Logging in and starting a new visit). After finishing the recording we can export the file as JMX
*Example on how to record a script: https://www.youtube.com/watch?v=GSIiaH334Lo

### Install JMETER
Before installing JMeter we have to install Java SDK since Java was not installed.
How to install Java: https://youtu.be/MxjjRmm0k-I
After Java is installed, we are set to install JMeter.
How to install JMeter: https://youtu.be/rV3H-ZFHz2g

### MAIN Scenario: Performing a patient consultation

[create_encounter.txt](https://github.com/albionshala/asha-bahmni-performance/files/9467929/create_encounter.txt)

note: make sure to convert it to **.jmx** if you want to test it out with JMETER

## RESULTS

Important testing variables:

1. The scenario has a "Think Time" attached to it, as recommended [here](https://dzone.com/articles/tips-and-tricks-to-compose-the-most-effective-apac#:~:text=buy%20the%20product.-,Add%20%E2%80%9CThink%20Time%E2%80%9D,-When%20real%20users). Constant delay is set to 200ms, Random Delay Max. is set to 500ms.

2. The scenario has **0ms** ramp up time, meaning all of the threads will try to become active instantaneously. This is not representative of a real-life scenario but rather of an absolute worst case one

More detailed reports: 
 - **50** Concurrent Users: [50.zip](https://github.com/albionshala/asha-bahmni-performance/files/9467794/50.zip)
 - **100** Concurrent Users: [100.zip](https://github.com/albionshala/asha-bahmni-performance/files/9467796/100.zip)
 - **150** Concurrent Users: [150.zip](https://github.com/albionshala/asha-bahmni-performance/files/9467799/150.zip)

### 50 Concurrent Users
No functional requests fail.

![image](https://user-images.githubusercontent.com/38991607/187859206-393f68ff-6ef2-4a4d-a976-5369d7740416.png)

![image](https://user-images.githubusercontent.com/38991607/187859249-a9662e66-992b-4640-ac8a-3367f8d7ab0b.png)

![image](https://user-images.githubusercontent.com/38991607/187859264-6e8aed89-f1d5-4924-890f-53565764f318.png)

![image](https://user-images.githubusercontent.com/38991607/187859267-df81694c-79cf-4cce-9ee2-c757bec3878a.png)

![image](https://user-images.githubusercontent.com/38991607/187859382-f56ffcd9-754e-40c7-adce-d796e00b76c0.png)

![image](https://user-images.githubusercontent.com/38991607/187859394-2dd39d6c-e5e1-4d18-b8d5-af401185bdf8.png)


### 100 Concurrent Users

A single Bahmni encounter request times out.

![image](https://user-images.githubusercontent.com/38991607/187859460-81f9b160-d6cf-4b5a-9a41-1439e4bc877f.png)

![image](https://user-images.githubusercontent.com/38991607/187859504-60dee770-1ebb-4976-90fa-cdd6f631e425.png)

![image](https://user-images.githubusercontent.com/38991607/187859514-3e1f4b15-2424-4e0a-b52d-edf98b6ba2a9.png)

![image](https://user-images.githubusercontent.com/38991607/187859519-77eeff0c-f8cd-4b16-b3cc-ac2608f5d0ce.png)

![image](https://user-images.githubusercontent.com/38991607/187859537-2174b740-5e86-4e4b-b84a-8ea8fdee9476.png)

![image](https://user-images.githubusercontent.com/38991607/187859546-0c359176-f1f1-411d-992f-a5c746d525ba.png)


### 150 Concurrent Users
186 out of 900 encounter requests time out.


![image](https://user-images.githubusercontent.com/38991607/187859679-d20accf8-2109-46f2-aff1-c19e6ab6d2e4.png)

![image](https://user-images.githubusercontent.com/38991607/187859692-e91e9c5e-c9c8-4b8e-ae03-38723661dee0.png)

![image](https://user-images.githubusercontent.com/38991607/187859696-70a6a1ed-a716-4768-b57b-22612e03d325.png)

![image](https://user-images.githubusercontent.com/38991607/187859715-082418ef-f570-442c-aa43-37d2fdf6e47a.png)

![image](https://user-images.githubusercontent.com/38991607/187859720-4937ddf5-0d8c-4d85-9ffc-91270f3db1b9.png)

![image](https://user-images.githubusercontent.com/38991607/187859730-bb0b8577-3b88-40db-a086-c62bfb2bfba3.png)

Whereas following errors occured:

1. [first_error.txt](https://github.com/albionshala/asha-bahmni-performance/files/9467827/read_timed_out.txt)
2. [second_error.txt](https://github.com/albionshala/asha-bahmni-performance/files/9467837/second_error.txt)

The latter one is probably due to a previous timed out request









