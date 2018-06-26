---
title: Visual Studio 中 EditorConfig 的 .NET 編碼慣例設定
ms.date: 02/28/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language conventions [EditorConfig]
- formatting conventions [EditorConfig]
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: caedbf46ce3d56d57a22541f1ddc042d8e41eb48
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572643"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>EditorConfig 的 .NET 編碼慣例設定

在 Visual Studio 2017 中，您可以使用 [EditorConfig](../ide/create-portable-custom-editor-options.md) 檔案定義程式碼基底的程式碼樣式並維持一致。 EditorConfig 包含數個核心格式設定屬性，例如 `indent_style` 和 `indent_size`。 在 Visual Studio 中，也可以使用 EditorConfig 檔案設定 .NET 編碼慣例設定。 EditorConfig 檔案可讓您啟用或停用個別的 .NET 編碼慣例，並設定要強制執行慣例的程度 (透過嚴重性層級)。 若要深入了解使用 EditorConfig 在程式碼基底上強制一致性的方式，請參閱[使用 EditorConfig 建立可攜式自訂編輯器設定](../ide/create-portable-custom-editor-options.md)。 您也可以查看 [.NET 編譯器平台的 .editorconfig 檔案](https://github.com/dotnet/roslyn/blob/master/.editorconfig)作為範例。

有三個支援的 .NET 程式碼慣例類別：

- [語言慣例](#language-conventions)

   有關 C# 或 Visual Basic 語言的規則。 例如，您可以在定義變數或指定運算式主體成員時，指定使用 `var` 或明確類型的規則。

- [格式設定慣例](#formatting-conventions)

   有關程式碼配置和結構的規則，以使其更容易閱讀。 例如，您可以指定使用 Allman 大括弧或設定控制區塊空格的規則。

- [命名慣例](../ide/editorconfig-naming-conventions.md)

   有關程式碼項目的命名規則。 例如，您可以指定 `async` 方法必須以 "Async" 結尾。

## <a name="language-conventions"></a>語言慣例

語言慣例規則具有下列格式：

`options_name = false|true : none|suggestion|warning|error`

每個語言慣例規則必須指定 [true] (慣用此樣式) 或 [false] (不喜此樣式) 和 [嚴重性]。 嚴重性會指定該樣式的強制層級。

下表列出可能的嚴重性值及其效果：

嚴重性 | 作用
:------- | ------
無或無訊息 | 違反這項規則時，不向使用者顯示任何內容。 但程式碼產生功能會以此樣式產生程式碼。
建議 | 當違反這個樣式規則時，會向使用者顯示建議。 建議會顯示為前兩個字元下的三個灰點。
warning | 違反此樣式規則時，顯示編譯器警告。
個錯誤 | 違反此樣式規則時，顯示編譯器錯誤。

下列清單顯示允許的語言慣例規則：

- .NET 程式碼樣式設定
    - ["This." 和 "Me." 限定詞](#this_and_me)
        - dotnet\_style\_qualification\_for_field
        - dotnet\_style\_qualification\_for_property
        - dotnet\_style\_qualification\_for_method
        - dotnet\_style\_qualification\_for_event
    - [語言關鍵字而非類型參考的架構類型名稱](#language_keywords)
        - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
        - dotnet\_style\_predefined\_type\_for\_member_access
    - [修飾詞喜好設定](#normalize_modifiers)
        - dotnet\_style\_require\_accessibility_modifiers
        - csharp\_preferred\_modifier_order
        - visual\_basic\_preferred\_modifier_order
        - dotnet\_style\_readonly\_field
    - [運算式層級喜好設定](#expression_level)
        - dotnet\_style\_object_initializer
        - dotnet\_style\_collection_initializer
        - dotnet\_style\_explicit\_tuple_names
        - dotnet\_prefer\_inferred\_tuple_names
        - dotnet\_prefer\_inferred\_anonymous\_type\_member_names
    - ["Null" 檢查喜好設定](#null_checking)
        - dotnet\_style\_coalesce_expression
        - dotnet\_style\_null_propagation
- C# 程式碼樣式設定
    - [隱含和明確類型](#implicit-and-explicit-types)
        - csharp\_style\_var\_for\_built\_in_types
        - csharp\_style\_var\_when\_type\_is_apparent
        - csharp\_style\_var_elsewhere
    - [運算式主體成員](#expression_bodied_members)
        - csharp\_style\_expression\_bodied_methods
        - csharp\_style\_expression\_bodied_constructors
        - csharp\_style\_expression\_bodied_operators
        - csharp\_style\_expression\_bodied_properties
        - csharp\_style\_expression\_bodied_indexers
        - csharp\_style\_expression\_bodied_accessors
    - [模式比對](#pattern_matching)
        - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
        - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
    - [內嵌變數宣告](#inlined_variable_declarations)
        - csharp\_style\_inlined\_variable_declaration
    - [運算式層級喜好設定](#expression_level_csharp)
        - csharp\_prefer\_simple\_default_expression
        - csharp\_style\_deconstructed\_variable_declaration
        - csharp\_style\_pattern\_local\_over\_anonymous_function
    - ["Null" 檢查喜好設定](#null_checking_csharp)
        - csharp\_style\_throw_expression
        - csharp\_style\_conditional\_delegate_call
    - [程式碼區塊喜好設定](#code_block)
        - csharp\_prefer_braces

### <a name="net-code-style-settings"></a>.NET 程式碼樣式設定

本節中的樣式規則對 C# 和 Visual Basic 都適用。 若要查看慣用程式設計語言的程式碼範例，請在瀏覽器視窗右上角的 [語言] 下拉式功能表中選擇它。

#### <a name="this_and_me"></a>"This." 和 "Me." 限定詞

這個樣式規則 (規則識別碼 IDE0003 和 IDE0009) 可以套用至欄位、屬性、方法或事件。 **true** 值表示希望程式碼符號在 C# 中以 `this.` 開頭或在 Visual Basic 中以 `Me.` 開頭。 **false** 值表示希望程式碼項目前面_不_要加上 `this.` 或 `Me.`。

下表顯示規則名稱、適用的程式設計語言和預設值：

| 規則名稱 | 適用的語言 | Visual Studio 預設值 |
| ----------- | -------------------- | ----------------------|
| dotnet_style_qualification_for_field | C# 和 Visual Basic | false:none |
| dotnet_style_qualification_for_property | C# 和 Visual Basic | false:none |
| dotnet_style_qualification_for_method | C# 和 Visual Basic | false:none |
| dotnet_style_qualification_for_event | C# 和 Visual Basic | false:none |

**dotnet\_style\_qualification\_for_field**

- 當此規則設定為 **true** 時，希望欄位在 C# 中以 `this.` 開頭或在 Visual Basic 中以 `Me.` 開頭。
- 當此規則設定為 **false** 時，希望欄位_不_以 `this.` 或 `Me.` 開頭。

程式碼範例：

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```

```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```

**dotnet\_style\_qualification\_for_property**

- 當此規則設定為 **true** 時，希望屬性在 C# 中以 `this.` 開頭或在 Visual Basic 中以 `Me.` 開頭。
- 當此規則設定為 **false** 時，希望屬性_不_以 `this.` 或 `Me.` 開頭。

程式碼範例：

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```

```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```

**dotnet\_style\_qualification\_for_method**

- 當此規則設定為 **true** 時，希望方法在 C# 中以 `this.` 開頭或在 Visual Basic 中以 `Me.` 開頭。
- 當此規則設定為 **false** 時，希望方法_不_以 `this.` 或 `Me.` 開頭。

程式碼範例：

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```

```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```

**dotnet\_style\_qualification\_for_event**

- 當此規則設定為 **true** 時，希望事件在 C# 中以 `this.` 開頭或在 Visual Basic 中以 `Me.` 開頭。
- 當此規則設定為 **false** 時，希望事件_不_以 `this.` 或 `Me.` 開頭。

程式碼範例：

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```

```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```

這些規則可能會出現在 .editorconfig 檔案中，如下所示：

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="language_keywords"></a>語言關鍵字而非類型參考的架構類型名稱

此樣式規則可以套用至本機變數、方法參數和類別成員，或作為類型成員存取運算式的不同規則。 值為 **true** 表示偏好語言關鍵字 (例如 `int` 或 `Integer`) 而不是以關鍵字代表類型的類型名稱 (例如 `Int32`)。 值為 **false** 表示偏好類型名稱，而不是語言關鍵字。

下表顯示規則名稱、規則識別碼、適用的程式設計語言和預設值：

| 規則名稱 | 規則識別碼 | 適用的語言 | Visual Studio 預設值 |
| --------- | ------- | -------------------- | ----------------------|
| dotnet_style_predefined_type_for_locals_parameters_members | IDE0012 和 IDE0014 | C# 和 Visual Basic | true:none |
| dotnet_style_predefined_type_for_member_access | IDE0013 和 IDE0015 | C# 和 Visual Basic | true:none |

**dotnet\_style\_predefined\_type\_for\_locals\_parameters_members**

- 當此規則設定為 **true** 時，希望是本機變數、方法參數和類別成員的語言關鍵字，而不是以關鍵字表示類型的類型名稱。
- 當此規則設定為 **false** 時，希望是本機變數、方法參數和類別成員的類型名稱，而不是語言關鍵字。

程式碼範例：

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```

```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
```

**dotnet\_style\_predefined\_type\_for\_member_access**

- 當此規則設定為 **true** 時，希望是成員存取運算式的語言關鍵字，而不是以關鍵字表示類型的類型名稱。
- 當此規則設定為 **false** 時，希望是成員存取運算式的類型名稱，而不是語言關鍵字。

程式碼範例：

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```

```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```

這些規則可能會出現在 .editorconfig 檔案中，如下所示：

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="normalize_modifiers"></a>修飾詞喜好設定

本節中的樣式規則與修飾詞喜好設定有關，包括要求存取範圍修飾詞、指定所需的修飾詞排序次序和要求唯讀修飾詞。

下表顯示規則名稱、規則識別碼、適用的程式設計語言、預設值，以及第一個支援的 Visual Studio 版本：

| 規則名稱 | 規則識別碼 | 適用的語言 | Visual Studio 預設值 | Visual Studio 2017 版本 |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| dotnet_style_require_ accessibility_modifiers | IDE0040 | C# 和 Visual Basic | for_non_interface_members:none | 15.5 |
| csharp_preferred_modifier_order | IDE0036 | C# | public、private、protected、internal、static、extern、new、virtual、abstract、sealed、override、readonly、unsafe、volatile、async:none | 15.5 |
| visual_basic_preferred_modifier_order | IDE0036 | Visual Basic | Partial、Default、Private、Protected、Public、Friend、NotOverridable、Overridable、MustOverride、Overloads、Overrides、MustInherit、NotInheritable、Static、Shared、Shadows、ReadOnly、WriteOnly、Dim、Const、WithEvents、Widening、Narrowing、Custom、Async:none | 15.5 |
| dotnet_style_readonly_field | IDE0044 | C# 和 Visual Basic | true:suggestion | 15.7 |

**dotnet\_style\_require\_accessibility_modifiers**

此規則不接受 **true** 或 **false** 值，但接受下列資料表中的值：

| 值 | 描述 |
| ----- |:----------- |
| always | 偏好指定存取範圍修飾詞 |
| for\_non\_interface_members | 偏好宣告存取範圍修飾詞，但公用介面成員除外。 這是與**一律**相同，且已新增以便未來 C# 新增預設介面方法時校訂之用。 |
| never | 偏好不指定存取範圍修飾詞 |

程式碼範例：

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst = "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst = "constant";
}
```

**csharp_preferred_modifier_order**

- 當此規則設定為修飾詞清單時，偏好指定排序。
- 當此規則從檔案中省略時，偏好不排序修飾詞。

程式碼範例：

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

**visual_basic_preferred_modifier_order**

- 當此規則設定為修飾詞清單時，偏好指定排序。
- 當此規則從檔案中省略時，偏好不排序修飾詞。

程式碼範例：

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

**dotnet_style_readonly_field**

- 當此規則設定為 **true** 時，偏好欄位應該標記 `readonly` (C#) 或 `ReadOnly` (Visual Basic)，如果只是內嵌指派，或在建構函式內指派的話。
- 當此規則設定為 **false** 時，對於欄位是否應標記 `readonly` (C#) 或 `ReadOnly` (Visual Basic)，不指派喜好設定。

程式碼範例：

```csharp
// dotnet_style_readonly_field = true
class MyClass
{
    private readonly int _daysInYear = 365;
}
```

```vb
' dotnet_style_readonly_field = true
Public Class MyClass
    Private ReadOnly daysInYear As Int = 365
End Class
```

這些規則可能會出現在 .editorconfig 檔案中，如下所示：

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion
dotnet_style_readonly_field = true:warning

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="expression_level"></a>運算式層級喜好設定

本節中的樣式規則涉及運算式層級喜好設定，包括使用物件初始設定式、集合初始設定式、明確或推斷的 Tuple 名稱，以及推斷的匿名類型。

下表顯示規則名稱、規則識別碼、適用的程式設計語言、預設值，以及第一個支援的 Visual Studio 版本：

| 規則名稱 | 規則識別碼 | 適用的語言 | Visual Studio 預設值 | Visual Studio 2017 版本 |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_object_initializer | IDE0017 | C# 和 Visual Basic | true:suggestion | 初次發行 |
| dotnet_style_collection_initializer | IDE0028 | C# 和 Visual Basic | true:suggestion | 初次發行 |
| dotnet_style_explicit_tuple_names | IDE0033 | C# 7.0+ 和 Visual Basic 15+ | true:suggestion | 初次發行 |
| dotnet_style_prefer_inferred_tuple_names | IDE0037 | C# 7.1+ 和 Visual Basic 15+ | true:suggestion | 15.6 |
| dotnet_style_prefer_inferred_anonymous_ type_member_names | IDE0037 | C# 和 Visual Basic | true:suggestion | 15.6 |

**dotnet\_style\_object_initializer**

- 當此規則設定為 **true** 時，希望盡可能使用物件初始設定式來初始化物件。
- 當此規則設定為 **false** 時，希望*不要*使用物件初始設定式來初始化物件。

程式碼範例：

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```

```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

**dotnet\_style\_collection_initializer**

- 當此規則設定為 **true** 時，希望盡可能使用集合初始設定式來初始化集合。
- 當此規則設定為 **false** 時，希望*不要*使用集合初始設定式來初始化集合。

程式碼範例：

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```

```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```

**dotnet\_style\_explicit\_tuple_names**

- 當此規則設定為 **true** 時，希望是 Tuple 名稱，不是 ItemX 屬性。
- 當此規則設定為 **false** 時，希望是 ItemX 屬性，不是 Tuple 名稱。

程式碼範例：

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```

```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

**dotnet\_style\_prefer\_inferred\_tuple_names**

- 當此規則設定為 **true** 時，優先使用推斷的元組元素名稱。
- 當此規則設定為 **false** 時，優先使用明確的元組元素名稱。

程式碼範例：

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

**dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names**

- 當此規則設定為 **true** 時，優先使用推斷的匿名型別成員名稱。
- 當此規則設定為 **false** 時，優先使用明確的匿名型別成員名稱。

程式碼範例：

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };

```

這些規則可能會出現在 .editorconfig 檔案中，如下所示：

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
```

#### <a name="null_checking"></a>Null 檢查喜好設定

本節中的樣式規則涉及 null 檢查喜好設定。

下表顯示規則名稱、規則識別碼、適用的程式設計語言、預設值，以及第一個支援的 Visual Studio 版本：

| 規則名稱 | 規則識別碼 | 適用的語言 | Visual Studio 預設值 | Visual Studio 2017 版本 |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_coalesce_expression | IDE0029 | C# 和 Visual Basic | true:suggestion | 初次發行 |
| dotnet_style_null_propagation | IDE0031 | C# 6.0+ 和 Visual Basic 14+ | true:suggestion | 初次發行 |

**dotnet\_style\_coalesce_expression**

- 當此規則設定為 **true** 時，希望是 null 聯合運算式，不是三元運算子檢查。
- 當此規則設定為 **false** 時，希望是三元運算子檢查，不是 null 聯合運算式。

程式碼範例：

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```

```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

**dotnet\_style\_null_propagation**

- 當此規則設定為 **true** 時，希望盡可能使用 null 條件運算子。
- 當此規則設定為 **false** 時，希望盡可能使用三元 null 檢查。

程式碼範例：

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```

```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```

這些規則可能會出現在 .editorconfig 檔案中，如下所示：

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

### <a name="c-code-style-settings"></a>C# 程式碼樣式設定

本節中的樣式規則只適用於 C#。

#### <a name="implicit-and-explicit-types"></a>隱含和明確類型

本節中的樣式規則 (規則識別碼 IDE0007 和 IDE0008) 是關於使用 [var](/dotnet/csharp/language-reference/keywords/var) 關鍵字與變數宣告中的明確類型。 當類型顯然位於其他位置時，這項規則可以分別套用至內建類型。

下表顯示規則名稱、適用的程式設計語言和預設值：

| 規則名稱 | 適用的語言 | Visual Studio 預設值 |
| ----------- | -------------------- | ----------------------|
| csharp_style_var_for_built_in_types | C# | true:none |
| csharp_style_var_when_type_is_apparent | C# | true:none |
| csharp_style_var_elsewhere | C# | true:none |

**csharp\_style\_var\_for\_built\_in_types**

- 當此規則設定為 **true** 時，希望使用 `var` 宣告變數與內建系統類型，例如 `int`。
- 當此規則設定為 **false** 時，希望使用明確類型不要使用 `var` 宣告變數與內建系統類型，例如 `int`。

程式碼範例：

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

**csharp\_style\_var\_when\_type\_is_apparent**

- 當此規則設定為 **true** 時，在宣告運算式右側已提到類型時希望使用 `var`。
- 當此規則設定為 **false** 時，在宣告運算式右側已提到類型時，希望使用明確類型不要使用 `var`。

程式碼範例：

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

**csharp\_style\_var_elsewhere**

- 當此規則設定為 **true** 時，除非為另一個程式碼樣式規則覆寫，否則所有情況都希望是 `var` 不要是明確類型。
- 當此規則設定為 **false** 時，除非為另一個程式碼樣式規則覆寫，否則所有情況都希望是明確類型不要是 `var`。

程式碼範例：

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

Editorconfig 檔案範例︰

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="expression_bodied_members"></a>運算式主體成員

本節中的樣式規則是關於當邏輯由單一運算式組成時，使用[運算式主體成員](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members)。 此規則可套用至方法、建構函式、運算子、屬性、索引子及存取子。

下表顯示規則名稱、規則識別碼、適用的語言版本、預設值，以及第一個支援的 Visual Studio 版本：

| 規則名稱 | 規則識別碼 | 適用的語言 | Visual Studio 預設值 | Visual Studio 2017 版本 |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_style_expression_bodied_methods | IDE0022 | C# 6.0+ | false:none | 15.3 |
| csharp_style_expression_bodied_constructors | IDE0021 | C# 7.0+ | false:none | 15.3 |
| csharp_style_expression_bodied_operators | IDE0023 和 IDE0024 | C# 7.0+ | false:none | 15.3 |
| csharp_style_expression_bodied_properties | IDE0025 | C# 7.0+ | true:none | 15.3 |
| csharp_style_expression_bodied_indexers | IDE0026 | C# 7.0+ | true:none | 15.3 |
| csharp_style_expression_bodied_accessors | IDE0027 | C# 7.0+ | true:none | 15.3 |

**csharp\_style\_expression\_bodied_methods**

此規則接受下表中的值：

| 值 | 描述 |
| ----- |:----------- |
| true | 偏好針對方法使用運算式主體的成員 |
| when_on_single_line | 當所有方法都在同一行時，偏好針對方法使用運算式主體的成員 |
| False | 偏好針對方法使用區塊主體 |

程式碼範例：

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

**csharp\_style\_expression\_bodied_constructors**

此規則接受下表中的值：

| 值 | 描述 |
| ----- |:----------- |
| true | 偏好針對建構函式使用運算式主體的成員 |
| when_on_single_line | 當所有建構函式都在同一行時，偏好針對建構函式使用運算式主體的成員 |
| False | 偏好針對建構函式使用區塊主體 |

程式碼範例：

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

**csharp\_style\_expression\_bodied_operators**

此規則接受下表中的值：

| 值 | 描述 |
| ----- |:----------- |
| true | 偏好針對運算子使用運算式主體的成員 |
| when_on_single_line | 當所有運算子都在同一行時，偏好針對運算子使用運算式主體的成員 |
| False | 偏好針對運算子使用區塊主體 |

程式碼範例：

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

**csharp\_style\_expression\_bodied_properties**

此規則接受下表中的值：

| 值 | 描述 |
| ----- |:----------- |
| true | 偏好針對屬性使用運算式主體的成員 |
| when_on_single_line | 當所有屬性都在同一行時，偏好針對屬性使用運算式主體的成員 |
| False | 偏好針對屬性使用區塊主體 |

程式碼範例：

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

**csharp\_style\_expression\_bodied_indexers**

此規則接受下表中的值：

| 值 | 描述 |
| ----- |:----------- |
| true | 偏好針對索引子使用運算式主體的成員 |
| when_on_single_line | 當所有索引子都在同一行時，偏好針對索引子使用運算式主體的成員 |
| False | 偏好針對索引子使用區塊主體 |

程式碼範例：

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _value[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

**csharp\_style\_expression\_bodied_accessors**

此規則接受下表中的值：

| 值 | 描述 |
| ----- |:----------- |
| true | 偏好針對存取子使用運算式主體的成員 |
| when_on_single_line | 當所有存取子都在同一行時，偏好針對存取子使用運算式主體的成員 |
| False | 偏好針對存取子使用區塊主體 |

程式碼範例：

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

Editorconfig 檔案範例︰

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
```

#### <a name="pattern_matching"></a>模式比對

本節中的樣式規則是關於在 C# 中使用[模式比對](/dotnet/csharp/pattern-matching)。

下表顯示規則名稱、規則識別碼、適用的語言版本和預設值：

| 規則名稱 | 規則識別碼 | 適用的語言 | Visual Studio 預設值 |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_pattern_matching_over_is_with_cast_check | IDE0020 | C# 7.0+ | true:suggestion |
| csharp_style_pattern_matching_over_as_with_null_check | IDE0019 | C# 7.0+ | true:suggestion |

**csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check**

- 當此規則設定為 **true** 時，希望是模式比對，而非具有類型轉換的 `is` 運算式。
- 當此規則設定為 **false** 時，希望是具有類型轉換的 `is` 運算式，而非模式比對。

程式碼範例：

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

**csharp\_style\_pattern\_matching\_over\_as\_with\_null_check**

- 當此規則設定為 **true** 時，希望是模式比對，而非具有 null 檢查的 `as` 運算式，以判斷是否為特定類型。
- 當此規則設定為 **false** 時，希望是具有 null 檢查的 `as` 運算式，而非模式比對，以判斷是否為特定類型。

程式碼範例：

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

Editorconfig 檔案範例︰

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="inlined_variable_declarations"></a>內嵌變數宣告

這個樣式規則考量 `out` 變數是否宣告內嵌。 從 C# 7 開始，您可以[在方法呼叫的引數清單中宣告 out 變數](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument)，而非在其他的變數中宣告。

下表顯示規則名稱、規則識別碼、適用的語言版本和預設值：

| 規則名稱 | 規則識別碼 | 適用的語言 | Visual Studio 預設值 |
| --------- | -------- | -------------------- | ----------------------|
| csharp_style_inlined_variable_declaration | IDE0018 | C# 7.0+ | true:suggestion |

**csharp\_style\_inlined\_variable_declaration**

- 當此規則設定為 **true** 時，希望盡可能在方法呼叫的引數清單中宣告 `out` 變數內嵌。
- 當此規則設定為 **false** 時，希望先宣告 `out` 變數再宣告方法呼叫。

程式碼範例：

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Editorconfig 檔案範例︰

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

#### <a name="expression_level_csharp"></a>運算式層級喜好設定

本節中的樣式規則與運算式層級喜好設定有關，包括使用[預設運算式](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference)、解構的變數，以及使用區域函式而不是匿名函式。

下表顯示規則名稱、規則識別碼、適用的語言版本、預設值，以及第一個支援的 Visual Studio 版本：

| 規則名稱 | 規則識別碼 | 適用的語言 | Visual Studio 預設值 | Visual Studio 2017 版本 |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_prefer_simple_default_expression | IDE0034 | C# 7.1+ | true:suggestion | 15.3 |
| csharp_style_deconstructed_variable_declaration | IDE0042 | C# 7.0+ | true:suggestion | 15.5 |
| csharp_style_pattern_local_over_anonymous_function | IDE0039 | C# 7.0+ | true:suggestion | 15.5 |

**csharp\_prefer\_simple\_default_expression**

此樣式規則關於在編譯器能推斷運算式類型時，使用[預設值運算式的 `default` 常值](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference)。

- 當此規則設定為 **true** 時，希望是 `default` 不要是 `default(T)`。
- 當此規則設定為 **false** 時，希望是 `default(T)` 不要是 `default`。

程式碼範例：

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

**csharp\_style\_deconstructed\_variable_declaration**

- 當此規則設定為 **true** 時，偏好使用解構的變數宣告。
- 當此規則設定為 **false** 時，偏好不使用解構的變數宣告。

程式碼範例：

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

**csharp\_style\_pattern\_local\_over\_anonymous_function**

- 當此規則設定為 **true** 時，偏好使用區域函式而不是匿名函式。
- 當此規則設定為 **false** 時，偏好使用匿名函式而不是區域函式。

程式碼範例：

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

Editorconfig 檔案範例︰

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
```

#### <a name="null_checking_csharp"></a>"Null" 檢查喜好設定

這些樣式規則是關於 `null` 檢查的語法，包括使用 `throw` 運算式或 `throw` 陳述式，以及叫用 [lambda 運算式](/dotnet/csharp/lambda-expressions)時要執行 null 檢查還是使用條件式聯合運算子 (`?.`)。

下表顯示規則名稱、規則識別碼、適用的語言版本和預設值：

| 規則名稱 | 規則識別碼 | 適用的語言 | Visual Studio 預設值 |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_throw_expression | IDE0016 | C# 7.0+ | true:suggestion |
| csharp_style_conditional_delegate_call | IDE0041 | C# 6.0+ | true:suggestion |

**csharp\_style\_throw_expression**

- 當此規則設定為 **true** 時，希望使用 `throw` 運算式，不要使用 `throw` 陳述式。
- 當此規則設定為 **false** 時，希望使用 `throw` 陳述式，不要使用 `throw` 運算式。

程式碼範例：

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

**csharp\_style\_conditional\_delegate_call**

- 當此規則設定為 **true** 時，希望叫用 lambda 運算式時，使用條件式聯合運算子 (`?.`) 不要執行 null 檢查。
- 當此規則設定為 **false** 時，希望先執行 Null 檢查，再叫用 Lambda 運算式，不要使用條件式聯合運算子 (`?.`)。

程式碼範例：

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

Editorconfig 檔案範例︰

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="code_block"></a>程式碼區塊喜好設定

這個樣式規則是有關使用大括弧 `{ }` 括住程式碼區塊。

下表顯示規則名稱、規則識別碼、適用的語言版本、預設值，以及第一個支援的 Visual Studio 版本：

| 規則名稱 | 規則識別碼 | 適用的語言 | Visual Studio 預設值 | Visual Studio 2017 版本 |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_prefer_braces | IDE0011 | C# | true:none | 15.3 |

**csharp\_prefer\_braces**

- 當此規則設定為 **true** 時，希望使用大括弧，即使只有一行程式碼。
- 當此規則設定為 **false** 時，如果可以，請不要使用大括弧。

程式碼範例：

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

Editorconfig 檔案範例︰

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:none
```

## <a name="formatting-conventions"></a>格式設定慣例

大部分的格式設定慣例規則具有下列格式：

`rule_name = false|true`

您指定 **true** (慣用此樣式) 或 **false** (不喜好此樣式)。 您不用指定嚴重性。 有些規則不是指定 true 或 false，而是指定其他值來描述套用規則的時間及位置。

下列清單顯示 Visual Studio 中可用的格式化慣例規則：

- .NET 格式化設定
    - [組合管理 Using](#usings)
        - dotnet_sort_system_directives_first
- C# 格式化設定
    - [新行字元選項](#newline)
        - csharp_new_line_before_open_brace
        - csharp_new_line_before_else
        - csharp_new_line_before_catch
        - csharp_new_line_before_finally
        - csharp_new_line_before_members_in_object_initializers
        - csharp_new_line_before_members_in_anonymous_types
        - csharp_new_line_between_query_expression_clauses
    - [縮排選項](#indent)
        - csharp_indent_case_contents
        - csharp_indent_switch_labels
        - csharp_indent_labels
    - [間距選項](#spacing)
        - csharp_space_after_cast
        - csharp_space_after_keywords_in_control_flow_statements
        - csharp_space_between_method_declaration_parameter_list_parentheses
        - csharp_space_between_method_call_parameter_list_parentheses
        - csharp_space_between_parentheses
    - [換行選項](#wrapping)
        - csharp_preserve_single_line_statements
        - csharp_preserve_single_line_blocks

### <a name="net-formatting-settings"></a>.NET 格式化設定

本節中的格式化規則適用於 C# 和 Visual Basic。

#### <a name="usings"></a>組合管理 Using

此格式化規則是有關放置 System.* using 指示詞，相對於其他 using 指示詞。

下表顯示規則名稱、適用的語言、預設值，以及第一個支援的 Visual Studio 版本：

| 規則名稱 | 適用的語言 | Visual Studio 預設值 | Visual Studio 2017 版本 |
| ----------- | -------------------- | ----------------------| ----------------  |
| dotnet_sort_system_directives_first |  C# 和 Visual Basic | true | 15.3  |

**dotnet\_sort\_system\_directives_first**

- 當此規則設定為 **true** 時，依字母順序排序 System.* using 指示詞，並將它們放在其他的 using 之前。
- 當此規則設定為 **false** 時，請勿將 System.* using 指示詞放置在其他 using 指示詞之前。

程式碼範例：

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

Editorconfig 檔案範例︰

```EditorConfig
# .NET formatting settings:
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
```

### <a name="c-formatting-settings"></a>C# 格式化設定

本節中的格式化規則只適用於 C# 程式碼。

#### <a name="newline"></a>新行字元選項

這些格式化規則是關於格式化程式碼新行的使用。

下表顯示「新行」規則名稱、適用的語言、預設值，以及第一個支援的 Visual Studio 版本：

| 規則名稱 | 適用的語言 | Visual Studio 預設值 | Visual Studio 2017 版本 |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_new_line_before_open_brace |  C# | 全部 | 15.3  |
| csharp_new_line_before_else |  C# | true | 15.3  |
| csharp_new_line_before_catch |  C# | true | 15.3  |
| csharp_new_line_before_finally |  C# | true | 15.3  |
| csharp_new_line_before_members_in_object_initializers |  C# | true | 15.3  |
| csharp_new_line_before_members_in_anonymous_types |  C# | true | 15.3  |
| csharp_new_line_between_query_expression_clauses |  C# | true | 15.3  |

**csharp\_new\_line\_before\_open_brace**

此規則是有關左大括弧 `{` 應該和前面的程式碼放在同一行還是放在新行中。 此規則不指定 **true** 或 **false**。 請改為指定 [全部]、[無] 或一或多個程式碼項目，例如**方法**或**屬性**，來定義應於何時套用此規則。 下表顯示允許變數的完整清單：

| 值 | 描述
| ------------- |:-------------|
| accessors、anonymous_methods、anonymous_types、control_blocks、events、indexers、lambdas、local_functions、methods、object_collection、properties、types。<br>(請以 ',' 分隔多種類型)。 | 指定的程式碼項目 (也稱為 "Allman" 樣式) 在新行需有括弧 |
| 全部 | 針對所有運算式要求大括弧位於新行上 ("Allman" 樣式) |
| 無 | 針對所有運算式要求大括弧位於同一行上 ("K&R") |

程式碼範例：

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

**csharp\_new\_line\_before_else**

- 當此規則設定為 **true** 時，將 `else` 陳述式放在新的一行。
- 當此規則設定為 **false** 時，將 `else` 陳述式放在同一行。

程式碼範例：

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

**csharp\_new\_line\_before_catch**

- 當此規則設定為 **true** 時，將 `catch` 陳述式放在新的一行。
- 當此規則設定為 **false** 時，將 `catch` 陳述式放在同一行。

程式碼範例：

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

**csharp\_new\_line\_before_finally**

- 當此規則設定為 **true** 時，要求 `finally` 陳述式位於右大括弧之後的新行上。
- 當此規則設定為 **false** 時，要求 `finally` 陳述式和右大括弧位於同行。

程式碼範例：

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

**csharp\_new\_line\_before\_members\_in\_object_initializers**

- 當此規則設定為 **true** 時，要求物件初始設定式的成員位於不同行上。
- 當此規則設定為 **false** 時，要求物件初始設定式的成員位於同行上。

程式碼範例：

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

**csharp\_new\_line\_before\_members\_in\_anonymous_types**

- 當此規則設定為 **true** 時，要求匿名型別的成員位於不同行上。
- 當此規則設定為 **false** 時，要求匿名型別的成員位於同行上。

程式碼範例：

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

**csharp_new_line_between_query_expression_clauses**

- 當此規則設定為 **true** 時，要求查詢運算式子句的項目位於不同行上。
- 當此規則設定為 **false** 時，要求查詢運算式子句的項目位於同行上。

程式碼範例：

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

Editorconfig 檔案範例︰

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="indent"></a>縮排選項

這些格式化規則是關於格式化程式碼縮排的使用。

下表顯示規則名稱、適用的語言、預設值，以及第一個支援的 Visual Studio 版本：

| 規則名稱 | 適用的語言 | Visual Studio 預設值 | Visual Studio 2017 版本 |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_indent_case_contents |  C# | true | 15.3  |
| csharp_indent_switch_labels |  C# | true | 15.3  |
| csharp_indent_labels |  C# | no_change | 15.3  |

**csharp\_indent\_case_contents**

- 當此規則設定為 **true** 時，縮排 `switch` 案例的內容。
- 當此規則設定為 **false** 時，不縮排 `switch` 案例的內容。

程式碼範例：

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent\_switch_labels**

- 當此規則設定為 **true** 時，縮排 `switch` 標籤。
- 當此規則設定為 **false** 時，不縮排 `switch` 標籤。

程式碼範例：

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent_labels**

此規則不接受 **true** 或 **false** 值，但接受下列資料表中的值：

| 值 | 描述 |
| ----- |:----------- |
| flush_left | 標籤放在最左邊的資料行 |
| one_less_than_current | 將標籤置於比目前內容的縮排少一個單位的位置 |
| no_change | 將標籤置於和目前內容相同縮排的位置 |

程式碼範例：

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

Editorconfig 檔案範例︰

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="spacing"></a>間距選項

這些格式化規則是關於格式化程式碼空白字元的使用。

下表顯示規則名稱、適用的語言、預設值，以及第一個支援的 Visual Studio 版本：

| 規則名稱 | 適用的語言 | Visual Studio 預設值 | Visual Studio 2017 版本 |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_space_after_cast |  C# | False | 15.3  |
| csharp_space_after_keywords_in_control_flow_statements |  C# | true | 15.3  |
| csharp_space_between_method_declaration_parameter_ list_parentheses |  C# | False | 15.3  |
| csharp_space_between_method_call_parameter_list_parentheses |  C# | False | 15.3  |
| csharp_space_between_parentheses |  C# | False | 15.3  |

**csharp\_space\_after_cast**

- 當此規則設定為 **true** 時，轉換和值之間需要空格。
- 當此規則設定為 **false** 時，轉換和值之間_不_需要空格。

程式碼範例：

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

**csharp_space_after_keywords_in_control_flow_statements**

- 當此規則設定為 **true** 時；例如，控制流程陳述式中的關鍵字後面需要保留一個空格，例如 `for` 迴圈。
- 當此規則設定為 **false** 時；例如，控制流程陳述式中的關鍵字後面_不_需要保留一個空格，例如 `for` 迴圈。

程式碼範例：

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

**csharp_space_between_method_declaration_parameter_list_parentheses**

- 當此規則設定為 **true** 時，在方法宣告參數清單的左括弧後面和右括弧前面加上空格字元。
- 當此規則設定為 **false** 時，不要在方法宣告參數清單的左括弧後面和右括弧前面加上空格字元。

程式碼範例：

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

**csharp_space_between_method_call_parameter_list_parentheses**

- 當此規則設定為 **true** 時，在方法呼叫的左括弧後面和右括弧前面加上空格字元。
- 當此規則設定為 **false** 時，不要在方法呼叫的左括弧後面和右括弧前面加上空格字元。

程式碼範例：

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

**csharp_space_between_parentheses**

此規則接受下表中的一或多個值：

| 值 | 描述 |
| ----- |:------------|
| control_flow_statements | 在控制流程陳述式的括號之間加入空格 |
| 運算式 | 在運算式的括號之間加入空格 |
| type_casts | 在類型轉換中的括號之間加入空格 |

如果您略過這項規則，或使用 `control_flow_statements`、`expressions` 或 `type_casts` 以外的值，即不套用設定。

程式碼範例：

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

Editorconfig 檔案範例︰

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
```

#### <a name="wrapping"></a>換行選項

這些格式化規則是有關陳述式和程式碼區塊的單一行與個別行的使用。

下表顯示規則名稱、適用的語言、預設值，以及第一個支援的 Visual Studio 版本：

| 規則名稱 | 適用的語言 | Visual Studio 預設值 | Visual Studio 2017 版本 |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_preserve_single_line_statements |  C# | true | 15.3  |
| csharp_preserve_single_line_blocks |  C# | true | 15.3  |

**csharp_preserve_single_line_statements**

- 當此規則設定為 **true** 時，陳述式和成員宣告留在同一行。
- 當此規則設定為 **false** 時，陳述式和成員宣告留在不同行。

程式碼範例：

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

**csharp_preserve_single_line_blocks**

- 當此規則設定為 **true** 時，程式碼區塊留在單一行。
- 當此規則設定為 **false** 時，程式碼區塊留在不同行。

程式碼範例：

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

Editorconfig 檔案範例︰

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

## <a name="see-also"></a>另請參閱

- [快速動作](../ide/quick-actions.md)
- [EditorConfig 的 .NET 命名慣例](../ide/editorconfig-naming-conventions.md)
- [建立可攜式自訂編輯器選項](../ide/create-portable-custom-editor-options.md)
- [.NET 編譯器平台的 .editorconfig 檔案](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
