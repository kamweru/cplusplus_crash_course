### Separate Interface from Implementation

#### The .h File

The .h file does not typically include definitions of the member functions.
The definitions are considered "proprietary" details that you don't provide
to "clients" of your class. 

Rather than fully defining the class inside the curly braces, 
we provide function prototypes i.e. provide:

* The name of the function.
* What the function returns
* Function parameters
 
> Gradebook.h File 
 
``` c++
 
#include <string>
using std::string;

// GradeBook class Definition
class GradeBook {
public:
    GradeBook(string); // constructor initializes courseName
    void setCourseName( string name ); // function that sets the course name
    string getCourseName(); // function that gets the course name
    void showMessage(); // function that displays a welcome message
private:
    string courseName; // course name for this GradeBook
}; // end class GradeBook
 
```
 
 > Gradebook.cpp File 

GradeBook member function definitions.
This file contains implementations of
the member functions prototyped in GradeBook.h
 
``` c++

#include <iostream>
using std::cout;
using std::endl;

#include "GradeBook.h" // include definition of class GradeBook

// constructor initializes courseName with string supplied as argument
GradeBook::GradeBook(string name)
{
    setCourseName(name); // call set function to initialize courseName
} // end GradeBook constructor

// function that sets the course name
void GradeBook::setCourseName( string name )
{
    courseName = name; // store the course name in the object
} // end function setCourseName

// function to get the course name
string GradeBook::getCourseName()
{
    return courseName;
}

// function that displays a welcome message
void GradeBook::showMessage()
{
    // this statement calls getCourseName to get the
    // name of the course this GradeBook represents
    cout << "Welcome to the grade book for\n" << getCourseName() << "!" << endl;
}

```

> main.cpp File 
 
``` c++
 
#include <iostream>
using std::cout;
using std::endl;

#include "GradeBook.h"

// Create and manipulate a GradeBook object
int main()
{
    // create two GradeBook objects
    GradeBook gradeBook1("Introduction to C++ Programming");
    GradeBook gradeBook2("Data structures in C++");

    // display initial value of courseName for each GradeBook
    cout << "gradeBook1 created for course: " << gradeBook1.getCourseName()
         << "\n gradeBook2 created for course: " << gradeBook2.getCourseName() << endl;

    return 0;
}
 
```