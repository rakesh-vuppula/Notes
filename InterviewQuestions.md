1. what is encapsulation ? what is abstraction ?
2. What happens if I return Unique pointer?
3. auto_ptr vs shared_ptr?
4. what will happen if shared_ptr is created using raw pointer and later deleted?
5. difference between static_cast and Implicit conversion () ?
6. A -> B&C -> D Dimond problem? what will be the order of construction of classes?
7. map, un ordered map and multimap? time complexity?
8. Why threads? Synchronisation ? deadlock ? data race?
9. What's new learnt in c++?
10. Design patterns? how many you know? explain breifly?
11. Diamond problem?
12. Class B and C are derived from A is in library and B&C are not virtually derived. How outside class D will use A methods without abmigious?
13. What is copy elision?
14. What happens in below cases.
    ```
	itr = somevector.begin();
	itr--;
	
	itr = somevector.end()
	itr++;
    ```

16. When do you use Lambda function?
17. What will be the value of x in each case?
    ```cpp
    auto incr1(int& a) {return ++a;}
    auto incr2(int& a) {return a++;}
    decltype(auto) incr4(int& a) {return ++a;}

    int y = 10;
    int& x = incr1(y);
    int& x = incr2(y);
    int& x = incr4(y);
    ```

18. How to represent binary number ( ex: 1010 1110 to int var)?

19. what is deprecated attribute?
20. What is Generic Lambda ?

21. Little Endian and Big Endian?
22. Static and Dynamic linkage?
23. covariant return types...!
    ```cpp
    class Base
    {
    public:
        // This version of GetThis() returns a pointer to a Base class
        virtual Base* GetThis() { return this; }
    };
    
    class Derived: public Base
    {
        // Normally override functions have to return objects of the same type as the base function
        // However, because Derived is derived from Base, it's okay to return Derived* instead of Base*
        virtual Derived* GetThis() { return this; }
    };
    //Note that some older compilers (eg. Visual Studio 6) do not support covariant return types.
    ```

24. what is Koening lookup ?
25. Variable argument list example.. ?
    ```cpp
    #include <stdio.h>
    #include <stdarg.h>

    double average(int num,...) {

    va_list valist;
    double sum = 0.0;
    int i;

    /* initialize valist for num number of arguments */
    va_start(valist, num);

    /* access all the arguments assigned to valist */
    for (i = 0; i < num; i++) {
        sum += va_arg(valist, int);
    }
        
    /* clean memory reserved for valist */
    va_end(valist);

    return sum/num;
    }

    int main() {
    printf("Average of 2, 3, 4, 5 = %f\n", average(4, 2,3,4,5));
    printf("Average of 5, 10, 15 = %f\n", average(3, 5,10,15));
    }
    ```
26. How to allocate memory to N-D array and how to pass/return to/from function?
27. How new and delete will work?
28. write overrloadin new and delete operators?
29. Deep Copy vs shallow copy?
30. How to write overloaded operator for Obj + 1 and 1+obj ?
  
31. Abstract classes and Interfaces.
    ```cpp
    Class Base
    {
    public :
    virtual void func(){}
    }
    Class D1 : public Base
    {
    public :
    virtual void func() override{}
    }
    Class D2 : public D1
    {
    public :
    virtual void func() override{}
    }

    Base* b = new D2;
    b->func(); //will call func of D1
    ```

32. Can Virtual functions be private in c++?
33. write a function to overload template function?
34. what is the value of vptr in case of an Interface class and abstract class?
35. when do you use volatile keyword?
36. Time and Space complexity of different container and operations? **
37. Can inline functions be virtual?
38. inline vs Macro
    ```
    Macros are error prone
        #define DOUBLE(X) X*X
        int y = 3;
        int j = DOUBLE(++y); // expecting 16 but would get 25.
    ```
39. Can a constructor be inline?
40. Can I overload function of Base in derived?
    ```cpp
    class Base {
    public:
        virtual void fun() { cout << "Base Fun"<<endl; }
    //friend int main();
        void display(int i)
        {
            cout<<"Base display"<<endl;
        }
    };
    class Derived: public Base {
    public:
        void fun() { cout << "Derived Fun"<<endl; }
        void display()
        {
            cout<<"Derived display"<<endl;
        }
    };

    int main ()
    {
        Derived d;
        d.display(1234);
        d.display();
    }
    ```
  
41. How to solve problem in above code?
    ```cpp
    //Modify derived class as below.
	class Derived: public Base {
		public:
			void fun() { cout << "Derived Fun"<<endl; }
			using Base::display; //Bring Base display function to derived class scope.
			void display() // Overloading Base class method will not work.
			{
				cout<<"Derived display"<<endl;
			}
		};
    ```
39. Can I call a virtual method from constructor ?
  
40. Size of an empty class?
41. Can I through exception in Constructor? Explain in details? **
42. How to Reduce or avoid padding bits?
    ```cpp 
	#pragma pack(n) //n byte alignment
    ```

43. Output of below program 
    ```cpp
    class Base1 
    {
        int x, y;
        public:
            Base1(){cout<<"default constr"<<endl;}
    };        
    class Base2
    {
        int x, y;
    };
    int main()
    {
    Base1 b1Obj = {10, 20};
    Base1 b2Obj = {10, 20};
    return 0;
    }
    ```
  
44. what will happen If I declare a namespace within a class?
45. What is the order of member initialization in class initializer list?
46. Do you see any problem in below code snippet and explain?
    ```cpp
    int x = 10;
    switch(x)
    {
        case 10:
            int a = 1;
            cout<<a<<endl;
            break;
        case 20:
            int b;
            b = 2;
            cout<<b<<endl;
            break;
        case 30:
            {
                int c = 30;
                cout<<c<<endl;
                break;
            }
        default:
            break; 
    }
    ```
  
47. what is Conversion Constructor and conversion operator?
	> Conversion operator will not have return type but it returns object.
	
48. Whar is the size of each struct?
    ```cpp
	struct A
	{
		int i;
		char c;
	};

	struct B
	{
		struct A a;
		char c;
	};
	struct C
	{
		double d;
		struct A a;
		char c;
	};
	struct D
	{
		double d;
		struct A* a;
		char c;
	};
	```
	
49. What is the output ?
	```cpp
	class Base
	{
	  public:
		Base(){cout<<"constructor"<<endl;}
		~Base(){cout<<"destructor"<<endl;}
		virtual void dummy(){}
		void* operator new(size_t nbytes)
		{
			cout<<"new operator"<<endl;
			return malloc(nbytes);
		}
		void operator delete(void* ptr)
		{
			cout<<"delete operator"<<endl;
			free(ptr);
		}
	};
	class Derived : public Base
	{
	  public:
		Derived(){cout<<"Derived constructor"<<endl;}
		~Derived(){cout<<"v destructor"<<endl;}
		virtual void dummy() override{}
		void* operator new(size_t nbytes)
		{
			cout<<"Derived new operator"<<endl;
			return malloc(nbytes);
		}
		void operator delete(void* ptr)
		{
			cout<<"Derived delete operator"<<endl;
			free(ptr);
		}
	};
	int main()
	{
		Base* b = new Base;
		delete b;
		
		Base* b = new Derived;
		delete b;
		return 0;
	}
    ```
	
50. Output of below program?
    
	```cpp
	class A
	{
	public:
		virtual void fun() { cout << "A::fun() "; }
	};

	class B: public A
	{
	public:
	void fun() { cout << "B::fun() "; }
	};

	class C: public B
	{
	public:
	void fun() { cout << "C::fun() "; }
	};

	int main()
	{
		B *bp = new C;
		bp->fun();
		A *ap = new C;
		ap->fun();
		return 0;
	}
	```	
51. What is dangling pointer?
	
52. Can we do - delete this; - ?
	
53. What is segmentation fault? How do you debug? **
	
    The following are some typical causes of a segmentation fault:
    * stack overflow.
    * Buffer underflow
    * Attempting to access a nonexistent memory address (outside process's address space)
    * Attempting to access memory the program does not have rights to (such as kernel structures in process context)
    * Attempting to write read-only memory (such as code segment)
    ```cpp
        int main(void)
        {
            char *s = "hello world"; // on heap
            *s = 'H'; // read-only memory
        }
    //solution: 
        int main(void)
        {
            char s[] = "hello world"; // on stack.
            s[0] = 'H';
        }
	```
54. What is Placement new operator?
	
55. If we try to use memory beyond allocated in placement new.. what will happen?
	
56. New vs Malloc ?

    | new                                           |      malloc               |
    |-----------------------------------------------|:-------------------------:|
    | is an operator                                |  function                 |
    | return pointer of exact data type             |    returns void *         |
    | calls constructor                             | cannot call constructor   |
    | returns nullptr or throws bad_alloc exception | return null               |
    | can be overriden                              | cannot be overrriden      |
    | size is calculated at compile time            | size calculated manually  |

57. delete vs free ?
58. Can I delete null ptr? What will happen?
59. What will happen on calling delete twice on same obj;
    ```
    Base* b = new Base;
    delete b; // deletes the data pointed by b. But b points to same location.
    delete b; //Segmentation fault
    ```

60. Can we mix new[] and delete? what will happen?
61. Write code to pass variable arguments to function.
62. Can I realloc memory allocated using new?
    > No.. https://isocpp.org/wiki/faq/freestore-mgmt#renew
63. Do wee need to check against null after calling new? 
64. In p = new Fred(); does the Fred memory “leak” if the Fred constructor throws an exception?
    > No.. https://isocpp.org/wiki/faq/freestore-mgmt#new-doesnt-leak-if-ctor-throws
65. Exception i Constructor or destructor ? **
66. p = new Fred[n]; delete[] p;
    How Compiler will know how many object to delete/destruct?
67. How to allocate memory to multi dimentional array using new ?
68. How to restrict an Object creation to be dynamic (using new only)?
69. How to restrcit dynamic creation of Object?
70. Difference Between post increment and pre increment? Which one is efficient , why?
71. Diff between struct and class?
72. Can I declare private members of a struct?
73. What are friend classes and functions, when to use them?
74. Overloading vs. overriding ?

    - Overriding of functions occurs when one class is inherited from another class. Overloading can occur without inheritance.
    - Overloaded functions must differ in function signature ie either number of parameters or type of parameters should differ. 
        In overriding, function signatures must be same.
    - Overridden functions are in different scopes; whereas overloaded functions are in same scope.
    - Overriding is needed when derived class function has to do some added or different job than the base class function.
    - Overloading is used to have same name functions which behave differently depending upon parameters passed to them.
75. can constructor be overload?
76. can destructor be overload ?
    > The reason why you can't overload a destructor is because your code wouldn't have a clue about which destructor it needs to call when you destroy an object.
    > Unless you're calling destructors badly but then you're behaving badly! ;-) You can't! Each class can only have one destructor.\
    > Its compile time error if you try to overload it.
77. Can i call constructor /destructor explictly  ? if so how ?
78. what is object slicing ?
79. initializer list ? is there any advantage of initalizer list ?
    - For initialization of non-static const data members:
    - For initialization of reference members:
    - For initialization of member objects which do not have default constructor:
    - For initialization of base class members :
    - When constructor’s parameter name is same as data member
    - For Performance reasons
80. Why Const reference is used in Copy constructor?
81. when all the copy constructor called ?
82. can i delete this pointer in a destructor?
83. virtual base classes ? what does it mean ?
84. function pointers ? what's the advantage of function pointers ?
85. What difference between array and vector ?
86. Difference between sequence container and associative container ?
87. Is stl::set is associative or sequence container? Why?
88. How to find an element (which is having duplicates) in multimap or multiset? **
89. Which STL should be used to achieve data serialisation? **
90. How does map::insert work if the key is going to be user defined type like object?
91. Types of iterators , Explain each with examples
92. Explain about volatile keyword ? when does we use it ?
93. Different types of casting ?
94. Difference between static and dynamic casting ?
95. Can we cast dynamic casting for non - polymorphic objects ? **
96. If so can casting will be successful ?
97. Why we cannot create object of pure virtual function or abstract class ?
98. Can we give of pure virtual function definition in base class ?
99. What is function objects or functors ?
100. Let us assume , class have a protected members (base class).
    Now derive class has inherited from base class private way what will happen ?
    what will happen Now again derive class has inherited from second derive class private way what will happen ?

101. what is mutable ?
102. what is stack unwinding ? when does this comes into the picture ?
103. what is size of empty vector?
    i.e. vector <int> a;
         printf ( "sizeof = [%d]", sizeof (a));
    > http://stackoverflow.com/questions/27935802/size-of-empty-vector
104. Functions that cannot be overloaded in C++?
105. Implement your own String class ( behave as string template class ) - write code.
106. How do you restrict class , that it shouldn't be inherited by other class.
107. write macro for largest of two numbers?
108. write macro for to find no of seconds in an year?
109. Is there any problem in the below code , if so how do you correct it
    int fun ( volatile int a ) { return (a * a * a );}
110. Write code - Implement your own CSmartPointers ?
111. Explain about RTTI ?
112. Write code - Delete node at the particular position ( linked list )
113. Write code - Overload assignment \
                  **Overload pre-increment** **\
                  **Overload post-increment** **\
                  Overload new \
                  Overload delete \
                  Overload subscription \
                  Overload dereference \
                  Overload indirection operators?
    (how to overload new[] operator ?)
114. Implement your own Iterator?
115. how to delete array of objects / pointers ?
116. What will be the output? What do you do when it crashes? How do you debug?
```cpp
int main()
{
    int i=0;
    i++; //OR
    cout<<i;//OR
    cout<<i++;//OR
    cout<<++i;//OR
    return 0;
}
```

117. what is the output?
```cpp
class A
{
    int a;
};

int main()
{
A *a = new A;
std::cout <<a << a++ << std::endl; //OR
std::cout <<*a << *a++ << std::endl;
return 0;
}
```
118.   What will happen after retutn statement of a program?
119.   How many static memebers will be created in below program?
```cpp
#include <iostream>
using namespace std;
template <class T>
class A
{
    public:
    static int stat;
};
template <class T>
int A<T>::stat = 10;

int main()
{
A<int> a;
A<float> b;
A<int>::stat = 20;
std::cout << A<int>::stat << std::endl;
std::cout << A<float>::stat << std::endl;
return 0;
}
```

120. What is the output of below program?
```cpp
class B
{
    public:
    int y;
    B():y(25){}
};
template <class T>
class A
{
    public:
    A():x(15){}
    static int stat;
    int x;
    void modify(B& b) const
    {
        b.y = 36;
        //x = 30;
        //Nothing
    }
};
template <class T>
int A<T>::stat = 10;

int main()
{
A<int> a;
A<float> b;
B objb;
std::cout << "Before"<<objb.y << std::endl;
a.modify(objb);
std::cout << objb.y << std::endl;
A<int>::stat = 20;
std::cout << A<int>::stat << std::endl;
std::cout << A<float>::stat << std::endl;
return 0;
}
```

121.   What do you do for below program to work?
```cpp
int main()
{
    classA objA;
    classB objB;
    objA = objB;
}
```

122.   You have a vector VP1 which store pointers to classA instances. How do you create another vector VP2 which is copy of VP1?
123.   write your own vector class which should have push_back, erase, size and capacity functions?
124.   What is the output?
```cpp
class A
{
    public:
    int a;
    int b;
    A(int z):b(z),a(b/5)
    {
        std::cout<< a <<endl;
        std::cout<< b <<endl;
    }
};
int main()
{
    A objA(10);
    return 0;
}
```
125.   Program for Dynamic_Cast between pointers and between references? What will happen in case of success and failure?
126.   You have a class member function something like below.
127.  Write a program ro implement stack.
128.  What if i do not override the pure virtual function?
    > It will not create any error until and unless you try to create an object for class B. 
    > If you try to do below error will come.
    >   PureVirtual.cpp:29:4: error: cannot declare variable ‘objc’ to be of abstract type ‘B’
    >   B objc;
    >        ^
    >   PureVirtual.cpp:11:7: note:   because the following virtual functions are pure within ‘B’:
    >   class B: public A
    >        ^

129.  What is the problem in below program?
```cpp
void square(volatile int* x)
{
    cout<<*x**x; 
}
//Ans: Here With volatile keyword you are telling the compiler that do not optimize x. always take latest value.
// So you may not get square everytime.
```
	 
130.  Queue implementation?
131.  Can structure have constructor, Destructor, Access specifiers and Inheritance?
132.  Is it possible to define Virtual static or virtual const functions ?
133.  How to avoid implicit conversion? 
    ```
    ex: fun(int a) being called by
        fun(10); and fun('c');
    ```

134. static_cast<Base*>(0) -> what it'll give?
135. How do you call base class virtual function with base class pointer pointing
   to Derived class without any major changes in the base class or derived class?
136. What is difference between Vector and List?
137. Difference between Ordered-Map and Un-Ordered Map?
138. How vector reallocates the size when it reaches the capacity?
139. Can a class have an object of self type?
140. When do you need Overloaded new operator? **
141. What is Stack Overflow and Heap Corruption?
142. When and how to use accumulator in C++ ? 
143. What is template specialization? Write an example for function/class template specialization?
144. What is variadic template ?
145. What is the output of below program?
```cpp
#include <iostream>
int main()
{
    int x = 012; // 0 before the number means this is octal
    std::cout << x;
    return 0;
}
```
146. Explain Big Endian and Little Endian?
147. What is Macro stringification?
148. Static linking and Dynamic linking?
149. What are Static and Dynamic libraries?
     > https://www.geeksforgeeks.org/static-vs-dynamic-libraries/
150. What are Atomic functions?
151. Allocating memory to multi dimensional array and accessing elements of a multi dimensional array using pointers or Indexes?
152. Expect the Output in below cases.
```cpp
class Base {
public:
    virtual void fun() { cout << "Base Fun"<<endl; }
};
class Derived: public Base {
    void fun() { cout << "Derived Fun"<<endl; }
};

int main()
{
    //Case 1
    Base *ptr = new Derived;
    ptr->fun();
    //Case 2
    Derived *ptr2 = new Derived;
    ptr2->fun();
    return 0;
}
```

----------------------------------------------------
## Design
- SOLID principles?
- Difference between Aggregation and Composition relationship?
- Dependency injection principle.
- how do you achieve singleton without making constructor as singleton?
- Write code for singleton class? explain problem w.r.t to threading?
- Explain double locking mechanism?
- Factory pattern implementation?
- when do you go for inheratance vs composition ?
- can you give an example has-a (compostion)and is-a relationship(inheritance) ?
- how many types of design pattern ? i.e. creation, behaviour and structural design pattern ?


-------------------------------------------
## Common or Basic questions
- Storage classes in c++?
- copy constructor ? what does copy constructor does ?
- does compiler give default copy constructor ?
- Operators that cannot be overloaded in C++?
- different types of interhitance ?
- what all the features you have touched upon/recently learned on c++ ?
- How your application(project) starts? Explain?
- Pointer Vs reference?
- What are the differences between C and C++?
- Programs on strings – reverse a line, find occurrences of a substring in a string, string length, compare strings, concatenate strings with optimized code.
- Linked list and circular linked list programs?
- Different sorting techniques and searching?
- One iteration solution to find the duplicate element in a. Singly linked list?
- Where does ‘this’ pointer gets stored?

- Brief about project and responsibilities.
- Explain any challenging problem I have till date.


---------------------------------------------
## Threads
- Process vs Thread?
- Can threads will have access to shared memory?
- Producer consumer problem?
- Priority inversion ?
- what is Deadlock?
- thread synchronizations ?
- data synchronization ?
- Can i communicate using shared memory between different process ?
- Using sharedmemory is there any limit , sharing the data between the process ?
- What's the maximum size transferring between the two process using message queue?
- Write code - Treading synchronization problem and explain?
- When do you go semaphore and mutex
- Explain system booting process?
- Can i Use mutex locking in ISR?
- What are spin locks can i use in ISR?
- Why  threads are light weight?
- What is the scenario where you use counting semaphore?
- What are different IPC mechanisms I have used?
- What if message queue is full and when you want to send messages into queue?
- Write a program to print number sequence; Even number in one thread and Odd number from another thread?
- Is Shared pointer thread safe?
- What is Conditional variable? Explain in detail?


---------------------------------------------
## Other Useful Links

C++ : http://www.stroustrup.com/bs_faq2.html#virtual-ctor
      http://www.qnx.com/developers/docs/6.4.1/neutrino/sys_arch/ipc.html#Message_queues

Boost.interprcess : http://www.boost.org/doc/libs/1_52_0/doc/html/interprocess.html
        https://users.cs.cf.ac.uk/Dave.Marshall/C/node31.html#SECTION003110000000000000000

DSA : https://www.cs.auckland.ac.nz/~jmor159/PLDS210/ds_ToC.html

Smart Pointers : https://www.codeproject.com/Articles/541067/Cplusplus-Smart-Pointers

Detailed info about Vtable : http://stackoverflow.com/questions/70682/what-is-the-vtable-layout-and-vtable-pointer-location-in-c-objects-in-gcc-3-x
> Ans: Use "gcc -fdump-class-hierarchy filename.cpp -lstdc++" command to see the content of vtable. "filename.cpp.002t.class" file will be
> generated with content of the above command.

Concurrent Programming with C++11 : https://www.youtube.com/playlist?list=PL5jc9xFGsL8E12so1wlMS0r0hTQoJL74M

Modern C++ : https://www.youtube.com/playlist?list=PL5jc9xFGsL8FWtnZBeTqZBbniyw0uHyaH

C++ 14 : https://www.youtube.com/playlist?list=PLk6CEY9XxSIAloDTEauOy_ss9fEqSP4JR

