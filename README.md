java cObject-Oriented Programming
Resit Coursework
This assignment involves the development of Java classes and a program to support analysis of earthquake
data compiled by the United States Geological Survey. We have provided three example datasets that you
can use to test your solution.
1 Preparation
A Zip archive containing the ffles for the assignment is provided in Minerva. When you unzip it, you should
see three ffles of earthquake data, along with four .java ffles. One of these, QuakeException.java, is
complete and ready for you to use; the other three ffles containing empty Java classes.
There are ‘To Do’ comments inside the classes that summarise the code that you need to write, and detailed
step-by-step instructions are provided below.
Before you begin programming, take some time to study the sample data. You can use a spreadsheet
application to do this. Each row in the dataset represents a single earthquake. The different columns
represent various parameters measured for an earthquake. You don’t need to know what most of these are,
although further details can be found at the USGS Earthquake Hazards Program website if you are interested.
The only columns relevant to this assignment are: latitude, longitude, depth and magnitude.
Note that fflenames consist of two parts: a severity level (often expressed in terms of earthquake magnitude)
and a time period. The two parts are separated by the underscore character. Thus, 2.5_day.csv contains
details of earthquakes of magnitude 2.5 or greater, recorded over a single day; 4.5_week.csv records
earthquakes of magnitude 4.5 or greater, over a one-week period; and significant_month.csv records
‘signiffcant’ earthquakes recorded during a one-month period.
2 Quake Class
This class encapsulates the details a single earthquake.
1. Edit Quake.java in a text editor. Add to the class ffelds that represent the latitude, longitude, depth
and magnitude of an earthquake.
2. Create a constructor for Quake that takes a single String parameter. This string represents all of the
data provided by the USGS for a single earthquake, with each value separated from the others by
commas. To see real examples of what this string looks like, open one of the data ffles in a text editor
(not in a spreadsheet), and examine any of the lines after the ffrst.
Note: you can use a method of the String class to help you implement this.
Your constructor should perform some basic validation, checking that latitude is within the allowed
range of −90.0
◦
to 90.0
◦
, and that longitude is within the allowed range of −180.0
◦
to 180.0
◦
. You
should throw an instance of QuakeException, containing an appropriate error message, if latitude or
longitude are invalid.
3. Write simple ‘getter’ methods for each of the ffelds. These methods should simply return the values
of the ffelds.
4. Write a toString method for Quake. This should generate and return a string representation of
the Quake object. The string should contain magnitude, depth, latitude and longitude, in that order,
formatted like this example:
M5.0, 12.6 km, (35.4975°, 141.0217°)
Note: the ‘degrees’ symbol can be generated with the Unicode escape sequence \u00b0.
As you complete each step of implementing this class, remove the corresponding ‘To Do’ comment and
check that your code compiles.
Once you’ve written the constructor and getter methods, you can test them by writing a small program that
creates a Quake object from a string. You can use one of the lines from the given data ffles as the string.
1IMPORTANT: You should make sure that the Quake class is working as expected before moving on to
the other class or the program that uses the classes.
3 QuakeDataset Class
This class represents an entire dataset containing the details of multiple earthquakes.
1. Edit QuakeDataset.java. Add to the class a ffeld that can represent a collection of Quake objects.
There are various options open to you here, some of which will be easier to u代 写program、java
代做程序编程语言se and more ffexible than
others. Make sure that the ffeld is initialized properly—either at the point of deffnition or by writing
a constructor.
Note that when a QuakeDataset object is created, it should represent an ‘empty’ dataset—ready to
accept data, but not yet containing any data.
2. Now write a method named readData in QuakeDataset. This method should accept two String
parameters, representing the severity level and time period for a ffle of earthquake data.
Note that the allowed values for severity level are significant, 4.5, 2.5, 1.0 and all. The
allowed values for time period are hour, day, week and month. You should throw an instance of
QuakeException if the supplied parameter values do not meet these requirements.
The readData method should
• Read earthquake data from the relevant data ffle
• Turn each line of data into a Quake object
• Store this Quake object in the ffeld provided for this purpose
The name of the data ffle should be determined from the severity level and time period parameters:
e.g., if severity is "4.5" and period is "week", then 4.5_week.csv should be used.
The readData method should NOT intercept any exceptions that might occur during the process of
reading from the CSV ffle.
3. Write a method named size that returns the number of Quake objects currently stored.
4. Write a method named get that returns the Quake object at a speciffc position. Position should be
supplied as an int parameter and should be zero-based: i.e., calling get with an argument of 0 should
return the ffrst Quake object in the dataset.
5. Write a method to ffnd and return the Quake object representing the strongest (maximum magnitude)
earthquake in the dataset. If there are multiple candidates, the ffrst one should be returned by the
method.
6. Write a method to ffnd and return the Quake object representing the shallowest (minimum depth)
earthquake in the dataset. Again, in the case of multiple candidates, the ffrst one should be returned
by the method.
7. Finally, write a method that prints out details of each Quake object, one quake per line. You should
exploit the toString method deffned in Quake for this.
As with Quake, you should remove the relevant ‘To Do’ comments as you implement each method, and you
should ffx any compilation errors before moving on to the next step.
You will need to make sure that your QuakeDataset class is reasonably robust. The get method and the
methods to ffnd the strongest, weakest, deepest and shallowest earthquakes should all throw an instance
of QuakeException if there are no Quake objects currently stored in the QuakeDataset object. The get
method should throw an instance of QuakeException if the supplied position parameter is invalid.
4 QuakeInfo Program
Edit QuakeInfo.java. Inside the main method of the class, write the code indicated by the ‘To Do’
comments, removing the comments as you go. The ffnished program should print this and then terminate if
it is run without two command line arguments:
Usage: java QuakeInfo  
2If the program is run with two arguments but one or both are invalid, it should catch the resulting exception
and display the associated error message, then terminate.
If the program is run with two valid arguments, and if a valid CSV ffle corresponding to these arguments
exists, the program should generate output like this:
7 quakes in dataset
M6.1, 54.0 km, (-21.9342°, -70.3404°)
M6.2, 96.8 km, (-22.1960°, -68.4984°)
M7.0, 10.0 km, (17.5601°, 120.8011°)
M5.4, 10.0 km, (26.9092°, 55.2149°)
M6.4, 10.0 km, (-44.5986°, -79.7623°)
M6.8, 10.0 km, (-22.6455°, -114.2227°)
M4.7, 51.1 km, (60.9805°, -150.9365°)
Shallowest : M7.0, 10.0 km, (17.5601°, 120.8011°)
Strongest : M7.0, 10.0 km, (17.5601°, 120.8011°)
5 Submission
Create a Zip archive containing all of .java and .csv ffles. Submit this Zip archive via the link provided
in Minerva.
The deadline for submission will be advertised in Minerva.
3

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
