# C++ Crash Course Notes
A C++17 Crash Course.
> Notes created while going through a C++17 Crash Course 

1. [C++ CLASSES](#1.-c++-classes)
      - [Behaviors of attributes and functions in classes](#1a-attributes-and-functions-of-a-class-have-private-default-behavior)
      - [Behaviors of attributes and functions in structs](#1b-attributes-and-functions-of-a-struct-have-public-default-behavior)
      - [Define a Class with a member function](#1c-define-a-class-with-a-member-function)
      - [Define a class with a member function that takes a parameter](#1d-define-a-class-with-a-member-function-that-takes-a-parameter)
      - [Define a class that contains a data member](#1e-define-a-class-that-contains-a-data-member)
      - [Instantiating multiple objects of a class and using the class constructor](#1f-instantiating-multiple-objects-of-a-class-and-using-the-class-constructor)
2. [Place a class in a separate file for reusability](#2-place-a-class-in-a-separate-file-for-reusability)
3. [Separate Interface from Implementation](#3-separate-interface-from-implementation)

### 1. C++ Classes

> A class might be considered as an extended concept of a data structure:
> instead of holding only data, it can hold both data and functions.

> An object is an instantiation of a class. By default, all attributes and
> functions of a class are private. If you want a public default behavior, 
> you can use keyword struct instead of keyword class in the declaration.

##### 1.a Attributes and functions of a CLASS have PRIVATE default behavior

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

##### 1.b Attributes and functions of a STRUCT have PUBLIC default behavior

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

##### 1.c Define a class with a member function

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

##### 1.d Define a class with a member function that takes a parameter

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

##### 1.e Define a class that contains a data member

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

 ##### 1.f Instantiating multiple objects of a class and using the class constructor

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

##### 2. Place a class in a separate file for reusability

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

### 3. Separate Interface from Implementation

##### The .h File

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
