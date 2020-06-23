 1. How to write overloaded operator for Obj + 1 and 1+obj ?
  
 2. Abstract classes and Interfaces.
  
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

  3. Can Virtual functions be private in c++?
  4. write a function to overload template function?
  5. what is the value of vptr in case of an Interface class and abstract class?
  6. when do you use volatile keyword?
  7. Time and Space complexity of different container and operations? **
  8. Can inline functions be virtual?
  9. Can a constructor be inline?
  10. Can I overload function of Base in derived?
     
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
  
  11. How to solve problem in above code?

  Modify derived class as below.
	class Derived: public Base {
		public:
			void fun() { cout << "Derived Fun"<<endl; }
			using Base::display; //Bring Base display function to derived class scope.
			void display() // Overloading Base class method will not work.
			{
				cout<<"Derived display"<<endl;
			}
		};
  Can I call a virtual method from constructor ?
  
  Size of an empty class?
  
  Can I through exception in Constructor? Explain in details? **
  
  How to Reduce or avoid padding bits?
  
	#pragma pack(n) //n byte alignment

  
  Output of below program 
  
  class Base1 {
		int x, y;
		public:
			Base1(){cout<<"default constr"<<endl;}
		};
		
		class Base2 {
		int x, y;
		};
  
  int main()
  {
	Base1 b1Obj = {10, 20};
	Base1 b2Obj = {10, 20};
	return 0;
  }
  
  what will happen If I declare a namespace within a class?
  
  What is the order of member initialization in class initializer list?
  
  Do you see any problem in below code snippet and explain?
  
  
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
  
  what is Conversion Constructor and conversion operator?
	* Conversion operator will not have return type but it returns object.
	
  Whar is the size of each struct?
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
	
	
	What is the output ?
	
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
	
	Output of below program?
	
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
		
	What is dangling pointer?
	
	Can we do - delete this; - ?
	
	What is segmentation fault? How do you debug? **
	
		The following are some typical causes of a segmentation fault:
		stack overflow.
		Buffer underflow
		Attempting to access a nonexistent memory address (outside process's address space)
		Attempting to access memory the program does not have rights to (such as kernel structures in process context)
		Attempting to write read-only memory (such as code segment)
			int main(void)
			{
				char *s = "hello world"; // on heap
				*s = 'H'; // read-only memory
			}
		sol: 
			int main(void)
			{
				char s[] = "hello world"; // on stack.
				s[0] = 'H';
			}
	
	What is Placement new operator?
	
	If we try to use memory beyond allocated in placement new.. what will happen?
	
	
  
  
  
  