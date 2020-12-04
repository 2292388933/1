---
id: doc4
title: c#
--- 
## c#程序结构
程序主要包括:
- 命名空间声明（Namespace declaration）
- class
- Class 方法
- 一个 Main 方法<br/>
- 语句（Statements）& 表达式（Expressions）<br/>
- 注释<br/>
"Hello World"
```c#
using System;
namespace HelloWorldApplication
{
   class HelloWorld
   {
      static void Main(string[] args)
      {
         /* 我的第一个 C# 程序*/
         Console.WriteLine("Hello World");
         Console.ReadKey();
      }
   }
}
```
- 程序的第一行using System;-using关键字用于在程序中包含System命名空间。一个程序一般有多个using语句。
- 下一行是namespace声明。一个namespace里包含了一系列的类。HelloWorldApplication命名空间包含了类HelloWorld。
- 下一行是class声明。类HelloWorld包含了程序使用的数据和方法声明。类一般包含多个方法。方法定义了类的行为。在这里，HelloWorld类只有一个Main方法。
- 下一行定义了Main方法，是所有C#程序的入口点。Main方法说明当执行时类将做什么动作。<br/>
- 下一行/*...*/将会被编译器忽略，且它会在程序中添加额外的注释。
- Main方法通过语句Console.WriteLine("Hello World");指定了它的行为。WriteLine是一个定义在System命名空间中的Console类的一个方法。该语句会在屏幕上显示消息"Hello World"。
- 最后一行Console.ReadKey();是针对VS.NET用户的。这使得程序会等待一个按键的动作，防止程序从Visual Studio .NET启动时屏幕会快速运行并关闭。

注意：
- C# 是大小写敏感的。
- 所有的语句和表达式必须以分号（;）结尾。
- 程序的执行从 Main 方法开始。
- 与 Java 不同的是，文件名可以不同于类的名称。

## c#基本语法
以 Rectangle（矩形）对象为例。它具有 length 和 width 属性。
```c#
using System;
namespace RectangleApplication
{
    class Rectangle
    {
        // 成员变量
        double length;
        double width;
        public void Acceptdetails()
        {
            length = 4.5;    
            width = 3.5;
        }
        public double GetArea()
        {
            return length * width;
        }
        public void Display()
        {
            Console.WriteLine("Length: {0}", length);
            Console.WriteLine("Width: {0}", width);
            Console.WriteLine("Area: {0}", GetArea());
        }
    }
   
    class ExecuteRectangle
    {
        static void Main(string[] args)
        {
            Rectangle r = new Rectangle();
            r.Acceptdetails();
            r.Display();
            Console.ReadLine();
        }
    }
}
```
using 关键字<br/>
在任何 C# 程序中的第一条语句都是：
```c#
using System;
```
using 关键字用于在程序中包含命名空间。一个程序可以包含多个 using 语句。

class 关键字<br/>
class 关键字用于声明一个类。

实例化一个类<br/>
在上面的程序中，类 ExecuteRectangle 是一个包含 Main() 方法和实例化 Rectangle 类的类。

标识符<br/>
标识符是用来识别类、变量、函数或任何其它用户定义的项目。在 C# 中，类的命名必须遵循如下基本规则：
- 标识符必须以字母、下划线或 @ 开头，后面可以跟一系列的字母、数字（ 0 - 9 ）、下划线（ _ ）、@。
- 标识符中的第一个字符不能是数字。
- 标识符必须不包含任何嵌入的空格或符号，比如 ? - +! # % ^ & * ( ) [ ] { } . ; : " ' / \。
- 标识符不能是 C# 关键字。除非它们有一个 @ 前缀。 例如，@if 是有效的标识符，但 if 不是，因为 if 是关键字。
- 标识符必须区分大小写。大写字母和小写字母被认为是不同的字母。
- 不能与C#的类库名称相同。

C# 关键字
关键字是 C# 编译器预定义的保留字。这些关键字不能用作标识符，但是，如果您想使用这些关键字作为标识符，可以在关键字前面加上 @ 字符作为前缀。<br/>
在 C# 中，有些关键字在代码的上下文中有特殊的意义，如 get 和 set，这些被称为上下文关键字（contextual keywords）。<br/>

## c#数据类型
在 C# 中，变量分为以下几种类型：
- 值类型（Value types）
- 引用类型（Reference types
- 指针类型（Pointer types）
值类型（Value types）<br/>
值类型变量可以直接分配给一个值。它们是从类 System.ValueType 中派生的。<br/>
值类型直接包含数据。比如 int、char、float，它们分别存储数字、字符、浮点数。当您声明一个 int 类型时，系统分配内存来存储值。<br/>
如需得到一个类型或一个变量在特定平台上的准确尺寸，可以使用 sizeof 方法。表达式 sizeof(type) 产生以字节为单位存储对象或类型的存储尺寸。下面举例获取任何机器上 int 类型的存储尺寸：
```c#
using System;

namespace DataTypeApplication
{
   class Program
   {
      static void Main(string[] args)
      {
         Console.WriteLine("Size of int: {0}", sizeof(int));
         Console.ReadLine();
      }
   }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
Size of int: 4
```
引用类型（Reference types）<br/>
引用类型不包含存储在变量中的实际数据，但它们包含对变量的引用。<br/>
换句话说，它们指的是一个内存位置。使用多个变量时，引用类型可以指向一个内存位置。如果内存位置的数据是由一个变量改变的，其他变量会自动反映这种值的变化。内置的 引用类型有：object、dynamic 和 string。

对象（Object）类型<br/>
对象（Object）类型 是 C# 通用类型系统（Common Type System - CTS）中所有数据类型的终极基类。Object 是 System.Object 类的别名。所以对象（Object）类型可以被分配任何其他类型（值类型、引用类型、预定义类型或用户自定义类型）的值。但是，在分配值之前，需要先进行类型转换。<br/>
当一个值类型转换为对象类型时，则被称为 装箱；另一方面，当一个对象类型转换为值类型时，则被称为 拆箱。
```c#
object obj;
obj = 100; // 这是装箱
```
动态（Dynamic）类型<br/>
您可以存储任何类型的值在动态数据类型变量中。这些变量的类型检查是在运行时发生的。<br/>
声明动态类型的语法：
```c#
dynamic <variable_name> = value;
```
例如
```c#
dynamic d = 20;
```
动态类型与对象类型相似，但是对象类型变量的类型检查是在编译时发生的，而动态类型变量的类型检查是在运行时发生的。

字符串（String）类型<br/>
字符串（String）类型 允许您给变量分配任何字符串值。字符串（String）类型是 System.String 类的别名。它是从对象（Object）类型派生的。字符串（String）类型的值可以通过两种形式进行分配：引号和 @引号。<br/>
例如：
```c#
String str = "runoob.com";
```
一个 @引号字符串：
```c#
@"runoob.com";
```
C# string 字符串的前面可以加 @（称作"逐字字符串"）将转义字符（\）当作普通字符对待，比如：
```c#
string str = @"C:\Windows";
```
@ 字符串中可以任意换行，换行符及缩进空格都计算在字符串长度之内
```c#
string str = @"<script type=""text/javascript"">
    <!--
    -->
</script>";
```
用户自定义引用类型有：class、interface 或 delegate。

指针类型（Pointer types）<br/>
指针类型变量存储另一种类型的内存地址。C# 中的指针与 C 或 C++ 中的指针有相同的功能。<br/>
声明指针类型的语法：
```c#
type* identifier;
```
例如：
```c#
char* cptr;
int* iptr;
```

# c#类型转换
类型转换从根本上说是类型铸造，或者说是把数据从一种类型转换为另一种类型。在 C# 中，类型铸造有两种形式：
- 隐式类型转换 - 这些转换是 C# 默认的以安全方式进行的转换, 不会导致数据丢失。例如，从小的整数类型转换为大的整数类型，从派生类转换为基类。
- 显式类型转换 - 显式类型转换，即强制类型转换。显式转换需要强制转换运算符，而且强制转换会造成数据丢失。<br/>
下面的实例显示了一个显式的类型转换：
```c#
namespace TypeConversionApplication
{
    class ExplicitConversion
    {
        static void Main(string[] args)
        {
            double d = 5673.74;
            int i;

            // 强制转换 double 为 int
            i = (int)d;
            Console.WriteLine(i);
            Console.ReadKey();
           
        }
    }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
5673
```
C# 类型转换方法<br/>
C# 提供了下列内置的类型转换方法：
1. ToBoolean 如果可能的话，把类型转换为布尔型。
1. ToByte 把类型转换为字节类型。
1. ToChar 如果可能的话，把类型转换为单个 Unicode 字符类型。
1. ToDateTime 把类型（整数或字符串类型）转换为 日期-时间 结构。
1. ToDecimal 把浮点型或整数类型转换为十进制类型。
1. ToDouble 把类型转换为双精度浮点型。
1. ToInt16 把类型转换为 16 位整数类型。
1. ToInt32 把类型转换为 32 位整数类型。
1. ToInt64 把类型转换为 64 位整数类型。
1. ToSbyte 把类型转换为有符号字节类型。
1. ToSingle 把类型转换为小浮点数类型。
1. ToString 把类型转换为字符串类型。
1. ToType 把类型转换为指定类型。
1. ToUInt16 把类型转换为 16 位无符号整数类型。
1. ToUInt32 把类型转换为 32 位无符号整数类型。
1. ToUInt64 把类型转换为 64 位无符号整数类型。<br/>
下面的实例把不同值的类型转换为字符串类型：
```c#
namespace TypeConversionApplication
{
    class StringConversion
    {
        static void Main(string[] args)
        {
            int i = 75;
            float f = 53.005f;
            double d = 2345.7652;
            bool b = true;

            Console.WriteLine(i.ToString());
            Console.WriteLine(f.ToString());
            Console.WriteLine(d.ToString());
            Console.WriteLine(b.ToString());
            Console.ReadKey();
           
        }
    }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
75
53.005
2345.7652
True
```

c#变量
- 
C# 中的变量定义<br/>
C# 中变量定义的语法：
```c#
<data_type> <variable_list>;
```
在这里，data_type 必须是一个有效的 C# 数据类型，可以是 char、int、float、double 或其他用户自定义的数据类型。variable_list 可以由一个或多个用逗号分隔的标识符名称组成。

C# 中的变量初始化<br/>
变量通过在等号后跟一个常量表达式进行初始化（赋值）。初始化的一般形式为：
```c#
variable_name = value;
```
变量可以在声明时被初始化（指定一个初始值）。初始化由一个等号后跟一个常量表达式组成，如下所示：
```c#
<data_type> <variable_name> = value;
```
接受来自用户的值<br/>
System 命名空间中的 Console 类提供了一个函数 ReadLine()，用于接收来自用户的输入，并把它存储到一个变量中。<br/>
例如：
```c#
int num;
num = Convert.ToInt32(Console.ReadLine());
```
函数 Convert.ToInt32() 把用户输入的数据转换为 int 数据类型，因为 Console.ReadLine() 只接受字符串格式的数据。

C# 中的 Lvalues 和 Rvalues<br/>
C# 中的两种表达式：
1. lvalue：lvalue 表达式可以出现在赋值语句的左边或右边。
1. rvalue：rvalue 表达式可以出现在赋值语句的右边，不能出现在赋值语句的左边。<br/>
变量是 lvalue 的，所以可以出现在赋值语句的左边。数值是 rvalue 的，因此不能被赋值，不能出现在赋值语句的左边。

c#常量
- 
字符串常量<br/>
字符串常量是括在双引号 "" 里，或者是括在 @"" 里。字符串常量包含的字符与字符常量相似，可以是：普通字符、转义序列和通用字符<br/>
使用字符串常量时，可以把一个很长的行拆成多个行，可以使用空格分隔各个部分。<br/>
这里是一些字符串常量的实例。下面所列的各种形式表示相同的字符串。<br/>
```c#
string a = "hello, world";                  // hello, world
string b = @"hello, world";               // hello, world
string c = "hello \t world";               // hello     world
string d = @"hello \t world";               // hello \t world
string e = "Joe said \"Hello\" to me";      // Joe said "Hello" to me
string f = @"Joe said ""Hello"" to me";   // Joe said "Hello" to me
string g = "\\\\server\\share\\file.txt";   // \\server\share\file.txt
string h = @"\\server\share\file.txt";      // \\server\share\file.txt
string i = "one\r\ntwo\r\nthree";
string j = @"one
two
three";
```
定义常量<br/>
常量是使用 const 关键字来定义的 。定义一个常量的语法如下：
```c#
const <data_type> <constant_name> = value;
```
下面的代码演示了如何在程序中定义和使用常量：
```c#
using System;

public class ConstTest
{
    class SampleClass
    {
        public int x;
        public int y;
        public const int c1 = 5;
        public const int c2 = c1 + 5;

        public SampleClass(int p1, int p2)
        {
            x = p1;
            y = p2;
        }
    }

    static void Main()
    {
        SampleClass mC = new SampleClass(11, 22);
        Console.WriteLine("x = {0}, y = {1}", mC.x, mC.y);
        Console.WriteLine("c1 = {0}, c2 = {1}",
                          SampleClass.c1, SampleClass.c2);
    }
}
```
当上面的代码被编译和执行时，它会产生下列结果：

```c#
x = 11, y = 22
c1 = 5, c2 = 10
```
c#循环
- 
foreach<br/>
C# 也支持 foreach 循环，使用foreach可以迭代数组或者一个集合对象。<br/>
以下实例有三个部分：
- 通过 foreach 循环输出整型数组中的元素。
- 通过 for 循环输出整型数组中的元素。
- foreach 循环设置数组元素的计算器。
```c#
class ForEachTest
{
    static void Main(string[] args)
    {
        int[] fibarray = new int[] { 0, 1, 1, 2, 3, 5, 8, 13 };
        foreach (int element in fibarray)
        {
            System.Console.WriteLine(element);
        }
        System.Console.WriteLine();


        // 类似 foreach 循环
        for (int i = 0; i < fibarray.Length; i++)
        {
            System.Console.WriteLine(fibarray[i]);
        }
        System.Console.WriteLine();


        // 设置集合中元素的计算器
        int count = 0;
        foreach (int element in fibarray)
        {
            count += 1;
            System.Console.WriteLine("Element #{0}: {1}", count, element);
        }
        System.Console.WriteLine("Number of elements in the array: {0}", count);
    }
}
```
输出结果为：
```c#
0
1
1
2
3
5
8
13

0
1
1
2
3
5
8
13

Element #1: 0
Element #2: 1
Element #3: 1
Element #4: 2
Element #5: 3
Element #6: 5
Element #7: 8
Element #8: 13
Number of elements in the array: 8
```
c#封装
- 
封装被定义为"把一个或多个项目封闭在一个物理的或者逻辑的包中"。在面向对象程序设计方法论中，封装是为了防止对实现细节的访问。<br/>
抽象和封装是面向对象程序设计的相关特性。抽象允许相关信息可视化，封装则使开发者实现所需级别的抽象。<br/>
C#封装根据具体的需要，设置使用者的访问权限，并通过访问修饰符来实现。<br/>
一个访问修饰符定义了一个类成员的范围和可见性。C#支持的访问修饰符如下所示：<br/>
- public：所有对象都可以访问;
- private：对象本身在对象内部可以访问;
- protected：只有该类对象及其子类对象可以访问;
- internal：同一个程序集的对象可以访问;
- protected internal：访问限于当前程序集或派生自包含类的类型。
Public 访问修饰符<br/>
Public 访问修饰符允许一个类将其成员变量和成员函数暴露给其他的函数和对象。任何公有成员可以被外部的类访问。
下面的实例说明了这点：
```c#
using System;

namespace RectangleApplication
{
    class Rectangle
    {
        //成员变量
        public double length;
        public double width;

        public double GetArea()
        {
            return length * width;
        }
        public void Display()
        {
            Console.WriteLine("长度： {0}", length);
            Console.WriteLine("宽度： {0}", width);
            Console.WriteLine("面积： {0}", GetArea());
        }
    }// Rectangle 结束

    class ExecuteRectangle
    {
        static void Main(string[] args)
        {
            Rectangle r = new Rectangle();
            r.length = 4.5;
            r.width = 3.5;
            r.Display();
            Console.ReadLine();
        }
    }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
长度： 4.5
宽度： 3.5
面积： 15.75
```
在上面的实例中，成员变量 length 和 width 被声明为 public，所以它们可以被函数 Main() 使用 Rectangle 类的实例 r 访问。<br/>
成员函数 Display() 和 GetArea() 可以直接访问这些变量。<br/>
成员函数 Display() 也被声明为 public，所以它也能被 Main() 使用 Rectangle 类的实例 r 访问。<br/>
Private 访问修饰符<br/>
Private 访问修饰符允许一个类将其成员变量和成员函数对其他的函数和对象进行隐藏。只有同一个类中的函数可以访问它的私有成员。即使是类的实例也不能访问它的私有成员。<br/>
下面的实例说明了这点：
```c#
using System;

namespace RectangleApplication
{
    class Rectangle
    {
        //成员变量
        private double length;
        private double width;

        public void Acceptdetails()
        {
            Console.WriteLine("请输入长度：");
            length = Convert.ToDouble(Console.ReadLine());
            Console.WriteLine("请输入宽度：");
            width = Convert.ToDouble(Console.ReadLine());
        }
        public double GetArea()
        {
            return length * width;
        }
        public void Display()
        {
            Console.WriteLine("长度： {0}", length);
            Console.WriteLine("宽度： {0}", width);
            Console.WriteLine("面积： {0}", GetArea());
        }
    }//end class Rectangle    
    class ExecuteRectangle
    {
        static void Main(string[] args)
        {
            Rectangle r = new Rectangle();
            r.Acceptdetails();
            r.Display();
            Console.ReadLine();
        }
    }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
请输入长度：
4.4
请输入宽度：
3.3
长度： 4.4
宽度： 3.3
面积： 14.52
```
在上面的实例中，成员变量 length 和 width 被声明为 private，所以它们不能被函数 Main() 访问。<br/>
成员函数 AcceptDetails() 和 Display() 可以访问这些变量。<br/>
由于成员函数 AcceptDetails() 和 Display() 被声明为 public，所以它们可以被 Main() 使用 Rectangle 类的实例 r 访问。<br/>
Protected 访问修饰符<br/>
Protected 访问修饰符允许子类访问它的基类的成员变量和成员函数。这样有助于实现继承。我们将在继承的章节详细讨论这个。更详细地讨论这个。<br/>
Internal 访问修饰符<br/>
Internal 访问说明符允许一个类将其成员变量和成员函数暴露给当前程序中的其他函数和对象。换句话说，带有 internal 访问修饰符的任何成员可以被定义在该成员所定义的应用程序内的任何类或方法访问。<br/>
下面的实例说明了这点：
```c#
using System;

namespace RectangleApplication
{
    class Rectangle
    {
        //成员变量
        internal double length;
        internal double width;
       
        double GetArea()
        {
            return length * width;
        }
       public void Display()
        {
            Console.WriteLine("长度： {0}", length);
            Console.WriteLine("宽度： {0}", width);
            Console.WriteLine("面积： {0}", GetArea());
        }
    }//end class Rectangle    
    class ExecuteRectangle
    {
        static void Main(string[] args)
        {
            Rectangle r = new Rectangle();
            r.length = 4.5;
            r.width = 3.5;
            r.Display();
            Console.ReadLine();
        }
    }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
长度： 4.5
宽度： 3.5
面积： 15.75
```
在上面的实例中，请注意成员函数 GetArea() 声明的时候不带有任何访问修饰符。如果没有指定访问修饰符，则使用类成员的默认访问修饰符，即为 private。<br/>
Protected Internal 访问修饰符<br/>
Protected Internal 访问修饰符允许在本类,派生类或者包含该类的程序集中访问。这也被用于实现继承。

c#方法
- 
C# 中定义方法<br/>
当定义一个方法时，从根本上说是在声明它的结构的元素。在 C# 中，定义方法的语法如下：
```c#
<Access Specifier> <Return Type> <Method Name>(Parameter List)
{
   Method Body
}
```
下面是方法的各个元素：
- Access Specifier：访问修饰符，这个决定了变量或方法对于另一个类的可见性。
- Return type：返回类型，一个方法可以返回一个值。返回类型是方法返回的值的数据类型。如果方法不返回任何值，则返回类型为 void。
- Method name：方法名称，是一个唯一的标识符，且是大小写敏感的。它不能与类中声明的其他标识符相同。
- Parameter list：参数列表，使用圆括号括起来，该参数是用来传递和接收方法的数据。参数列表是指方法的参数类型、顺序和数量。参数是可选的，也就是说，一个方法可能不包含参数。
- Method body：方法主体，包含了完成任务所需的指令集。
实例:下面的代码片段显示一个函数 FindMax，它接受两个整数值，并返回两个中的较大值。它有 public 访问修饰符，所以它可以使用类的实例从类的外部进行访问。
```c#
class NumberManipulator
{
   public int FindMax(int num1, int num2)
   {
      /* 局部变量声明 */
      int result;

      if (num1 > num2)
         result = num1;
      else
         result = num2;

      return result;
   }
   ...
}
```
C# 中调用方法<br/>
您可以使用方法名调用方法。下面的实例演示了这点：
```c#
using System;

namespace CalculatorApplication
{
   class NumberManipulator
   {
      public int FindMax(int num1, int num2)
      {
         /* 局部变量声明 */
         int result;

         if (num1 > num2)
            result = num1;
         else
            result = num2;

         return result;
      }
      static void Main(string[] args)
      {
         /* 局部变量定义 */
         int a = 100;
         int b = 200;
         int ret;
         NumberManipulator n = new NumberManipulator();

         //调用 FindMax 方法
         ret = n.FindMax(a, b);
         Console.WriteLine("最大值是： {0}", ret );
         Console.ReadLine();
      }
   }
}
```
当上面的代码被编译和执行时，它会产生下列结果:
```c#
最大值是： 200
```
您也可以使用类的实例从另一个类中调用其他类的公有方法。例如，方法 FindMax 属于 NumberManipulator 类，您可以从另一个类 Test 中调用它。
```c#
using System;

namespace CalculatorApplication
{
    class NumberManipulator
    {
        public int FindMax(int num1, int num2)
        {
            /* 局部变量声明 */
            int result;

            if (num1 > num2)
                result = num1;
            else
                result = num2;

            return result;
        }
    }
    class Test
    {
        static void Main(string[] args)
        {
            /* 局部变量定义 */
            int a = 100;
            int b = 200;
            int ret;
            NumberManipulator n = new NumberManipulator();
            //调用 FindMax 方法
            ret = n.FindMax(a, b);
            Console.WriteLine("最大值是： {0}", ret );
            Console.ReadLine();

        }
    }
}
```
当上面的代码被编译和执行时，它会产生下列结果:
```c#
最大值是： 200
```
按值传递参数<br/>
这是参数传递的默认方式。在这种方式下，当调用一个方法时，会为每个值参数创建一个新的存储位置。<br/>
实际参数的值会复制给形参，实参和形参使用的是两个不同内存中的值。所以，当形参的值发生改变时，不会影响实参的值，从而保证了实参数据的安全。下面的实例演示了这个概念：
```c#
using System;
namespace CalculatorApplication
{
   class NumberManipulator
   {
      public void swap(int x, int y)
      {
         int temp;
         
         temp = x; /* 保存 x 的值 */
         x = y;    /* 把 y 赋值给 x */
         y = temp; /* 把 temp 赋值给 y */
      }
     
      static void Main(string[] args)
      {
         NumberManipulator n = new NumberManipulator();
         /* 局部变量定义 */
         int a = 100;
         int b = 200;
         
         Console.WriteLine("在交换之前，a 的值： {0}", a);
         Console.WriteLine("在交换之前，b 的值： {0}", b);
         
         /* 调用函数来交换值 */
         n.swap(a, b);
         
         Console.WriteLine("在交换之后，a 的值： {0}", a);
         Console.WriteLine("在交换之后，b 的值： {0}", b);
         
         Console.ReadLine();
      }
   }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
在交换之前，a 的值：100
在交换之前，b 的值：200
在交换之后，a 的值：100
在交换之后，b 的值：200
```
结果表明，即使在函数内改变了值，值也没有发生任何的变化。
按引用传递参数<br/>
引用参数是一个对变量的内存位置的引用。当按引用传递参数时，与值参数不同的是，它不会为这些参数创建一个新的存储位置。引用参数表示与提供给方法的实际参数具有相同的内存位置。<br/>
在 C# 中，使用 ref 关键字声明引用参数。下面的实例演示了这点：
```c#
using System;
namespace CalculatorApplication
{
   class NumberManipulator
   {
      public void swap(ref int x, ref int y)
      {
         int temp;

         temp = x; /* 保存 x 的值 */
         x = y;    /* 把 y 赋值给 x */
         y = temp; /* 把 temp 赋值给 y */
       }
   
      static void Main(string[] args)
      {
         NumberManipulator n = new NumberManipulator();
         /* 局部变量定义 */
         int a = 100;
         int b = 200;

         Console.WriteLine("在交换之前，a 的值： {0}", a);
         Console.WriteLine("在交换之前，b 的值： {0}", b);

         /* 调用函数来交换值 */
         n.swap(ref a, ref b);

         Console.WriteLine("在交换之后，a 的值： {0}", a);
         Console.WriteLine("在交换之后，b 的值： {0}", b);
 
         Console.ReadLine();

      }
   }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
在交换之前，a 的值：100
在交换之前，b 的值：200
在交换之后，a 的值：200
在交换之后，b 的值：100
```
结果表明，swap 函数内的值改变了，且这个改变可以在 Main 函数中反映出来。<br/>
提供给输出参数的变量不需要赋值。当需要从一个参数没有指定初始值的方法中返回值时，输出参数特别有用。请看下面的实例，来理解这一点：
```c#
using System;

namespace CalculatorApplication
{
   class NumberManipulator
   {
      public void getValues(out int x, out int y )
      {
          Console.WriteLine("请输入第一个值： ");
          x = Convert.ToInt32(Console.ReadLine());
          Console.WriteLine("请输入第二个值： ");
          y = Convert.ToInt32(Console.ReadLine());
      }
   
      static void Main(string[] args)
      {
         NumberManipulator n = new NumberManipulator();
         /* 局部变量定义 */
         int a , b;
         
         /* 调用函数来获取值 */
         n.getValues(out a, out b);

         Console.WriteLine("在方法调用之后，a 的值： {0}", a);
         Console.WriteLine("在方法调用之后，b 的值： {0}", b);
         Console.ReadLine();
      }
   }
}
```
当上面的代码被编译和执行时，它会产生下列结果（取决于用户输入）：
```c#
请输入第一个值：
7
请输入第二个值：
8
在方法调用之后，a 的值： 7
在方法调用之后，b 的值： 8
```
C＃可空类型（可空）<br/>
？：单问号用于对int，double，bool等无法直接赋值的null的数据类型进行null的赋值，意思是这个数据类型是Nullable类型的。
```c#
int? i = 3;
```
等同于：
```
Nullable<int> i = new Nullable<int>(3);
int i; //默认值0
int? ii; //默认值null
```
?? ：双问号可用于判断一个变量在为null时返回一个指定的值。<br/>
接下来我们详细说明。<br/>
C＃可空类型（Nullable）<br/>
C＃提供了一个特殊的数据类型，nullable类型（可空类型），可空类型可以表示其基础值类型正常范围内的值，再加上一个null值。<br/>
声明一个nullable类型（可空类型）的语法如下：
```c#
< data_type> ? <variable_name> = null;
```
下面的实例演示了可空数据类型的用法：
```c#
using System;
namespace CalculatorApplication
{
   class NullablesAtShow
   {
      static void Main(string[] args)
      {
         int? num1 = null;
         int? num2 = 45;
         double? num3 = new double?();
         double? num4 = 3.14157;
         
         bool? boolval = new bool?();

         // 显示值
         
         Console.WriteLine("显示可空类型的值： {0}, {1}, {2}, {3}",
                            num1, num2, num3, num4);
         Console.WriteLine("一个可空的布尔值： {0}", boolval);
         Console.ReadLine();

      }
   }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
显示可空类型的值： , 45,  , 3.14157
一个可空的布尔值：
```
Null 合并运算符（ ?? ）<br/>
Null 合并运算符用于定义可空类型和引用类型的默认值。Null 合并运算符为类型转换定义了一个预设值，以防可空类型的值为 Null。Null 合并运算符把操作数类型隐式转换为另一个可空（或不可空）的值类型的操作数的类型。<br/>
如果第一个操作数的值为 null，则运算符返回第二个操作数的值，否则返回第一个操作数的值。下面的实例演示了这点：
using System;
namespace CalculatorApplication
{
   class NullablesAtShow
   {
         
      static void Main(string[] args)
      {
         
         double? num1 = null;
         double? num2 = 3.14157;
         double num3;
         num3 = num1 ?? 5.34;      // num1 如果为空值则返回 5.34
         Console.WriteLine("num3 的值： {0}", num3);
         num3 = num2 ?? 5.34;
         Console.WriteLine("num3 的值： {0}", num3);
         Console.ReadLine();

      }
   }
}
当上面的代码被编译和执行时，它会产生下列结果：
```c#
num3 的值： 5.34
num3 的值： 3.14157
```

C# 数组（Array）
- 
声明数组<br/>
在 C# 中声明一个数组，您可以使用下面的语法：
```c#
datatype[] arrayName;
```
其中，
- datatype 用于指定被存储在数组中的元素的类型。
- [ ] 指定数组的秩（维度）。秩指定数组的大小。
- arrayName 指定数组的名称。
例如：
```c#
double[] balance;
```
初始化数组<br/>
声明一个数组不会在内存中初始化数组。当初始化数组变量时，您可以赋值给数组。<br/>
数组是一个引用类型，所以您需要使用 new 关键字来创建数组的实例。<br/>
例如：
```c#
double[] balance = new double[10];
```
赋值给数组<br/>
您可以通过使用索引号赋值给一个单独的数组元素，比如：
```c#
double[] balance = new double[10];
balance[0] = 4500.0;
```
您可以在声明数组的同时给数组赋值，比如：
```c#
double[] balance = { 2340.0, 4523.69, 3421.0};
```
您也可以创建并初始化一个数组，比如：
```c#
int [] marks = new int[5]  { 99,  98, 92, 97, 95};
```
在上述情况下，你也可以省略数组的大小，比如：
```c#
int [] marks = new int[]  { 99,  98, 92, 97, 95};
```
您也可以赋值一个数组变量到另一个目标数组变量中。在这种情况下，目标和源会指向相同的内存位置：
```c#
int [] marks = new int[]  { 99,  98, 92, 97, 95};
int[] score = marks;
```
当您创建一个数组时，C# 编译器会根据数组类型隐式初始化每个数组元素为一个默认值。例如，int 数组的所有元素都会被初始化为 0。<br/>
访问数组元素<br/>
元素是通过带索引的数组名称来访问的。这是通过把元素的索引放置在数组名称后的方括号中来实现的。例如：
```c#
double salary = balance[9];
```
下面是一个实例，使用上面提到的三个概念，即声明、赋值、访问数组：
```c#
using System;
namespace ArrayApplication
{
   class MyArray
   {
      static void Main(string[] args)
      {
         int []  n = new int[10]; /* n 是一个带有 10 个整数的数组 */
         int i,j;


         /* 初始化数组 n 中的元素 */        
         for ( i = 0; i < 10; i++ )
         {
            n[ i ] = i + 100;
         }

         /* 输出每个数组元素的值 */
         for (j = 0; j < 10; j++ )
         {
            Console.WriteLine("Element[{0}] = {1}", j, n[j]);
         }
         Console.ReadKey();
      }
   }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
Element[0] = 100
Element[1] = 101
Element[2] = 102
Element[3] = 103
Element[4] = 104
Element[5] = 105
Element[6] = 106
Element[7] = 107
Element[8] = 108
Element[9] = 109
```
使用 foreach 循环<br/>
在前面的实例中，我们使用一个 for 循环来访问每个数组元素。您也可以使用一个 foreach 语句来遍历数组。
```c#
using System;

namespace ArrayApplication
{
   class MyArray
   {
      static void Main(string[] args)
      {
         int []  n = new int[10]; /* n 是一个带有 10 个整数的数组 */


         /* 初始化数组 n 中的元素 */        
         for ( int i = 0; i < 10; i++ )
         {
            n[i] = i + 100;
         }

         /* 输出每个数组元素的值 */
         foreach (int j in n )
         {
            int i = j-100;
            Console.WriteLine("Element[{0}] = {1}", i, j);
         }
         Console.ReadKey();
      }
   }
}
```

c#字符串
- 
创建 String 对象<br/>
您可以使用以下方法之一来创建 string 对象：
- 通过给 String 变量指定一个字符串
- 通过使用 String 类构造函数
- 通过使用字符串串联运算符（ + ）
- 通过检索属性或调用一个返回字符串的方法
- 通过格式化方法来转换一个值或对象为它的字符串表示形式
下面的实例演示了这点：
```c#
using System;
     
     namespace StringApplication
     {
         class Program
         {
             static void Main(string[] args)
             {
                //字符串，字符串连接
                 string fname, lname;
                 fname = "Rowan";
                 lname = "Atkinson";
     
                 string fullname = fname + lname;
                 Console.WriteLine("Full Name: {0}", fullname);
     
                 //通过使用 string 构造函数
                 char[] letters = { 'H', 'e', 'l', 'l','o' };
                 string greetings = new string(letters);
                 Console.WriteLine("Greetings: {0}", greetings);
     
                 //方法返回字符串
                 string[] sarray = { "Hello", "From", "Tutorials", "Point" };
                 string message = String.Join(" ", sarray);
                 Console.WriteLine("Message: {0}", message);
     
                 //用于转化值的格式化方法
                 DateTime waiting = new DateTime(2012, 10, 10, 17, 58, 1);
                 string chat = String.Format("Message sent at {0:t} on {0:D}",
                 waiting);
                 Console.WriteLine("Message: {0}", chat);
                 Console.ReadKey() ;
             }
         }
     }
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
Full Name: RowanAtkinson
Greetings: Hello
Message: Hello From Tutorials Point
Message: Message sent at 17:58 on Wednesday, 10 October 2012
```

c#结构体
- 
定义结构体：为了定义一个结构体，您必须使用 struct 语句。struct 语句为程序定义了一个带有多个成员的新的数据类型。<br/>
例如，您可以按照如下的方式声明 Book 结构：
```c#
struct Books
{
   public string title;
   public string author;
   public string subject;
   public int book_id;
};
```
下面的程序演示了结构的用法：
```c#
using System;
using System.Text;
     
struct Books
{
   public string title;
   public string author;
   public string subject;
   public int book_id;
};  

public class testStructure
{
   public static void Main(string[] args)
   {

      Books Book1;        /* 声明 Book1，类型为 Books */
      Books Book2;        /* 声明 Book2，类型为 Books */

      /* book 1 详述 */
      Book1.title = "C Programming";
      Book1.author = "Nuha Ali";
      Book1.subject = "C Programming Tutorial";
      Book1.book_id = 6495407;

      /* book 2 详述 */
      Book2.title = "Telecom Billing";
      Book2.author = "Zara Ali";
      Book2.subject =  "Telecom Billing Tutorial";
      Book2.book_id = 6495700;

      /* 打印 Book1 信息 */
      Console.WriteLine( "Book 1 title : {0}", Book1.title);
      Console.WriteLine("Book 1 author : {0}", Book1.author);
      Console.WriteLine("Book 1 subject : {0}", Book1.subject);
      Console.WriteLine("Book 1 book_id :{0}", Book1.book_id);

      /* 打印 Book2 信息 */
      Console.WriteLine("Book 2 title : {0}", Book2.title);
      Console.WriteLine("Book 2 author : {0}", Book2.author);
      Console.WriteLine("Book 2 subject : {0}", Book2.subject);
      Console.WriteLine("Book 2 book_id : {0}", Book2.book_id);      

      Console.ReadKey();

   }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
Book 1 title : C Programming
Book 1 author : Nuha Ali
Book 1 subject : C Programming Tutorial
Book 1 book_id : 6495407
Book 2 title : Telecom Billing
Book 2 author : Zara Ali
Book 2 subject : Telecom Billing Tutorial
Book 2 book_id : 6495700
```
C# 结构的特点<br/>
您已经用了一个简单的名为 Books 的结构。在 C# 中的结构与传统的 C 或 C++ 中的结构不同。C# 中的结构有以下特点：
- 结构可带有方法、字段、索引、属性、运算符方法和事件。
- 结构可定义构造函数，但不能定义析构函数。但是，您不能为结构定义无参构造函数。无参构造函数(默认)是自动定义的，且不能被改变。
- 与类不同，结构不能继承其他的结构或类。
- 结构不能作为其他结构或类的基础结构。
- 结构可实现一个或多个接口。
- 结构成员不能指定为 abstract、virtual 或 protected。
- 当您使用 New 操作符创建一个结构对象时，会调用适当的构造函数来创建结构。与类不同，结构可以不使用 New 操作符即可被实例化。
- 如果不使用 New 操作符，只有在所有的字段都被初始化之后，字段才被赋值，对象才被使用。
类 vs 结构<br/>
类和结构有以下几个基本的不同点：
- 类是引用类型，结构是值类型。
- 结构不支持继承。
- 结构不能声明默认的构造函数。
针对上述讨论，让我们重写前面的实例：
```c#
using System;
using System.Text;
     
struct Books
{
   private string title;
   private string author;
   private string subject;
   private int book_id;
   public void setValues(string t, string a, string s, int id)
   {
      title = t;
      author = a;
      subject = s;
      book_id =id;
   }
   public void display()
   {
      Console.WriteLine("Title : {0}", title);
      Console.WriteLine("Author : {0}", author);
      Console.WriteLine("Subject : {0}", subject);
      Console.WriteLine("Book_id :{0}", book_id);
   }

};  

public class testStructure
{
   public static void Main(string[] args)
   {

      Books Book1 = new Books(); /* 声明 Book1，类型为 Books */
      Books Book2 = new Books(); /* 声明 Book2，类型为 Books */

      /* book 1 详述 */
      Book1.setValues("C Programming",
      "Nuha Ali", "C Programming Tutorial",6495407);

      /* book 2 详述 */
      Book2.setValues("Telecom Billing",
      "Zara Ali", "Telecom Billing Tutorial", 6495700);

      /* 打印 Book1 信息 */
      Book1.display();

      /* 打印 Book2 信息 */
      Book2.display();

      Console.ReadKey();

   }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
Title : C Programming
Author : Nuha Ali
Subject : C Programming Tutorial
Book_id : 6495407
Title : Telecom Billing
Author : Zara Ali
Subject : Telecom Billing Tutorial
Book_id : 6495700
```

c#类（Class）
- 
类的定义<br/>
类的定义是以关键字 class 开始，后跟类的名称。类的主体，包含在一对花括号内。下面是类定义的一般形式：
```c#
<access specifier> class  class_name
{
    // member variables
    <access specifier> <data type> variable1;
    <access specifier> <data type> variable2;
    ...
    <access specifier> <data type> variableN;
    // member methods
    <access specifier> <return type> method1(parameter_list)
    {
        // method body
    }
    <access specifier> <return type> method2(parameter_list)
    {
        // method body
    }
    ...
    <access specifier> <return type> methodN(parameter_list)
    {
        // method body
    }
}
```
请注意：
- 访问标识符 access specifier 指定了对类及其成员的访问规则。如果没有指定，则使用默认的访问标识符。类的默认访问标识符是 internal，成员的默认访问标识符是 private。
- 数据类型 data type 指定了变量的类型，返回类型 return type 指定了返回的方法返回的数据类型。
- 如果要访问类的成员，你要使用点（.）运算符。
- 点运算符链接了对象的名称和成员的名称。
下面的实例说明了目前为止所讨论的概念：
```c#
using System;
namespace BoxApplication
{
    class Box
    {
       public double length;   // 长度
       public double breadth;  // 宽度
       public double height;   // 高度
    }
    class Boxtester
    {
        static void Main(string[] args)
        {
            Box Box1 = new Box();        // 声明 Box1，类型为 Box
            Box Box2 = new Box();        // 声明 Box2，类型为 Box
            double volume = 0.0;         // 体积

            // Box1 详述
            Box1.height = 5.0;
            Box1.length = 6.0;
            Box1.breadth = 7.0;

            // Box2 详述
            Box2.height = 10.0;
            Box2.length = 12.0;
            Box2.breadth = 13.0;
           
            // Box1 的体积
            volume = Box1.height * Box1.length * Box1.breadth;
            Console.WriteLine("Box1 的体积： {0}",  volume);

            // Box2 的体积
            volume = Box2.height * Box2.length * Box2.breadth;
            Console.WriteLine("Box2 的体积： {0}", volume);
            Console.ReadKey();
        }
    }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
Box1 的体积： 210
Box2 的体积： 1560
```
成员函数和封装<br/>
类的成员函数是一个在类定义中有它的定义或原型的函数，就像其他变量一样。作为类的一个成员，它能在类的任何对象上操作，且能访问该对象的类的所有成员。<br/>
成员变量是对象的属性（从设计角度），且它们保持私有来实现封装。这些变量只能使用公共成员函数来访问。<br/>
让我们使用上面的概念来设置和获取一个类中不同的类成员的值：
```c#
using System;
namespace BoxApplication
{
    class Box
    {
       private double length;   // 长度
       private double breadth;  // 宽度
       private double height;   // 高度
       public void setLength( double len )
       {
            length = len;
       }

       public void setBreadth( double bre )
       {
            breadth = bre;
       }

       public void setHeight( double hei )
       {
            height = hei;
       }
       public double getVolume()
       {
           return length * breadth * height;
       }
    }
    class Boxtester
    {
        static void Main(string[] args)
        {
            Box Box1 = new Box();        // 声明 Box1，类型为 Box
            Box Box2 = new Box();                // 声明 Box2，类型为 Box
            double volume;                               // 体积


            // Box1 详述
            Box1.setLength(6.0);
            Box1.setBreadth(7.0);
            Box1.setHeight(5.0);

            // Box2 详述
            Box2.setLength(12.0);
            Box2.setBreadth(13.0);
            Box2.setHeight(10.0);
       
            // Box1 的体积
            volume = Box1.getVolume();
            Console.WriteLine("Box1 的体积： {0}" ,volume);

            // Box2 的体积
            volume = Box2.getVolume();
            Console.WriteLine("Box2 的体积： {0}", volume);
           
            Console.ReadKey();
        }
    }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
Box1 的体积： 210
Box2 的体积： 1560
```
C# 中的构造函数<br/>
类的 构造函数 是类的一个特殊的成员函数，当创建类的新对象时执行。<br/>
构造函数的名称与类的名称完全相同，它没有任何返回类型。<br/>
下面的实例说明了构造函数的概念：
```c#
using System;
namespace LineApplication
{
   class Line
   {
      private double length;   // 线条的长度
      public Line()
      {
         Console.WriteLine("对象已创建");
      }

      public void setLength( double len )
      {
         length = len;
      }
      public double getLength()
      {
         return length;
      }

      static void Main(string[] args)
      {
         Line line = new Line();    
         // 设置线条长度
         line.setLength(6.0);
         Console.WriteLine("线条的长度： {0}", line.getLength());
         Console.ReadKey();
      }
   }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
对象已创建
线条的长度： 6
```
默认的构造函数没有任何参数。但是如果你需要一个带有参数的构造函数可以有参数，这种构造函数叫做参数化构造函数。这种技术可以帮助你在创建对象的同时给对象赋初始值，具体请看下面实例：
```c#
using System;
namespace LineApplication
{
   class Line
   {
      private double length;   // 线条的长度
      public Line(double len)  // 参数化构造函数
      {
         Console.WriteLine("对象已创建，length = {0}", len);
         length = len;
      }

      public void setLength( double len )
      {
         length = len;
      }
      public double getLength()
      {
         return length;
      }

      static void Main(string[] args)
      {
         Line line = new Line(10.0);
         Console.WriteLine("线条的长度： {0}", line.getLength());
         // 设置线条长度
         line.setLength(6.0);
         Console.WriteLine("线条的长度： {0}", line.getLength());
         Console.ReadKey();
      }
   }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
对象已创建，length = 10
线条的长度： 10
线条的长度： 6
```
C# 中的析构函数<br/>
类的 析构函数 是类的一个特殊的成员函数，当类的对象超出范围时执行。<br/>
析构函数的名称是在类的名称前加上一个波浪形（~）作为前缀，它不返回值，也不带任何参数。<br/>
析构函数用于在结束程序（比如关闭文件、释放内存等）之前释放资源。析构函数不能继承或重载。<br/>
下面的实例说明了析构函数的概念：
```c#
using System;
namespace LineApplication
{
   class Line
   {
      private double length;   // 线条的长度
      public Line()  // 构造函数
      {
         Console.WriteLine("对象已创建");
      }
      ~Line() //析构函数
      {
         Console.WriteLine("对象已删除");
      }

      public void setLength( double len )
      {
         length = len;
      }
      public double getLength()
      {
         return length;
      }

      static void Main(string[] args)
      {
         Line line = new Line();
         // 设置线条长度
         line.setLength(6.0);
         Console.WriteLine("线条的长度： {0}", line.getLength());          
      }
   }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
对象已创建
线条的长度： 6
对象已删除
```
C# 类的静态成员<br/>
我们可以使用 static 关键字把类成员定义为静态的。当我们声明一个类成员为静态时，意味着无论有多少个类的对象被创建，只会有一个该静态成员的副本。<br/>
关键字 static 意味着类中只有一个该成员的实例。静态变量用于定义常量，因为它们的值可以通过直接调用类而不需要创建类的实例来获取。静态变量可在成员函数或类的定义外部进行初始化。你也可以在类的定义内部初始化静态变量。<br/>
下面的实例演示了静态变量的用法：
using System;
namespace StaticVarApplication
{
    class StaticVar
    {
       public static int num;
        public void count()
        {
            num++;
        }
        public int getNum()
        {
            return num;
        }
    }
    class StaticTester
    {
        static void Main(string[] args)
        {
            StaticVar s1 = new StaticVar();
            StaticVar s2 = new StaticVar();
            s1.count();
            s1.count();
            s1.count();
            s2.count();
            s2.count();
            s2.count();        
            Console.WriteLine("s1 的变量 num： {0}", s1.getNum());
            Console.WriteLine("s2 的变量 num： {0}", s2.getNum());
            Console.ReadKey();
        }
    }
}
当上面的代码被编译和执行时，它会产生下列结果：
```c#
s1 的变量 num： 6
s2 的变量 num： 6
```
你也可以把一个成员函数声明为 static。这样的函数只能访问静态变量。静态函数在对象被创建之前就已经存在。下面的实例演示了静态函数的用法：
```c#
using System;
namespace StaticVarApplication
{
    class StaticVar
    {
       public static int num;
        public void count()
        {
            num++;
        }
        public static int getNum()
        {
            return num;
        }
    }
    class StaticTester
    {
        static void Main(string[] args)
        {
            StaticVar s = new StaticVar();
            s.count();
            s.count();
            s.count();                  
            Console.WriteLine("变量 num： {0}", StaticVar.getNum());
            Console.ReadKey();
        }
    }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
变量 num： 3
```

C# 继承
- 
继承是面向对象程序设计中最重要的概念之一。继承允许我们根据一个类来定义另一个类，这使得创建和维护应用程序变得更容易。同时也有利于重用代码和节省开发时间。<br/>
当创建一个类时，程序员不需要完全重新编写新的数据成员和成员函数，只需要设计一个新的类，继承了已有的类的成员即可。这个已有的类被称为的基类，这个新的类被称为派生类。<br/>
继承的思想实现了 属于（IS-A） 关系。例如，哺乳动物 属于（IS-A） 动物，狗 属于（IS-A） 哺乳动物，因此狗 属于（IS-A） 动物。<br/>
基类和派生类<br/>
一个类可以派生自多个类或接口，这意味着它可以从多个基类或接口继承数据和函数。<br/>
C# 中创建派生类的语法如下：
```c#
<访问修饰符符> class <基类>
{
 ...
}
class <派生类> : <基类>
{
 ...
}
```
假设，有一个基类 Shape，它的派生类是 Rectangle：
```c#
using System;
namespace InheritanceApplication
{
   class Shape
   {
      public void setWidth(int w)
      {
         width = w;
      }
      public void setHeight(int h)
      {
         height = h;
      }
      protected int width;
      protected int height;
   }

   // 派生类
   class Rectangle: Shape
   {
      public int getArea()
      {
         return (width * height);
      }
   }
   
   class RectangleTester
   {
      static void Main(string[] args)
      {
         Rectangle Rect = new Rectangle();

         Rect.setWidth(5);
         Rect.setHeight(7);

         // 打印对象的面积
         Console.WriteLine("总面积： {0}",  Rect.getArea());
         Console.ReadKey();
      }
   }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
总面积： 35
```
基类的初始化<br/>
派生类继承了基类的成员变量和成员方法。因此父类对象应在子类对象创建之前被创建。您可以在成员初始化列表中进行父类的初始化。<br/>
下面的程序演示了这点：
```c#
using System;
namespace RectangleApplication
{
   class Rectangle
   {
      // 成员变量
      protected double length;
      protected double width;
      public Rectangle(double l, double w)
      {
         length = l;
         width = w;
      }
      public double GetArea()
      {
         return length * width;
      }
      public void Display()
      {
         Console.WriteLine("长度： {0}", length);
         Console.WriteLine("宽度： {0}", width);
         Console.WriteLine("面积： {0}", GetArea());
      }
   }//end class Rectangle  
   class Tabletop : Rectangle
   {
      private double cost;
      public Tabletop(double l, double w) : base(l, w)
      { }
      public double GetCost()
      {
         double cost;
         cost = GetArea() * 70;
         return cost;
      }
      public void Display()
      {
         base.Display();
         Console.WriteLine("成本： {0}", GetCost());
      }
   }
   class ExecuteRectangle
   {
      static void Main(string[] args)
      {
         Tabletop t = new Tabletop(4.5, 7.5);
         t.Display();
         Console.ReadLine();
      }
   }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
长度： 4.5
宽度： 7.5
面积： 33.75
成本： 2362.5
```
C# 多重继承<br/>
多重继承指的是一个类别可以同时从多于一个父类继承行为与特征的功能。与单一继承相对，单一继承指一个类别只可以继承自一个父类。<br/>
C# 不支持多重继承。但是，您可以使用接口来实现多重继承。下面的程序演示了这点：
```c#
using System;
namespace InheritanceApplication
{
   class Shape
   {
      public void setWidth(int w)
      {
         width = w;
      }
      public void setHeight(int h)
      {
         height = h;
      }
      protected int width;
      protected int height;
   }

   // 基类 PaintCost
   public interface PaintCost
   {
      int getCost(int area);

   }
   // 派生类
   class Rectangle : Shape, PaintCost
   {
      public int getArea()
      {
         return (width * height);
      }
      public int getCost(int area)
      {
         return area * 70;
      }
   }
   class RectangleTester
   {
      static void Main(string[] args)
      {
         Rectangle Rect = new Rectangle();
         int area;
         Rect.setWidth(5);
         Rect.setHeight(7);
         area = Rect.getArea();
         // 打印对象的面积
         Console.WriteLine("总面积： {0}",  Rect.getArea());
         Console.WriteLine("油漆总成本： ${0}" , Rect.getCost(area));
         Console.ReadKey();
      }
   }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
总面积： 35
油漆总成本： $2450
```

C# 多态性
- 
多态是同一个行为具有多个不同表现形式或形态的能力。<br/>
多态性意味着有多重形式。在面向对象编程范式中，多态性往往表现为"一个接口，多个功能"。<br/>
多态性可以是静态的或动态的。在静态多态性中，函数的响应是在编译时发生的。在动态多态性中，函数的响应是在运行时发生的。<br/>
在 C# 中，每个类型都是多态的，因为包括用户定义类型在内的所有类型都继承自 Object。<br/>
静态多态性<br/>
在编译时，函数和对象的连接机制被称为早期绑定，也被称为静态绑定。C# 提供了两种技术来实现静态多态性。分别为：
- 函数重载
- 运算符重载
函数重载<br/>
您可以在同一个范围内对相同的函数名有多个定义。函数的定义必须彼此不同，可以是参数列表中的参数类型不同，也可以是参数个数不同。不能重载只有返回类型不同的函数声明。<br/>
下面的实例演示了几个相同的函数 Add()，用于对不同个数参数进行相加处理：
```c#
using System;
namespace PolymorphismApplication
{
    public class TestData  
    {  
        public int Add(int a, int b, int c)  
        {  
            return a + b + c;  
        }  
        public int Add(int a, int b)  
        {  
            return a + b;  
        }  
    }  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            TestData dataClass = new TestData();
            int add1 = dataClass.Add(1, 2);  
            int add2 = dataClass.Add(1, 2, 3);

            Console.WriteLine("add1 :" + add1);
            Console.WriteLine("add2 :" + add2);  
        }  
    }  
}
```
下面的实例演示了几个相同的函数 print()，用于打印不同的数据类型：
using System;
namespace PolymorphismApplication
{
   class Printdata
   {
      void print(int i)
      {
         Console.WriteLine("输出整型: {0}", i );
      }

      void print(double f)
      {
         Console.WriteLine("输出浮点型: {0}" , f);
      }

      void print(string s)
      {
         Console.WriteLine("输出字符串: {0}", s);
      }
      static void Main(string[] args)
      {
         Printdata p = new Printdata();
         // 调用 print 来打印整数
         p.print(1);
         // 调用 print 来打印浮点数
         p.print(1.23);
         // 调用 print 来打印字符串
         p.print("Hello Runoob");
         Console.ReadKey();
      }
   }
}
当上面的代码被编译和执行时，它会产生下列结果：
```c#
输出整型: 1
输出浮点型: 1.23
输出字符串: Hello Runoob
```
动态多态性<br/>
C# 允许您使用关键字 abstract 创建抽象类，用于提供接口的部分类的实现。当一个派生类继承自该抽象类时，实现即完成。抽象类包含抽象方法，抽象方法可被派生类实现。派生类具有更专业的功能。<br/>
请注意，下面是有关抽象类的一些规则：
- 您不能创建一个抽象类的实例。
- 您不能在一个抽象类外部声明一个抽象方法。
- 通过在类定义前面放置关键字 sealed，可以将类声明为密封类。当一个类被声明为 sealed 时，它不能被继承。抽象类不能被声明为 sealed。
下面的程序演示了一个抽象类：
```c#
using System;
namespace PolymorphismApplication
{
   abstract class Shape
   {
       abstract public int area();
   }
   class Rectangle:  Shape
   {
      private int length;
      private int width;
      public Rectangle( int a=0, int b=0)
      {
         length = a;
         width = b;
      }
      public override int area ()
      {
         Console.WriteLine("Rectangle 类的面积：");
         return (width * length);
      }
   }

   class RectangleTester
   {
      static void Main(string[] args)
      {
         Rectangle r = new Rectangle(10, 7);
         double a = r.area();
         Console.WriteLine("面积： {0}",a);
         Console.ReadKey();
      }
   }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
Rectangle 类的面积：
面积： 70
```
当有一个定义在类中的函数需要在继承类中实现时，可以使用虚方法。<br/>
虚方法是使用关键字 virtual 声明的。<br/>
虚方法可以在不同的继承类中有不同的实现。<br/>
对虚方法的调用是在运行时发生的。<br/>
动态多态性是通过 抽象类 和 虚方法 实现的。<br/>
以下实例创建了 Shape 基类，并创建派生类 Circle、 Rectangle、Triangle， Shape 类提供一个名为 Draw 的虚拟方法，在每个派生类中重写该方法以绘制该类的指定形状。<br/>
```c#
using System;
using System.Collections.Generic;

public class Shape
{
    public int X { get; private set; }
    public int Y { get; private set; }
    public int Height { get; set; }
    public int Width { get; set; }
   
    // 虚方法
    public virtual void Draw()
    {
        Console.WriteLine("执行基类的画图任务");
    }
}

class Circle : Shape
{
    public override void Draw()
    {
        Console.WriteLine("画一个圆形");
        base.Draw();
    }
}
class Rectangle : Shape
{
    public override void Draw()
    {
        Console.WriteLine("画一个长方形");
        base.Draw();
    }
}
class Triangle : Shape
{
    public override void Draw()
    {
        Console.WriteLine("画一个三角形");
        base.Draw();
    }
}

class Program
{
    static void Main(string[] args)
    {
        // 创建一个 List<Shape> 对象，并向该对象添加 Circle、Triangle 和 Rectangle
        var shapes = new List<Shape>
        {
            new Rectangle(),
            new Triangle(),
            new Circle()
        };

        // 使用 foreach 循环对该列表的派生类进行循环访问，并对其中的每个 Shape 对象调用 Draw 方法
        foreach (var shape in shapes)
        {
            shape.Draw();
        }

        Console.WriteLine("按下任意键退出。");
        Console.ReadKey();
    }

}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
画一个长方形
执行基类的画图任务
画一个三角形
执行基类的画图任务
画一个圆形
执行基类的画图任务
按下任意键退出。
```
下面的程序演示通过虚方法 area() 来计算不同形状图像的面积：
```c#
using System;
namespace PolymorphismApplication
{
   class Shape
   {
      protected int width, height;
      public Shape( int a=0, int b=0)
      {
         width = a;
         height = b;
      }
      public virtual int area()
      {
         Console.WriteLine("父类的面积：");
         return 0;
      }
   }
   class Rectangle: Shape
   {
      public Rectangle( int a=0, int b=0): base(a, b)
      {

      }
      public override int area ()
      {
         Console.WriteLine("Rectangle 类的面积：");
         return (width * height);
      }
   }
   class Triangle: Shape
   {
      public Triangle(int a = 0, int b = 0): base(a, b)
      {
     
      }
      public override int area()
      {
         Console.WriteLine("Triangle 类的面积：");
         return (width * height / 2);
      }
   }
   class Caller
   {
      public void CallArea(Shape sh)
      {
         int a;
         a = sh.area();
         Console.WriteLine("面积： {0}", a);
      }
   }  
   class Tester
   {
     
      static void Main(string[] args)
      {
         Caller c = new Caller();
         Rectangle r = new Rectangle(10, 7);
         Triangle t = new Triangle(10, 5);
         c.CallArea(r);
         c.CallArea(t);
         Console.ReadKey();
      }
   }
}
```
当上面的代码被编译和执行时，它会产生下列结果：
```c#
Rectangle 类的面积：
面积：70
Triangle 类的面积：
面积：25
```