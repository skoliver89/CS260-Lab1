# CS260-Lab1
Sorting, Searching &amp; Empirical Analysis

General 
At the top of the every source file that you create always write a class JavaDoc that includes: 
/** 
* Description of the class 
* 
* @author YOUR NAME 
* @version CS260 Lab #, mm/dd/yyyy (replace with the last edit date) 
*/
 
Concepts 
This lab will give you some basic tools and techniques for empirical time (and space) analysis of programs. You will focus on two techniques; using counters for counting operations (for this lab we are counting comparisons and memory moves) and clock time measurement. 

Background 
Review the online text material on time and space analysis (complexity). 

Assignment 
For this assignment you will be learning to add counters to programs to measure targeted operations and clock time measurements to compare execution durations. Download the source code “SortSearch.java” from the class web site http://www.wou.edu/las/cs/csclasses/ under CS260 tab. This code fills an array with random integers and then provides several sorting routines (bubble, selection, insertion). You will be modifying this program. 
Note: It required that you use Eclipse. Please ensure that your single source file compiles correctly from the command line. 

Part #0: “Setting the environment for CS260” 
#1) Download and install Eclipse to a computer you can use whenever you need. 
#2) Make sure the program SortSearch.java actually works under your environment

Part #1: “measuring quadratic sorts” 
#1) Add in counters to measure the number of data element comparisons (that is, each time two numbers are compared, count that as 1 and increment your counter by 1) in all of the sorting methods. You will need to provide output of these values each time the array is sorted. 
#2) Add in clock time measurement of the time it takes to execute the each sort independently of each other so that you can compare them. Provide some form of output for these times. 
#3) Modify the main (or simply run the program with modified values) for 10 different test cases for EACH sort, starting with an array size of 10000 elements and increasing its size by 10000 each step until you reach an array size of 100,000. This is a linear increase in the size of the array. Track each of the time and comparison counts for all of the sorts at each step. 
#4) Build a spread sheet from these figures and construct two charts, one for time duration, and one for comparison counts (you should use the array size as your x-axis). So you will have a time duration chart comparing the times for all three sorts, then a chart showing numbers of comparisons for each sort. I am leaving the charting open ended to see what you come up with.

Part #2 “Linear & Binary searching” 
#1) Implement and test the two shelled out searching methods, searchLinear should implement a linear search and searchBinary should implement a binary search approach. Test both methods to make sure that they are working correctly. 
#2) Add in a counter to measure the number of data element comparisons for both searching methods. 
#3) Add in clock time measurement of the time it takes to execute the each search.
#4)To get somewhat valid search measures, run 100 random searches (generate a random number in the range and search for it in the array) for each listsize using the same sequence of sizes as in #3 for sorting for Part 1. Calculate the AVERAGE for each run of 100 random searches on each of the different list sizes. 
#5) Build a spread sheet and chart the data from the AVERAGE search counts for each of the listsizes that shows a comparison between the average for linear and binary search. Similarly chart the clock time for the searches. 
