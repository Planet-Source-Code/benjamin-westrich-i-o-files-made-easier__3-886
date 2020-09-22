<div align="center">

## I/O files made easier :\)


</div>

### Description

This is to make Sequential access files easier to use. I remember when I first learned them from my text, it wasnt easy, and this should clear a few things up.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Benjamin Westrich](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/benjamin-westrich.md)
**Level**          |Beginner
**User Rating**    |4.4 (40 globes from 9 users)
**Compatibility**  |C\+\+ \(general\), Microsoft Visual C\+\+
**Category**       |[Data Structures](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/data-structures__3-8.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/benjamin-westrich-i-o-files-made-easier__3-886/archive/master.zip)





### Source Code

Well, We are going to look into Sequential access files and how to make and use them with a C++ program. Its not so hard... below I have fully commented code that will tell you step by step what each thing does. As while this is beginner, you should atleast know a few things like loops and variables before doing this. THe first one is the complete source to a program, the second bit is a commented snippet to companion the first. Please rate me even if a bad rating:
<font color="blue">#include</font> <iostream.h><iostream.h><br>
<font color="blue">#include</font> <fstream.h><font color="#339900"> //Has
the info for opening the file, and input/output </font><br>
<font color="blue">int</font> main() <br>
{
<pre><font color="#339900">	//declare variable</font>
	float number;
<font color="#339900">	//open file </font>
	ofstream Out_File;<font color="#0000FF"> <font color="#339900">//associates it(object (Out_File) with this class, used to ouput info to a file </font></font>
	Out_File.open("datafile.dat", ios::app);<font color="#339900">//commented on heavily at end </font>
<font color="#339900">	//Check for open</font>
<font color="#0000FF">	if</font> (!Out_File.fail()) <font color="#339900">//checks to make sure it DIDNT fail (! operator) </font>
	{
<font color="#339900">		//input names and write to file </font>
		cout << "Please enter a number(enter a negative to exit): ";
		cin >> number;
<font color="#0000FF">		while</font> (number >= 0) <font color="#339900">//loops to check for a negative number </font>
		{
		Out_File << number << endl; <font color="#339900">//adds the line to the data file you opened. </font>
		cout << "Please enter a number(enter a negative to exit): ";
		cin >> number;
		}<font color="#339900">//end while </font>
<font color="#339900">		//close the file</font>
		Out_File.close();
	}
<font color="#0000FF">	else</font> <font color="#339900">//incase it didnt open for any reason.... </font>
	cout << "Sorry, error opening file... " << endl;
<font color="#339900">	//end if </font>
}<font color="#339900">//end main function(close program, no other prototypes) </font>
 </pre>
<pre>	<font color="#339900">/* Now, the 'Out_File.open("datafile.dat", ios::app)'works like so. The open part is
	fairly obvious, it opens the Object Out_file. The first part, "datafile.dat" is the
	filename you wish to open, or create(incase it doesnt exist).the second is the type
	of I/O you want, they follow the 'ios::' command and are as follows:
	ios::in Opens file for input into the program, Default mode for input files(will talk about later)
	ios::app Opens file for 'append', If the file doesnt exist it will create a new one, but if it
	does it will actually just continue writing to it with whatever you had on there before still on
	ios::out Opes a file for output to it, creates a new one, or deletes all the info in an old one so
	that it it starts of new. Very different then the append....
	on a side note: Out_File << number << endl; the endl actually makes a newline
 on the data file so that the data is on different lines and can be differentiated.
	Hopes this helps :) */</font>
 </pre>
<pre>
	Now... the code for the input of info from the file to the program is as follows...
	This is just a snippet and lacks header files, variable declaration, and main function call as you have seen all that in the last bit:
 <font color="#339900">//open file for for input</font>
 ifstream input_file;
 input_file.open("datafile.dat", ios::in); <font color="#339900">//make sure open was successful(more important in this one then the last)</font>
 <font color="#0000FF">if </font>( !input_file.fail() )
 {
		<font color="#339900">//read from file</font>
 		input_file >> score;
		<font color="#0000FF">while</font> ( !input_file.eof() )
 		{
 		<font color="#339900">	//increment counter and average</font>
 			index++;<font color="#339900"> //same as index = index + 1, shortens it </font>
 			totalscore += score;<font color="#339900"> //same as totalscore = totalscore + score, shortens it </font>
 			input_file >> score; <font color="#339900">//takes from file into the program.</font>
 		}<font color="#339900">//end while loop
		//close input_file</font>
 		input_file.close();
 <font color="#339900">
		//display average</font>
 		average = (float) totalscore / (float) index;
 		cout << "The average of the numbers you entered was " << average << endl;
 }
 <font color="#0000FF">else</font><font color="#339900"> //failed to open...</font>
 		cout << "cant open file";
 <font color="#339900">//end if</font>
 <font color="#339900">/* Pretty straight forward, we used to ifstream (input file) instead of ofstream this time,
	and it is to be noted that you dont have to assign it a value to read from as an array, since
	it does it in order. One by one. Hopes this helps to! */
 </font>

