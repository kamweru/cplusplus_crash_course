##### Place a class in a separate file for reusability

> GradeBook.h File

``` c++

#include <iostream>
using std::cout;
using std::endl;


#include <string>
using std::string;
using std::getline;

// Define a class GradeBook that contains a courseName data member
class GradeBook {
public:
    // constructor initializes courseName with string supplied as argument
    GradeBook(string name)
    {
        setCourseName(name); // call set function to initialize courseName
    }

    // function that sets the course name
    void setCourseName( string name )
    {
        courseName = name; // store the course name in the object
    }

    // function that gets the course name
    string getCourseName()
    {
        return courseName;
    }

    // function that displays a welcome message
    void showMessage()
    {
        // this statement calls getCourseName to get the
        // name of the course this GradeBook represents
        cout << "Welcome to the grade book for\n" << getCourseName() << "!" << endl;
    }

private:
    string courseName; // course name for this GradeBook
}; // end class GradeBook

```

> main.cpp File

> NOTE:

> The "Gradebook.h" preprocessor directive is in double quotes. 
> What it does is that it tells the preprocessor to look for the header 
> file definition in the current project. If the header file is not in 
> the current project, the preprocessor will look for it in 
> the standard header files 


``` c++
#include "GradeBook.h" // include definition of class GradeBook

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
