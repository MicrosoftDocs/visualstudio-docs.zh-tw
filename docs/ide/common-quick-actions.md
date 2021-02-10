---
title: 一般的快速動作
description: '最熱門 c # 和 Visual Basic 的快速動作，包括修正拼錯的關鍵字或符號、解決合併衝突、移除必要的匯入、產生類型、引入區域變數等。'
ms.date: 03/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d24b03bc79c32c32c570d26b7607d1ba36c1c1df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970903"
---
# <a name="common-quick-actions"></a>一般的快速動作

本主題中的此章節列出一些同時適用於 C# 和 Visual Basic 程式碼的一般 **快速動作**。 這些動作是 Visual Studio 中適用於編譯器診斷或內建之 [.NET 編譯器平台分析器](../code-quality/roslyn-analyzers-overview.md)的「程式碼修正」。

## <a name="actions-that-fix-errors"></a>修正錯誤的動作

本節中的快速動作可修正程式碼中會導致建置失敗的錯誤。 當快速動作可修正程式碼行上的錯誤時，會在紅色波浪線的邊界或底下顯示具有紅色 'x' 標記的燈泡。

![快速動作錯誤圖示與功能表](media/error-light-bulb-with-code.png)

### <a name="correct-misspelled-symbol-or-keyword"></a>修正拼字錯誤的符號或關鍵字

如果您不小心拼錯 Visual Studio 中的類型或關鍵字，這個快速動作會自動加以修正。 您會在燈泡功能表中看到這些專案，並將其顯示為「 **變更 \<misspelled word> \<correct word>**」。 例如：

```csharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```vb
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

| 錯誤識別碼 | 適用語言 |
| - | - |
| CS0103、BC30002 | C# 和 Visual Basic |

### <a name="resolve-git-merge-conflict"></a>解決 git merge 衝突

這些快速動作可讓您透過「採取變更」解決 git merge 衝突，這樣會移除衝突的程式碼和標記。

```csharp
// Before
private void MyMethod()
{
    if (false)
    {

    }
}

// Take changes from 'HEAD'

// After
private void MyMethod()
{
    if (true)
    {

    }
}
```

| 錯誤識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| CS8300、BC37284 | C# 和 Visual Basic | Visual Studio 2017 15.3 版和更新版本 |

## <a name="actions-that-remove-unnecessary-code"></a>移除不必要程式碼的動作

### <a name="remove-unnecessary-usingsimports"></a>移除不必要的 using/Import

[ **移除不必要的 using/Imports** ] 快速動作會移除目前檔案的任何未使用和指示詞 `using` `Import` 。 當您選取此項目時，將會移除未使用的命名空間匯入。

| 適用語言 | 支援的版本 |
| - | - |
| C# 和 Visual Basic | Visual Studio 2015 和更新版本 |

### <a name="remove-unnecessary-cast"></a>移除不必要的 Cast

若將型別轉型成不需轉換的另一種型別，**移除不必要的轉換** 快速動作項目將會移除不必要的轉換。

```csharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```vb
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

| 診斷識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| IDE0004 | C# 和 Visual Basic | Visual Studio 2015 和更新版本 |

### <a name="remove-unused-variables"></a>移除未使用的變數

這個快速動作可讓您移除已宣告但從未在程式碼中使用的變數。

```csharp
// Before
public MyMethod()
{
    var unused = 8;
    var used = 1;
    return DoStuff(used);
}

// Remove unused variables

// After
public MyMethod()
{
    var used = 1;
    return DoStuff(used);
}
```

| 診斷識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| CS0219、BC42024 | C# 和 Visual Basic | Visual Studio 2017 15.3 版和更新版本 |

### <a name="remove-type-from-default-value-expression"></a>從預設值運算式中移除類型

這個快速動作會從 default 值運算式中移除實值型別，並在編譯器可推斷運算式的類型時使用[ default 常值](/dotnet/csharp/language-reference/operators/default#default-literal)。

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }
```

| 診斷識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| IDE0034 | C# 7.1+ | Visual Studio 2017 15.3 版和更新版本 |

## <a name="actions-that-add-missing-code"></a>新增遺漏程式碼的動作

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>針對參考組件的類型、NuGet 套件的類型或您方案中的其他類型新增 using/import

使用位於您方案中其他專案的類型會自動顯示快速動作，但是其他則需要從 [工具] > [選項] > [C#] 或 [基本] > [進階] 索引標籤啟用︰

- 針對參考組件中的類型建議 using/Import
- 針對 NuGet 套件中的類型建議 using/Import

啟用時，如果您在目前未匯入但存在於參考元件或 NuGet 封裝中的命名空間中使用類型，則會建立 using 或 import 指示詞。

```csharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```vb
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

' After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

| 診斷識別碼 | 適用語言 |
| - | - |
| CS0103、BC30451 | C# 和 Visual Basic|

### <a name="add-missing-casesdefault-caseboth"></a>新增遺漏的 Case/預設的 Case/兩者

以 C# 建立 `switch` 陳述式或以 Visual Basic 建立 `Select Case` 陳述式時，您可以使用程式碼動作，自動新增遺漏的 Case 項目、預設的 Case 陳述式，或兩者。

以下列列舉和空白 `switch` 或 `Select Case` 陳述式為例：

```csharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```vb
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

使用 **新增兩者** 快速動作可填入遺漏的 case，並加入 default (預設) case：

```csharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```

```vb
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

| 診斷識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| IDE0010 | C# 和 Visual Basic| Visual Studio 2017 15.3 版和更新版本 |

### <a name="add-null-checks-for-parameters"></a>新增參數的 Null 檢查

這個快速動作可讓您在程式碼中新增檢查，以判斷參數是否為 Null。

```csharp
// Before
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty) // cursor inside myProperty
    {
        MyProperty = myProperty;
    }
}

// Add null check

// After
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty)
    {
        MyProperty = myProperty ?? throw new ArgumentNullException(nameof(myProperty));
    }
}
```

| 適用語言 | 支援的版本 |
| -------------------- | ---------------- |
| C# 和 Visual Basic| Visual Studio 2017 15.3 版和更新版本 |

### <a name="add-argument-name"></a>新增引數名稱

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

| 適用語言 | 支援的版本 |
| -------------------- | ---------------- |
| C# 和 Visual Basic| Visual Studio 2017 15.3 版和更新版本 |

### <a name="add-braces"></a>新增大括弧

「新增大括弧」快速動作會為單行 `if` 陳述式加上大括弧並自動換行。

```csharp
// Before
if (true)
    return "hello,world";

// Add braces

// After
if (true)
{
    return "hello,world";
}
```

| 診斷識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| IDE0011 | C# | Visual Studio 2017 和更新版本 |

### <a name="add-and-order-modifiers"></a>新增及排序修飾詞

這些快速動作可讓您排序現有的並新增遺漏的存取範圍修飾詞，來協助您組織化修飾詞。

```csharp
// Before
enum Color
{
    Red, White, Blue
}

// Add accessibility modifiers

// After
internal enum Color
{
    Red, White, Blue
}
```

```csharp
// Before
static private int thisFieldIsPublic;

// Order modifiers

// After
private static int thisFieldIsPublic;
```

| 診斷識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| IDE0036 | C# 和 Visual Basic| Visual Studio 2017 15.5 版和更新版本 |
| IDE0040 | C# 和 Visual Basic| Visual Studio 2017 15.5 版和更新版本 |

## <a name="code-transformations"></a>程式碼轉換

### <a name="convert-if-construct-to-switch"></a>將 'if' 建構轉換為 'switch'

這個快速動作可讓您將 **if-then-else** 建構轉換為 **switch** 建構。

```csharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```vb
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

| 適用語言 | 支援的版本 |
| -------------------- | ---------------- |
| C# 和 Visual Basic| Visual Studio 2017 15.3 版和更新版本 |

### <a name="convert-to-interpolated-string"></a>轉換成字串插值

[字串插值](/dotnet/csharp/language-reference/keywords/interpolated-strings)可以輕鬆表示含有內嵌變數的字串，類似於 **[String.Format](/dotnet/api/system.string.format#overloads)** 方法。  這個快速動作會辨識字串串連或使用 **String.Format** 的情況，並將使用方式變更為字串插值。

```csharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```vb
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

| 適用語言 | 支援的版本 |
| -------------------- | ---------------- |
| C# 6.0+ 和 Visual Basic 14+ | Visual Studio 2017 和更新版本 |

### <a name="use-object-initializers"></a>使用物件初始設定式

這個快速動作可讓您使用[物件初始設定式](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)，而非叫用建構函式及新增額外的指派陳述式。

```csharp
// Before
var c = new Customer();
c.Age = 21;

// Object initialization can be simplified

// After
var c = new Customer() { Age = 21 };
```

```vb
' Before
Dim c = New Customer()
c.Age = 21

' Object initialization can be simplified

' After
Dim c = New Customer() With {.Age = 21}
```

| 診斷識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| IDE0017 | C# 和 Visual Basic | Visual Studio 2017 和更新版本 |

### <a name="use-collection-initializers"></a>使用集合初始設定式

這個快速動作可讓您使用[集合初始設定式](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)，而非多次呼叫您類別的 `Add` 方法。

```csharp
// Before
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);

// Collection initialization can be simplified

// After
var list = new List<int> { 1, 2, 3 };
```

```vb
' Before
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)

' Collection initialization can be simplified

' After
Dim list = New List(Of Integer) From {1, 2, 3}
```

| 診斷識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| IDE0028 | C# 和 Visual Basic | Visual Studio 2017 和更新版本 |

### <a name="convert-auto-property-to-full-property"></a>將自動屬性轉換為完整屬性

這個快速動作可讓您將自動屬性轉換為完整屬性，反之亦然。

```csharp
// Before
private int MyProperty { get; set; }

// Convert to full property

// After
private int MyProperty
{
    get { return _myProperty; }
    set { _myProperty = value; }
}
```

```vb
' Before
Public Property Name As String

' Convert to full property

' After
Private _Name As String

Public Property Name As String
    Get
        Return _Name
    End Get
    Set
        _Name = Value
    End Set
End Property
```

| 適用語言 | 支援的版本 |
| -------------------- | ---------------- |
| C# 和 Visual Basic | Visual Studio 2017 15.5 版和更新版本 |

### <a name="convert-block-body-to-expression-bodied-member"></a>將區塊主體轉換成運算式主體成員

這個快速動作允許您為方法、建構函式、運算子、屬性、索引子及存取子將區塊主體轉換為運算式主體成員。

```csharp
//Before
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get { return _myProperty; }
        set
        {
            _myProperty = value;
        }
    }

    public MyClass4(int myProperty)
    {
        MyProperty = myProperty;
    }

    public void PrintProperty()
    {
        Console.WriteLine(MyProperty);
    }
}

// Use expression body for accessors/constructors/methods

// After
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get => _myProperty;
        set => _myProperty = value;
    }

    public MyClass4(int myProperty) => MyProperty = myProperty;

    public void PrintProperty() => Console.WriteLine(MyProperty);
}
```

| 診斷識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| IDE0021-27 | C# 6.0+ | Visual Studio 2017 和更新版本 |

### <a name="convert-anonymous-function-to-local-function"></a>將匿名函式轉換成區域函式

這個快速動作會將匿名函式轉換成區域函式。

```csharp
// Before
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};

// Use local function

// After
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}
```

### <a name="convert-referenceequals-to-is-null"></a>將 'ReferenceEquals' 轉換成 'is null'

| 診斷識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| IDE0041 | C# 7.0+ | Visual Studio 2017 15.5 版和更新版本 |

這個快速動作會建議在可能的情況下使用[模式比對](/dotnet/csharp/pattern-matching)，而非 ```ReferenceEquals``` 程式碼模式。

```csharp
// Before
var value = "someString";
if (object.ReferenceEquals(value, null))
{
    return;
}

// Use 'is null' check

// After
var value = "someString";
if (value is null)
{
    return;
}
```

| 診斷識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| IDE0039 | C# 7.0+ | Visual Studio 2017 第15版。 及更新版本 |

### <a name="introduce-pattern-matching"></a>引進模式比對

這個快速動作會建議使用[模式比對](/dotnet/csharp/pattern-matching)並搭配 C# 中的轉換及 Null 檢查。

```csharp
// Before
if (o is int)
{
    var i = (int)o;
    ...
}

// Use pattern matching

// After
if (o is int i)
{
    ...
}
```

```csharp
// Before
var s = o as string;
if (s != null)
{
    ...
}

// Use pattern matching

// After
if (o is string s)
{
    ...
}
```

| 診斷識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| IDE0020 | C# 7.0+ | Visual Studio 2017 和更新版本 |
| IDE0019 | C# 7.0+ | Visual Studio 2017 和更新版本 |

### <a name="change-base-for-numeric-literals"></a>變更數值常值的基底

這個快速動作可讓您將數值常值從一個基底數值系統轉換至另一個基底數值系統。 例如，您可以將數字變更為十六進位或二進位格式。

```csharp
// Before
int countdown = 2097152;

// Convert to hex

// After
int countdown = 0x200000;
```

```vb
' Before
Dim countdown As Integer = 2097152

' Convert to hex

' After
Dim countdown As Integer = &H200000
```

| 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| C# 7.0+ 及 Visual Basic 14+ | Visual Studio 2017 15.3 版和更新版本 |

### <a name="insert-digit-separators-into-literals"></a>將數字分隔符號插入到常值中

這個快速動作可讓您將分隔符號字元加入到常值中。

```csharp
// Before
int countdown = 1000000;

// Separate thousands

// After
int countdown = 1_000_000;
```

```vb
' Before
Dim countdown As Integer = 1000000

' Separate thousands

' After
Dim countdown As Integer = 1_000_000
```

| 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| C# 7.0+ 及 Visual Basic 14+ | Visual Studio 2017 15.3 版和更新版本 |

### <a name="use-explicit-tuple-names"></a>使用明確的元組名稱

這個快速動作會識別可使用明確元組名稱，而非 Item1、Item2 等的區域。

```csharp
// Before
(string name, int age) customer = GetCustomer();
var name = customer.Item1;

// Use explicit tuple name

// After
(string name, int age) customer = GetCustomer();
var name = customer.name;
```

```vb
' Before
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1

' Use explicit tuple name

' After
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name
```

| 診斷識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| IDE0033 | C# 7.0+ 和 Visual Basic 15+ | Visual Studio 2017 和更新版本 |

### <a name="use-inferred-names"></a>使用推斷名稱

此快速動作會指出程式碼何時可以簡化成只在匿名類型中使用推斷的成員名稱，或在元組中使用推斷的的項目名稱。

```csharp
// Before
var anon = new { age = age, name = name };

// Use inferred member name

// After
var anon = new { age, name };
```

```csharp
// Before
var tuple = (age: age, name: name);

// Use inferred tuple element name

// After
var tuple = (age, name);
```

| 診斷識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| IDE0037 | C# | Visual Studio 2017 15.5 版和更新版本 |
| IDE0037 | C# 7.1+ | Visual Studio 2017 15.5 版和更新版本 |

### <a name="deconstruct-tuple-declaration"></a>解構元組宣告

此快速動作可解構元組變數宣告。

```csharp
// Before
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");

//Deconstruct variable declaration

// After
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");
```

| 診斷識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| IDE0042 | C# 7.0+ | Visual Studio 2017 15.5 版和更新版本 |

### <a name="make-method-synchronous"></a>將方法設為同步

當在方法中使用 `async` 或 `Async` 關鍵字時，也同時會在該方法中使用 `await` 或 `Await` 關鍵字。 但情況若非如此，將會顯示快速動作，讓您可以藉由移除 `async` 或 `Async` 關鍵字及變更傳回型別的方式，將方法設為同步。 使用 [快速動作] 功能表的 [將方法設為同步] 選項。

```csharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```vb
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

| 錯誤識別碼 | 適用語言 |
| ------- | -------------------- |
| CS1998、BC42356 | C# 和 Visual Basic |

### <a name="make-method-asynchronous"></a>將方法設為非同步

在方法內使用 `await` 或 `Await` 關鍵字時，系統會為方法加上 `async` 或 `Async` 關鍵字標記。 但情況若非如此，系統會顯示快速動作，讓您可以將方法設為非同步。 使用 [快速動作] 功能表的 [將方法/函式設為非同步] 選項。

```csharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method asynchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```vb
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method asynchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

| 錯誤識別碼 | 適用語言 | 支援的版本 |
| ------- | -------------------- | ---------------- |
| CS4032、BC37057 | C# 和 Visual Basic | Visual Studio 2017 和更新版本 |

## <a name="see-also"></a>另請參閱

- [快速動作](../ide/quick-actions.md)
