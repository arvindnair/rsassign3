Recommender Systems Assignment 3 Arvind Nair README File.

Folder Extraction and its contents:
1. PA3 is zipped folder and you need a WinZip or WinRar or 7zip to extract the contents.

2. Once you extract the contents, it will contain the following files:
 2.1 commons-math3-3.3.jar: It is the Apache Commons Math jar file which I used to initialize P and Q when the user chooses the -initPQ option.
 2.2 jama.jar: It is the JAMA jar file which was used for the Matrix representation required in the assignment.
 2.3 outputonmypc.txt: It is the file which contains the output as obtained on my PC by running the program for the assignment.
 2.4 P1.txt: It is the P1 file provided for reading.
 2.5 Q1.txt: It is the Q1 file provided for reading.
 2.6 README.txt: It is this file.
 2.7 rec3.jar: It is the main file which will execute the program for the assignment.
 2.8 results.txt: It is the file which contains the results as stated in the assignment.
 2.9 sourcecode.txt: It is the source code in plain text.
 2.10 test1.txt: It is the testing dataset provided for the assignment.
 2.11 train1.txt: It is the training dataset provided for the assignment.

How to compile and run the code:
1. I have used Java programming to do the assignment. The program is in a JAR file(rec3.jar). 

2. I have compiled into a runnable JAR file as for Matrix operations I have used an external JAR package named JAMA and for the normal distribution I have used the Apache Commons Math 3 JAR package. I have included JAMA and Math 3 in the folder PA3 for reference.

3. The source code has been provided in a separate text file.

4. I choose to make it a runnable JAR file as it encapsulates the JAMA and Math 3 library which is not a part of Java installation.

5. To run the JAR file from command prompt, open cmd and set the path in the folder PA3 to (location where Java is installed)/Java/jdk(version)/bin and type java -jar rec3.jar

6. Note that the train1.txt, test1.txt, P1.txt, Q1.txt, and samples_ml100k_0.02_0.005_0.005_0.005_k25.txt must be in the same folder as that of the JAR File.

7. The program starts and runs as per the instructions given in the assignment.

8. The program also asks the user for inputs of k, lambdau,lambdai, lambdaj, alpha and N and the user has to enter them. 

9. I have included a results.txt file in PA2 folder which has the results of the program as specified in the assignment in the order: Learning time = XXX sec, 
K=25, alpha=0.02, lambdau=0.005,lambdai=0.005,lambdaj = 0.005, N = 10, HR = mmm, ARHR = nnn

10. The outputs will be displayed on the screen as specified in the Assignment: Learning time = XXX sec, K=25, alpha=0.02, lambdau=0.005, lambdai=0.005, lambdaj = 0.005, N = 10, HR = mmm, ARHR = nnn

Note:
1. In order to choose the -readPQ option just enter 1 and then type the file name P1.txt and Q1.txt as required and both the files will be read.

2. When you choose the -initPQ option it will generate a P and Q matrix of size mXk and nXk where m is the number of users and n is the number of items using Apache Commons Math 3 package for Normal Distribution of mean 0 and standard deviation 0.1.

3.I have set the program to output the ns value at every 1000000 times. This will help us to notice that the program is running. It displays about 10 ns values and then calculates the HR and ARHR as specified in the assignment.

4.Each HR and ARHR took about 230000.0 ms on an average but that was on my PC and depending on my PC configurations and settings. It may take more time another machine. In the results file you can see that time in the learning time part.

5. Initially there is no learning time for the first time as it calculates the raw matrix without learning. Then the result is repeated due to the condition of nnz(R).
After that the learning begins. It displays the output accordingly.

6. The HR and ARHR increase sharply after the first learning and the proceed to be zig-zag with a small variation in between.

7. HR and ARHR is printed out 20 times. 

8. As mentioned in the Assignment I have taken N=10.

9. HR is around approx 0.115 and ARHR is around approx 0.018.

10. I have not put the samples file as it is too big to upload so you have to place it manually in the PA3 folder after extraction.

11. In -readPQ option, you have to give the filename as P1.txt and Q1.txt when asked.

How my code works:
1. [Line 39-86] Specify the train1.txt file path and then read train1.txt into CSR format.
2. [Line 103-172] Specify the test1.txt file path and then read test1.txt into CSR format.
3. [Line 188-194] Take the k and Top N value from user.
4. [Line 198-279] The -readPQ option works once the user enters 1 as his choice and the P and Q matrices are generated after reading the provided P and Q files are inputted from console.
5. [Line 281-304] The -initPQ option works once the user enters 2 as his choice and the P and Q matrices are generated after using the Normal Distribution function of the Math 3 JAR package. Values are generated randomly using the sample function.
6. [Line 306] The HR and ARHR are then calculated using the hrarhr function on the unlearnt P and Q matrices.
7. [Line 309-319] The lambdau, lambdai, lambdaj and alpha are taken as input from the user as required.
8. [Line 322-324] For convenience, I multiplied the lambdas by 2 and stored in different variables named lambdau2, lambdai2 and lambdaj2.
9. [Line 327] The sample file name is specified.
10. [Line 330,468 and 561-565] The timer is started and ends. Note that the start time is done twice as after each HR and ARHR calculation it must be reset.
11. [Lines 332-339] Reads the samples file provided line by line.
12. [Lines 341-460]First the ruij is calculated. Then it is passed to the sigmoid function and then Pu is updated as per the formula given for BPR.
13. Then the ruij is calculated again as the Pu has been updated, passed to the sigmoid function and Qi is updated as per the given formula. Similarly for Qj.
14. The program updates the Pu, Qi and Qj in the Matrix P and Q only at the end but keeps it updated in the array as this increases the speed of the program as we do not have to read P and Q repeatedly.
15. [Lines 466-469] The HR and ARHR is calculated when the condition is met as per the assignment.
16. [Lines 461-463] The ns value is output on the console to show that the program is running. This is for informational purposes only.
17. [Lines 478-483] The sigmoid function is specified.
18. [Lines 486-571] The hrarhr function is specified which calculates the HR and ARHR values for the P and Q matrices during the learning.
19. [Lines 574-631] The sorting function is specified to sort the cadidate set using merge sort in order to calculate the HR and ARHR for Top N items.
