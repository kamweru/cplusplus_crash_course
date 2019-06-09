# C++ Crash Course Notes
A C++17 Crash Course.
> Notes created while going through a C++17 Crash Course 

1. [C++ CLASSES](#1.-c++-classes)
      - [Behaviors of attributes and functions in classes](#11-attributes-and-functions-of-a-class-have-private-default-behavior)


### 1. C++ Classes

> A class might be considered as an extended concept of a data structure:
> instead of holding only data, it can hold both data and functions.

> An object is an instantiation of a class. By default, all attributes and
> functions of a class are private. If you want a public default behavior, 
> you can use keyword struct instead of keyword class in the declaration.

##### 1.1 Attributes and functions of a CLASS have PRIVATE default behavior

``` c++

class Foo {
    int attribute;
    int function(void){};
};

int main()
{
   Foo foo;
   foo.attribute = 1; // WRONG
   return 0;
}

```

##### Attributes and functions of a STRUCT have PUBLIC default behavior

``` c++ 

struct Bar {
    int attribute;
    int function( void ) { };
};

int main()
{
   Bar bar;
   bar.attribute = 1; // OK
   return 0;
}

```

##### Define a class with a member function

``` c++

#include <iostream>
using std::cout;
using std::endl;

// Define a class with a member function showMessage;

class GradeBook {
public:
    void showMessage()
    {
        cout << "Welcome to C++ Class" << endl;
    }
};

// Create a GradeBook object and call its showMessage Function

int main()
{
    GradeBook myGradeBook;
    myGradeBook.showMessage();
    return 0;
}

```

##### Define a class with a member function that takes a parameter

``` c++

#include <iostream>
using std::cout;
using std::cin;
using std::endl;    

#include <string>
using std::string;
using std::getline;

// Define a class with a member function that takes a parameter

class GradeBook {
public:
    void showMessage( string courseName )
    {
        cout << "Welcome to " << courseName << " Class" << endl;
    }
};

// Create a GradeBook object and call its showMessage Function

int main()
{
    GradeBook myGradeBook; // create a Foo object named foo
    string nameOfCourse;

    // prompt for and input course name
    cout<< "Please enter the course name:" << endl;
    getline(cin, nameOfCourse); // read a course name with spaces
    cout << endl; // output a blank line

    // Call Foo's showMessage function
    // and pass nameOfcourse as an argument
    myGradeBook.showMessage( nameOfCourse );
    return 0;
}

```

##### Define a class that contains a data member

``` c++

#include <iostream>
using std::cout;
using std::cin;
using std::endl;


#include <string>
using std::string;
using std::getline;

// Define a class GradeBook that contains a courseName data member

class GradeBook {
public:
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
};

// Create and manipulate a GradeBook object

int main()
{
    string nameOfCourse;
    GradeBook myGradeBook; // create a GradeBook object named myGradeBook

    // display the initial value of courseName
    cout << "Initial course name is: " << myGradeBook.getCourseName() << endl;

    // prompt for, input and set course name
    cout << "\n Please enter the course name: " << endl;
    getline(cin, nameOfCourse);
    myGradeBook.setCourseName(nameOfCourse); // set the course name

    cout << endl;

    myGradeBook.showMessage(); // display message with new course name

    return 0;
}   

```

 ##### Instantiating multiple objects of a class and using the class constructor

``` c++

#include <iostream>
using std::cout;
using std::endl;


#include <string>
using std::string;

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
};

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
