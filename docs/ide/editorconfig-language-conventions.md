---
title: EditorConfig 的 .NET 語言慣例
ms.date: 03/31/2020
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b9c7da96df8c68de0b9f6ba3e341d93596200934
ms.sourcegitcommit: 1803a67b516f67b209d8f4cf147314e604ef1927
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2020
ms.locfileid: "89641475"
---
# <a name="language-conventions"></a>語言慣例

Visual Studio 中 EditorConfig 的語言慣例分為兩類：適用於 Visual Basic 和 C# 的語言慣例，以及 C# 特定的語言慣例。 語言慣例會影響程式設計語言各個層面的使用方式，例如修飾詞和括弧。

> [!TIP]
> - 若要查看慣用程式設計語言的程式碼範例，請使用瀏覽器視窗右上角的語言選擇器選擇它。
>
>   ![程式碼語言選擇器控制項](media/code-language-picker.png)
>
> - 請使用**本文內容**連結以跳至頁面的不同章節。

## <a name="rule-format"></a>規則格式

語言慣例規則具有下列一般格式：

`option_name = value:severity`

您可以針對每個語言慣例，指定一個定義是否有偏好的樣式和偏好樣式使用時機的值。 許多規則接受的值 `true` (偏好以此樣式) 或 `false` (不偏好使用此樣式) 。 其他規則接受值，例如 `when_on_single_line` 或 `never` 。 第二個部分、指定 [嚴重性][](#severity-levels) 的規則。

::: moniker range=">=vs-2019"

> [!NOTE]
> 因為分析器會強制執行語言慣例，所以您也可以流量分析器的預設設定語法來設定其嚴重性。 語法的格式如下 `dotnet_diagnostic.<rule ID>.severity = <severity>` `dotnet_diagnostic.IDE0040.severity = silent` 。 如需詳細資訊，請參閱 [在 EditorConfig 檔中設定規則嚴重性](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file)。

::: moniker-end

## <a name="severity-levels"></a>嚴重性層級

語言慣例嚴重性可指定要強制執行該樣式的層級。 下表列出可能的嚴重性值及其效果：

Severity | 效果
:------- | ------
`error` | 違反此樣式規則時，顯示編譯器錯誤。
`warning` | 違反此樣式規則時，顯示編譯器警告。
`suggestion` | 當違反這個樣式規則時，會向使用者顯示建議。 建議會顯示為前兩個字元下的三個灰點。
`silent` | 違反這項規則時，不向使用者顯示任何內容。 但程式碼產生功能會以此樣式產生程式碼。 嚴重性的規則 `silent` 會參與清除，並且會出現在 [ **快速動作與重構** ] 功能表中。
`none` | 違反這項規則時，不向使用者顯示任何內容。 但程式碼產生功能會以此樣式產生程式碼。 嚴重性為 `none` 的規則永遠不會出現在 [快速動作及重構]**** 功能表中。 在大部分情況下，這會視為「已停用」或「已忽略」。

::: moniker range=">=vs-2019"

## <a name="automatically-configure-code-styles"></a>自動設定程式碼樣式

從 Visual Studio 2019 版本16.3 開始，您可以在發生樣式違規之後，從 [ [快速動作](quick-actions.md) ] 燈泡功能表設定程式碼樣式規則。

若要變更程式碼樣式慣例：

1. 將滑鼠停留在編輯器的波浪線上，然後開啟顯示的燈泡功能表。 選擇 [**設定或隱藏問題**]  >  **設定程式 \<rule ID> 代碼樣式**。

   ![Visual Studio 中的燈泡功能表設定程式碼樣式](media/vs-2019/configure-code-style.png)

2. 從該處選擇其中一個程式碼樣式選項。

   ![設定程式碼樣式設定](media/vs-2019/configure-code-style-setting.png)

   Visual Studio 新增或修改 EditorConfig 檔案中的設定，如預覽方塊中所示。

若要變更程式碼樣式違規的嚴重性，請遵循相同的步驟，但選擇 [ **設定 \<rule ID> 嚴重性** ]，而不是 [ **設定程式 \<rule ID> 代碼樣式**]。 如需詳細資訊，請參閱 [自動設定規則嚴重性](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity)。

::: moniker-end

## <a name="net-code-style-settings"></a>.NET 程式碼樣式設定

本節中的樣式規則對 C# 和 Visual Basic 都適用。

- ["This." 和 "Me." 限定詞](#this-and-me)
  - dotnet\_style\_qualification\_for_field
  - dotnet\_style\_qualification\_for_property
  - dotnet\_style\_qualification\_for_method
  - dotnet\_style\_qualification\_for_event
- [語言關鍵字而非類型參考的架構類型名稱](#language-keywords)
  - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
  - dotnet\_style\_predefined\_type\_for\_member_access
- [修飾詞喜好設定](#normalize-modifiers)
  - dotnet\_style\_require\_accessibility_modifiers
  - visual\_basic\_preferred\_modifier_order
  - dotnet\_style\_readonly\_field
- [括弧喜好設定](#parentheses-preferences)
  - dotnet\_style\_parentheses\_in\_arithmetic\_binary\_operators
  - dotnet\_style\_parentheses\_in\_other\_binary\_operators
  - dotnet\_style\_parentheses\_in\_other\_operators
  - dotnet\_style\_parentheses\_in\_relational\_binary\_operators
- [運算式層級喜好設定](#expression-level-preferences)
  - dotnet\_style\_object_initializer
  - dotnet\_style\_collection_initializer
  - dotnet\_style\_explicit\_tuple_names
  - dotnet\_style\_prefer\_inferred\_tuple_names
  - dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names
  - dotnet\_style\_prefer\_auto\_properties
  - dotnet\_style\_prefer\_conditional\_expression\_over\_assignment
  - dotnet\_style\_prefer\_conditional\_expression\_over\_return
  - dotnet\_style\_prefer\_compound\_assignment
- ["Null" 檢查喜好設定](#null-checking-preferences)
  - dotnet\_style\_coalesce_expression
  - dotnet\_style\_null_propagation
  - dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

### <a name="this-and-me-qualifiers"></a><a name="this-and-me"></a>"This." 和 "Me." 限定詞

此樣式規則可以套用到欄位、屬性、方法或事件。 **true** 值表示希望程式碼符號在 C# 中以 `this.` 開頭或在 Visual Basic 中以 `Me.` 開頭。 **false** 值表示希望程式碼項目前面_不_要加上 `this.` 或 `Me.`。

這些規則可能會出現在 .editorconfig** 檔案中，如下所示：

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="dotnet_style_qualification_for_field"></a>dotnet\_style\_qualification\_for_field

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_qualification_for_field |
| **規則識別碼** | IDE0003 和 IDE0009 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `true` - 希望欄位在 C# 中以 `this.` 開頭，或在 Visual Basic 中以 `Me.` 開頭<br /><br />`false` - 希望欄位「不」__ 以 `this.` 或 `Me.` 開頭 |
| **Visual Studio 預設值** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_property"></a>dotnet\_style\_qualification\_for_property

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_qualification_for_property |
| **規則識別碼** | IDE0003 和 IDE0009 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `true` - 希望屬性在 C# 中以 `this.` 開頭，或在 Visual Basic 中以 `Me.` 開頭<br /><br />`false` - 希望屬性「不」__ 以 `this.` 或 `Me.` 開頭 |
| **Visual Studio 預設值** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_method"></a>dotnet\_style\_qualification\_for_method

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_qualification_for_method |
| **規則識別碼** | IDE0003 和 IDE0009 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `true` - 希望方法在 C# 中以 `this.` 開頭，或在 Visual Basic 中以 `Me.` 開頭。<br /><br />`false` - 希望方法「不」__ 以 `this.` 或 `Me.` 開頭。 |
| **Visual Studio 預設值** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_event"></a>dotnet\_style\_qualification\_for_event

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_qualification_for_event |
| **規則識別碼** | IDE0003 和 IDE0009 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `true` - 希望事件在 C# 中以 `this.` 開頭，或在 Visual Basic 中以 `Me.` 開頭。<br /><br />`false` - 希望事件「不」__ 以 `this.` 或 `Me.` 開頭。 |
| **Visual Studio 預設值** | `false:silent` |

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

### <a name="language-keywords-instead-of-framework-type-names-for-type-references"></a><a name="language-keywords"></a>語言關鍵字而非類型參考的架構類型名稱

此樣式規則可以套用至本機變數、方法參數和類別成員，或作為類型成員存取運算式的不同規則。 值為 **true** 表示偏好語言關鍵字 (例如 `int` 或 `Integer`) 而不是以關鍵字代表型別的型別名稱 (例如 `Int32`)。 值為 **false** 表示偏好類型名稱，而不是語言關鍵字。

這些規則可能會出現在 .editorconfig** 檔案中，如下所示：

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="dotnet_style_predefined_type_for_locals_parameters_members"></a>dotnet\_style\_predefined\_type\_for\_locals\_parameters_members

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_predefined_type_for_locals_parameters_members |
| **規則識別碼** | IDE0012 和 IDE0014 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `true` - 希望是本機變數、方法參數和類別成員的語言關鍵字，而不是以關鍵字表示類型的類型名稱<br /><br />`false` - 希望是本機變數、方法參數和類別成員的類型名稱，而不是語言關鍵字 |
| **Visual Studio 預設值** | `true:silent` |

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

#### <a name="dotnet_style_predefined_type_for_member_access"></a>dotnet\_style\_predefined\_type\_for\_member_access

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_predefined_type_for_member_access |
| **規則識別碼** | IDE0013 和 IDE0015 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `true` - 希望是成員存取運算式的語言關鍵字，而不是以關鍵字表示類型的類型名稱<br /><br />`false` - 希望是成員存取運算式的類型名稱，而不是語言關鍵字 |
| **Visual Studio 預設值** | `true:silent` |

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

### <a name="modifier-preferences"></a><a name="normalize-modifiers"></a>修飾詞喜好設定

本節中的樣式規則與修飾詞喜好設定有關，包括要求存取範圍修飾詞、指定所需的修飾詞排序次序和要求唯讀修飾詞。

這些規則可能會出現在 .editorconfig** 檔案中，如下所示：

```ini
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

#### <a name="dotnet_style_require_accessibility_modifiers"></a>dotnet\_style\_require\_accessibility_modifiers

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_require_accessibility_modifiers |
| **規則識別碼** | IDE0040 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `always` - 偏好指定存取範圍修飾詞。<br /><br />`for_non_interface_members` - 偏好宣告存取範圍修飾詞，但公用介面成員除外。 (這是與**一律**相同，且已新增以便未來 C# 新增預設介面方法時校訂之用。)<br /><br />`never` - 偏好不指定存取範圍修飾詞。<br /><br />`omit_if_default` - 偏好指定存取範圍修飾詞，除非它們是預設修飾詞。 |
| **Visual Studio 預設值** | `for_non_interface_members:silent` |
| **引進的版本** | Visual Studio 2017 15.5 版 |

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

#### <a name="csharp_preferred_modifier_order"></a>csharp_preferred_modifier_order

|屬性|值|
|-|-|
| **規則名稱** | csharp_preferred_modifier_order |
| **規則識別碼** | IDE0036 |
| **適用的語言** | C# |
| **值** | 一或多個 C# 修飾詞，例如 `public`、`private` 和 `protected` |
| **Visual Studio 預設值** | `public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent` |
| **引進的版本** | Visual Studio 2017 15.5 版 |

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

#### <a name="visual_basic_preferred_modifier_order"></a>visual_basic_preferred_modifier_order

|屬性|值|
|-|-|
| **規則名稱** | visual_basic_preferred_modifier_order |
| **規則識別碼** | IDE0036 |
| **適用的語言** | Visual Basic |
| **值** | 一或多個 Visual Basic 修飾詞，例如 `Partial`、`Private` 和 `Public` |
| **Visual Studio 預設值** | `Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:silent` |
| **引進的版本** | Visual Studio 2017 15.5 版 |

- 當此規則設定為修飾詞清單時，偏好指定排序。
- 當此規則從檔案中省略時，偏好不排序修飾詞。

程式碼範例：

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

#### <a name="visual_basic_style_unused_value_expression_statement_preference"></a>visual_basic_style_unused_value_expression_statement_preference

|屬性|值|
|-|-|
| **規則名稱** | visual_basic_style_unused_value_expression_statement_preference |
| **規則識別碼** | IDE0058 |
| **適用的語言** | Visual Basic |
| **值** | `unused_local_variable:silent` |
| **Visual Studio 預設值** | `unused_local_variable:silent` |

程式碼範例：

```vb
' visual_basic_style_unused_value_expression_statement_preference = unused_local_variable:silent

Dim unused = Computation()
```

#### <a name="visual_basic_style_unused_value_assignment_preference"></a>visual_basic_style_unused_value_assignment_preference

|屬性|值|
|-|-|
| **規則名稱** | visual_basic_style_unused_value_assignment_preference |
| **規則識別碼** | IDE0059 |
| **適用的語言** | Visual Basic |
| **值** | `unused_local_variable:silent` |
| **Visual Studio 預設值** | `unused_local_variable:silent` |

程式碼範例：

```vb
' visual_basic_style_unused_value_assignment_preference = unused_local_variable:suggestion

Dim unused = Computation()
Dim x = 1;
```

#### <a name="dotnet_style_readonly_field"></a>dotnet_style_readonly_field

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_readonly_field |
| **規則識別碼** | IDE0044 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `true` - 偏好欄位應該標記 `readonly` (C#) 或 `ReadOnly` (Visual Basic)，如果只是內嵌指派，或在建構函式內指派的話<br /><br />`false` - 對於欄位是否應標記 `readonly` (C#) 或 `ReadOnly` (Visual Basic)，不指派喜好設定 |
| **Visual Studio 預設值** | `true:suggestion` |
| **引進的版本** | Visual Studio 2017 15.7 版 |

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

### <a name="parentheses-preferences"></a>括號喜好設定

本節中的樣式規則與括號喜好設定有關，包括對於算數、關係及其他二元運算子的括號用法。

這些規則可能會出現在 .editorconfig** 檔案中，如下所示：

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="dotnet_style_parentheses_in_arithmetic_binary_operators"></a>dotnet\_style\_parentheses\_in\_arithmetic\_binary_operators

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_parentheses_in_arithmetic_binary_operators |
| **規則識別碼** | IDE0047 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `always_for_clarity` - 建議使用括弧來說明算術運算子 (`*`、`/`、`%`、`+`、`-`、`<<`、`>>`、`&`、`^`、`|`) 優先順序<br /><br />`never_if_unnecessary` - 使用算術運算子時建議不使用括弧 (`*`、`/`、`%`、`+`、`-`、`<<`、`>>`、`&`、`^`、`|`) 優先順序 |
| **Visual Studio 預設值** | `always_for_clarity:silent` |
| **引進的版本** | Visual Studio 2017 15.8 版 |

程式碼範例：

```csharp
// dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
var v = a + (b * c);

// dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
var v = a + b * c;
```

```vb
' dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
Dim v = a + (b * c)

' dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
Dim v = a + b * c
```

#### <a name="dotnet_style_parentheses_in_relational_binary_operators"></a>dotnet\_style\_parentheses\_in\_relational\_binary_operators

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_parentheses_in_relational_binary_operators |
| **規則識別碼** | IDE0047 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `always_for_clarity` - 建議使用括弧來說明關係運算子 (`>`、`<`、`<=`、`>=`、`is`、`as`、`==`、`!=`) 優先順序<br /><br />`never_if_unnecessary` - 使用關係運算子時建議不使用括弧 (`>`、`<`、`<=`、`>=`、`is`、`as`、`==`、`!=`) 優先順序 |
| **Visual Studio 預設值** | `always_for_clarity:silent` |
| **引進的版本** | Visual Studio 2017 15.8 版 |

程式碼範例：

```csharp
// dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
var v = (a < b) == (c > d);

// dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
var v = a < b == c > d;
```

```vb
' dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
Dim v = (a < b) = (c > d)

' dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
Dim v = a < b = c > d
```

#### <a name="dotnet_style_parentheses_in_other_binary_operators"></a>dotnet\_style\_parentheses\_in\_other\_binary_operators

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_parentheses_in_other_binary_operators |
| **規則識別碼** | IDE0047 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `always_for_clarity` - 建議使用括弧來說明其他二元運算子 (`&&`、`||`、`??`) 優先順序<br /><br />`never_if_unnecessary` - 使用其他二元運算子時建議不使用括弧 (`&&`、`||`、`??`) 優先順序 |
| **Visual Studio 預設值** | `always_for_clarity:silent` |
| **引進的版本** | Visual Studio 2017 15.8 版 |

程式碼範例：

```csharp
// dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
var v = a || (b && c);

// dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
var v = a || b && c;
```

```vb
' dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
Dim v = a OrElse (b AndAlso c)

' dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
Dim v = a OrElse b AndAlso c
```

#### <a name="dotnet_style_parentheses_in_other_operators"></a>dotnet\_style\_parentheses\_in\_other_operators

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_parentheses_in_other_operators |
| **規則識別碼** | IDE0047 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `always_for_clarity` - 建議使用括弧來說明運算子優先順序<br /><br />`never_if_unnecessary` - 當運算子優先順序很明顯時建議不使用括弧 |
| **Visual Studio 預設值** | `never_if_unnecessary:silent` |
| **引進的版本** | Visual Studio 2017 15.8 版 |

程式碼範例：

```csharp
// dotnet_style_parentheses_in_other_operators = always_for_clarity
var v = (a.b).Length;

// dotnet_style_parentheses_in_other_operators = never_if_unnecessary
var v = a.b.Length;
```

```vb
' dotnet_style_parentheses_in_other_operators = always_for_clarity
Dim v = (a.b).Length

' dotnet_style_parentheses_in_other_operators = never_if_unnecessary
Dim v = a.b.Length
```

### <a name="expression-level-preferences"></a>運算式層級喜好設定

本節中的樣式規則涉及運算式層級喜好設定，包括使用物件初始設定式、集合初始設定式、明確或推斷的 Tuple 名稱，以及推斷的匿名類型。

這些規則可能會出現在 .editorconfig** 檔案中，如下所示：

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
dotnet_style_prefer_compound_assignment = true:suggestion
```

#### <a name="dotnet_style_object_initializer"></a>dotnet\_style\_object_initializer

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_object_initializer |
| **規則識別碼** | IDE0017 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `true` - 偏好盡可能使用物件初始設定式來初始化物件<br /><br />`false` - 偏好「不」** 使用物件初始設定式來初始化物件 |
| **Visual Studio 預設值** | `true:suggestion` |

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

#### <a name="dotnet_style_collection_initializer"></a>dotnet\_style\_collection_initializer

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_collection_initializer |
| **規則識別碼** | IDE0028 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `true` - 偏好盡可能使用集合初始設定式來初始化集合<br /><br />`false` - 偏好「不」** 使用集合初始設定式來初始化集合 |
| **Visual Studio 預設值** | `true:suggestion` |

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

#### <a name="dotnet_style_explicit_tuple_names"></a>dotnet\_style\_explicit\_tuple_names

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_explicit_tuple_names |
| **規則識別碼** | IDE0033 |
| **適用的語言** | C# 7.0+ 和 Visual Basic 15+ |
| **值** | `true` - 偏好 Tuple 名稱勝過 ItemX 屬性<br /><br />`false` - 偏好 ItemX 屬性勝過 Tuple 名稱 |
| **Visual Studio 預設值** | `true:suggestion` |

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

#### <a name="dotnet_style_prefer_inferred_tuple_names"></a>dotnet\_style\_prefer\_inferred\_tuple_names

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_prefer_inferred_tuple_names |
| **規則識別碼** | IDE0037 |
| **適用的語言** | C# 7.1+ 和 Visual Basic 15+ |
| **值** | `true` - 優先使用推斷的元組元素名稱<br /><br />`false` - 優先使用明確的元組元素名稱 |
| **Visual Studio 預設值** | `true:suggestion` |
| **引進的版本** | Visual Studio 2017 15.6 版 |

程式碼範例：

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

```vb
' dotnet_style_prefer_inferred_tuple_names = true
Dim tuple = (name, age)

' dotnet_style_prefer_inferred_tuple_names = false
Dim tuple = (name:=name, age:=age)
```

#### <a name="dotnet_style_prefer_inferred_anonymous_type_member_names"></a>dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_prefer_inferred_anonymous_type_member_names |
| **規則識別碼** | IDE0037 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `true` - 優先使用推斷的匿名型別成員名稱<br /><br />`false` - 優先使用明確的匿名型別成員名稱 |
| **Visual Studio 預設值** | `true:suggestion` |
| **引進的版本** | Visual Studio 2017 15.6 版 |

程式碼範例：

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };
```

```vb
' dotnet_style_prefer_inferred_anonymous_type_member_names = true
Dim anon = New With {name, age}

' dotnet_style_prefer_inferred_anonymous_type_member_names = false
Dim anon = New With {.name = name, .age = age}
```

#### <a name="dotnet_style_prefer_auto_properties"></a>dotnet\_style\_prefer\_auto\_properties

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_prefer_auto_properties |
| **規則識別碼** | IDE0032 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `true` - 優先使用 autoproperties，而非包含私用支援欄位的屬性<br /><br />`false` - 優先使用包含私用支援欄位的屬性，而非 autoproperties |
| **Visual Studio 預設值** | `true:suggestion` |
| **引進的版本** | Visual Studio 2017 15.7 版 |

程式碼範例：

```csharp
// dotnet_style_prefer_auto_properties = true
private int Age { get; }

// dotnet_style_prefer_auto_properties = false
private int age;

public int Age
{
    get
    {
        return age;
    }
}
```

```vb
' dotnet_style_prefer_auto_properties = true
Public ReadOnly Property Age As Integer

' dotnet_style_prefer_auto_properties = false
Private _age As Integer

Public ReadOnly Property Age As Integer
    Get
        return _age
    End Get
End Property
```

#### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **規則識別碼** | IDE0041 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `true` - 優先使用包含樣式比對的 Null 檢查，而非 `object.ReferenceEquals`<br /><br />`false` - 優先使用 `object.ReferenceEquals`，而非包含樣式比對的 Null 檢查 |
| **Visual Studio 預設值** | `true:suggestion` |
| **引進的版本** | Visual Studio 2017 15.7 版 |

程式碼範例：

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```

#### <a name="dotnet_style_prefer_conditional_expression_over_assignment"></a>dotnet\_style\_prefer\_conditional\_expression\_over_assignment

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_prefer_conditional_expression_over_assignment |
| **規則識別碼** | IDE0045 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `true` - 優先使用具有三元條件式的指派，而不是 if else 陳述式<br /><br />`false` - 優先使用具有 if else 陳述式的指派，而不是三元條件式 |
| **Visual Studio 預設值** | `true:suggestion` |
| **引進的版本** | Visual Studio 2017 15.8 版 |

程式碼範例：

```csharp
// dotnet_style_prefer_conditional_expression_over_assignment = true
string s = expr ? "hello" : "world";

// dotnet_style_prefer_conditional_expression_over_assignment = false
string s;
if (expr)
{
    s = "hello";
}
else
{
    s = "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_assignment = true
Dim s As String = If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_assignment = false
Dim s As String
If expr Then
    s = "hello"
Else
    s = "world"
End If
```

#### <a name="dotnet_style_prefer_conditional_expression_over_return"></a>dotnet\_style\_prefer\_conditional\_expression\_over_return

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_prefer_conditional_expression_over_return |
| **規則識別碼** | IDE0046 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `true` - 優先使用 return 陳述式以使用三元條件式，而不是 if else 陳述式<br /><br />`false` - 優先使用 return 陳述式以使用 if else 陳述式，而不是三元條件式 |
| **Visual Studio 預設值** | `true:suggestion` |
| **引進的版本** | Visual Studio 2017 15.8 版 |

程式碼範例：

```csharp
// dotnet_style_prefer_conditional_expression_over_return = true
return expr ? "hello" : "world"

// dotnet_style_prefer_conditional_expression_over_return = false
if (expr)
{
    return "hello";
}
else
{
    return "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_return = true
Return If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_return = false
If expr Then
    Return "hello"
Else
    Return "world"
End If
```

#### <a name="dotnet_style_prefer_compound_assignment"></a>dotnet\_style\_prefer\_compound\_assignment

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_prefer_compound_assignment |
| **規則識別碼** | IDE0054 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `true` - 偏好[複合指派](/dotnet/csharp/language-reference/operators/assignment-operator#compound-assignment)運算式<br /><br />`false`不偏好複合指派運算式 |
| **Visual Studio 預設值** | `true:suggestion` |

程式碼範例：

```csharp
// dotnet_style_prefer_compound_assignment = true
x += 1;

// dotnet_style_prefer_compound_assignment = false
x = x + 1;
```

```vb
' dotnet_style_prefer_compound_assignment = true
x += 1

' dotnet_style_prefer_compound_assignment = false
x = x + 1
```

### <a name="null-checking-preferences"></a>Null 檢查喜好設定

本節中的樣式規則涉及 null 檢查喜好設定。

這些規則可能會出現在 .editorconfig** 檔案中，如下所示：

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
```

#### <a name="dotnet_style_coalesce_expression"></a>dotnet\_style\_coalesce_expression

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_coalesce_expression |
| **規則識別碼** | IDE0029 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `true` - 偏好 null 聯合運算式勝過三元運算子檢查<br /><br />`false` - 偏好三元運算子檢查勝過 null 聯合運算式 |
| **Visual Studio 預設值** | `true:suggestion` |

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

#### <a name="dotnet_style_null_propagation"></a>dotnet\_style\_null_propagation

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_null_propagation |
| **規則識別碼** | IDE0031 |
| **適用的語言** | C# 6.0+ 和 Visual Basic 14+ |
| **值** | `true` - 偏好盡可能使用 Null 條件運算子<br /><br />`false` - 偏好盡可能使用三元 Null 檢查 |
| **Visual Studio 預設值** | `true:suggestion` |

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

### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

|屬性|值|
|-|-|
| **規則名稱** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **規則識別碼** | IDE0041 |
| **適用的語言** | C# 6.0+ 和 Visual Basic 14+ |
| **值** | `true` -偏好為參考相等方法的 null 檢查<br /><br />`false` -偏好參考相等的方法為 null 檢查 |
| **Visual Studio 預設值** | `true:silent` |

程式碼範例：

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```

## <a name="net-code-quality-settings"></a>.NET 程式碼品質設定

本節中的品質規則適用於 C# 和 Visual Basic 程式碼。 它們可用來設定 Visual Studio 整合式開發環境 (IDE) 中內建的程式碼分析器。 如需使用 EditorConfig 檔設定 FxCop 分析器的資訊，請參閱[設定 FxCop 分析器](../code-quality/configure-fxcop-analyzers.md)。

- [參數喜好設定](#parameter-preferences)
  - dotnet\_code\_quality\_unused\_parameters

### <a name="parameter-preferences"></a>參數喜好設定

本節中的品質規則涉及方法參數。

這些規則可能會出現在 .editorconfig** 檔案中，如下所示：

```ini
# CSharp and Visual Basic code quality settings:
[*.{cs,vb}]
dotnet_code_quality_unused_parameters = all:suggestion
```

#### <a name="dotnet_code_quality_unused_parameters"></a>dotnet\_code\_quality\_unused\_parameters

|屬性|值|
|-|-|
| **規則名稱** | dotnet_code_quality_unused_parameters |
| **規則識別碼** | IDE0060 |
| **適用的語言** | C# 和 Visual Basic |
| **值** | `all` - 將具有包含未使用參數的協助工具方法加上旗標<br /><br />`non_public` - 僅將包含未使用參數的非公用方法加上旗標 |
| **Visual Studio 預設值** | `all:suggestion` |

程式碼範例：

```csharp
// dotnet_code_quality_unused_parameters = all:suggestion
public int GetNum() { return 1; }

// dotnet_code_quality_unused_parameters = non_public:suggestion
public int GetNum(int arg1) { return 1; }
```

```vb
' dotnet_code_quality_unused_parameters = all:suggestion
Public Function GetNum()
    Return 1
End Function

' dotnet_code_quality_unused_parameters = non_public:suggestion
Public Function GetNum(arg1 As Integer)
    Return 1
End Function
```

## <a name="c-code-style-settings"></a>C# 程式碼樣式設定

本節中的樣式規則只適用於 C#。

- [隱含和明確類型](#implicit-and-explicit-types)
  - csharp\_style\_var\_for\_built\_in_types
  - csharp\_style\_var\_when\_type\_is_apparent
  - csharp\_style\_var_elsewhere
- [運算式主體成員](#expression-bodied-members)
  - csharp\_style\_expression\_bodied_methods
  - csharp\_style\_expression\_bodied_constructors
  - csharp\_style\_expression\_bodied_operators
  - csharp\_style\_expression\_bodied_properties
  - csharp\_style\_expression\_bodied_indexers
  - csharp\_style\_expression\_bodied_accessors
  - csharp\_style\_expression\_bodied_lambdas
  - csharp\_style\_expression\_bodied\_local_functions
- [模式比對](#pattern-matching)
  - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
  - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
- [內嵌變數宣告](#inlined-variable-declarations)
  - csharp\_style\_inlined\_variable_declaration
- [運算式層級喜好設定](#c-expression-level-preferences)
  - csharp\_prefer\_simple\_default_expression
- ["Null" 檢查喜好設定](#c-null-checking-preferences)
  - csharp\_style\_throw_expression
  - csharp\_style\_conditional\_delegate_call
- [修飾詞喜好設定](#normalize-modifiers)
  - csharp\_preferred\_modifier_order
- [程式碼區塊喜好設定](#code-block-preferences)
  - csharp\_prefer_braces
- [未使用的值喜好設定](#unused-value-preferences)
  - csharp\_style\_unused\_value\_expression\_statement_preference
  - csharp\_style\_unused\_value\_assignment_preference
- [索引和範圍喜好設定](#index-and-range-preferences)
  - csharp\_style\_prefer\_index_operator
  - csharp\_style\_prefer\_range_operator
- [其他喜好設定](#miscellaneous-preferences)
  - csharp\_style\_deconstructed\_variable_declaration
  - csharp\_style\_pattern\_local\_over\_anonymous_function
  - csharp\_using\_directive\_placement
  - csharp\_prefer\_static\_local_function
  - csharp\_prefer\_simple\_using_statement
  - csharp\_style\_prefer\_switch_expression

### <a name="implicit-and-explicit-types"></a>隱含和明確類型

本節中的樣式規則是關於使用 [var](/dotnet/csharp/language-reference/keywords/var) 關鍵字與變數宣告中的明確類型。 當類型顯然位於其他位置時，這項規則可以分別套用至內建類型。

Editorconfig ** 檔案範例︰

```ini
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="csharp_style_var_for_built_in_types"></a>csharp\_style\_var\_for\_built\_in_types

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_var_for_built_in_types |
| **規則識別碼** | IDE0007 和 IDE0008 |
| **適用的語言** | C#  |
| **值** | `true` - 偏好使用 `var` 宣告變數搭配內建系統類型，例如 `int`<br /><br />`false` - 偏好使用明確類型勝過 `var`，以宣告變數搭配內建系統類型，例如 `int` |
| **Visual Studio 預設值** | `true:silent` |

程式碼範例：

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

#### <a name="csharp_style_var_when_type_is_apparent"></a>csharp\_style\_var\_when\_type\_is_apparent

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_var_when_type_is_apparent |
| **規則識別碼** | IDE0007 和 IDE0008 |
| **適用的語言** | C#  |
| **值** | `true` - 在宣告運算式右側已提到類型時偏好使用 `var`<br /><br />`false` - 在宣告運算式右側已提到類型時偏好使用明確類型勝過 `var` |
| **Visual Studio 預設值** | `true:silent` |

程式碼範例：

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

#### <a name="csharp_style_var_elsewhere"></a>csharp\_style\_var_elsewhere

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_var_elsewhere |
| **規則識別碼** | IDE0007 和 IDE0008 |
| **適用的語言** | C#  |
| **值** | `true` - 除非為另一個程式碼樣式規則覆寫，否則所有情況都偏好使用 `var`，而非明確類型<br /><br />`false` - 除非為另一個程式碼樣式規則覆寫，否則所有情況都偏好使用明確類型，而非 `var` |
| **Visual Studio 預設值** | `true:silent` |

程式碼範例：

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

### <a name="expression-bodied-members"></a>運算式主體成員

本節中的樣式規則是關於當邏輯由單一運算式組成時，使用[運算式主體成員](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members)。 此規則可套用至方法、建構函式、運算子、屬性、索引子及存取子。

Editorconfig ** 檔案範例︰

```ini
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
csharp_style_expression_bodied_lambdas = true:silent
csharp_style_expression_bodied_local_functions = false:silent
```

#### <a name="csharp_style_expression_bodied_methods"></a>csharp\_style\_expression\_bodied_methods

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_expression_bodied_methods |
| **規則識別碼** | IDE0022 |
| **適用的語言** | C# 6.0+  |
| **值** | `true` - 偏好針對方法使用運算式主體<br /><br />`when_on_single_line` - 當所有方法都在同一行時，偏好針對方法使用運算式主體<br /><br />`false` - 偏好針對方法使用區塊主體 |
| **Visual Studio 預設值** | `false:silent` |

程式碼範例：

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

#### <a name="csharp_style_expression_bodied_constructors"></a>csharp\_style\_expression\_bodied_constructors

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_expression_bodied_constructors |
| **規則識別碼** | IDE0021 |
| **適用的語言** | C# 7.0+ |
| **值** | `true` - 偏好針對建構函式使用運算式主體<br /><br />`when_on_single_line` - 當所有建構函式都在同一行時，偏好針對建構函式使用運算式主體<br /><br />`false` - 偏好針對建構函式使用區塊主體 |
| **Visual Studio 預設值** | `false:silent` |

程式碼範例：

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

#### <a name="csharp_style_expression_bodied_operators"></a>csharp\_style\_expression\_bodied_operators

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_expression_bodied_operators |
| **規則識別碼** | IDE0023 和 IDE0024 |
| **適用的語言** | C# 7.0+ |
| **值** | `true` - 偏好針對運算子使用運算式主體<br /><br />`when_on_single_line` - 當所有運算子都在同一行時，偏好針對運算子使用運算式主體<br /><br />`false` - 偏好針對運算子使用區塊主體 |
| **Visual Studio 預設值** | `false:silent` |

程式碼範例：

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

#### <a name="csharp_style_expression_bodied_properties"></a>csharp\_style\_expression\_bodied_properties

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_expression_bodied_properties |
| **規則識別碼** | IDE0025 |
| **適用的語言** | C# 7.0+ |
| **值** | `true` - 偏好針對屬性使用運算式主體<br /><br />`when_on_single_line` - 當所有屬性都在同一行時，偏好針對屬性使用運算式主體<br /><br />`false` - 偏好針對屬性使用區塊主體 |
| **Visual Studio 預設值** | `true:silent` |

程式碼範例：

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

#### <a name="csharp_style_expression_bodied_indexers"></a>csharp\_style\_expression\_bodied_indexers

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_expression_bodied_indexers |
| **規則識別碼** | IDE0026 |
| **適用的語言** | C# 7.0+ |
| **值** | `true` - 偏好針對索引子使用運算式主體<br /><br />`when_on_single_line` - 當所有索引子都在同一行時，偏好針對索引子使用運算式主體<br /><br />`false` - 偏好針對索引子使用區塊主體 |
| **Visual Studio 預設值** | `true:silent` |

程式碼範例：

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

#### <a name="csharp_style_expression_bodied_accessors"></a>csharp\_style\_expression\_bodied_accessors

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_expression_bodied_accessors |
| **規則識別碼** | IDE0027 |
| **適用的語言** | C# 7.0+ |
| **值** | `true` - 偏好針對存取子使用運算式主體<br /><br />`when_on_single_line` - 當所有存取子都在同一行時，偏好針對存取子使用運算式主體<br /><br />`false` - 偏好針對存取子使用區塊主體 |
| **Visual Studio 預設值** | `true:silent` |

程式碼範例：

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

#### <a name="csharp_style_expression_bodied_lambdas"></a>csharp\_style\_expression\_bodied_lambdas

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_expression_bodied_lambdas |
| **規則識別碼** | IDE0053 |
| **值** | `true` - 偏好針對 Lambda 使用運算式主體<br /><br />`when_on_single_line` - 當所有 Lambda 都在同一行時，偏好針對 Lambda 使用運算式主體<br /><br />`false` - 偏好針對 Lambda 使用區塊主體 |
| **Visual Studio 預設值** | `true:silent` |

程式碼範例：

```csharp
// csharp_style_expression_bodied_lambdas = true
Func<int, int> square = x => x * x;

// csharp_style_expression_bodied_lambdas = false
Func<int, int> square = x => { return x * x; };
```

#### <a name="csharp_style_expression_bodied_local_functions"></a>csharp\_style\_expression\_bodied\_local_functions

從 C# 7.0 開始，C# 支援「區域函式」[](/dotnet/csharp/programming-guide/classes-and-structs/local-functions)。 區域函式是另一個成員中巢狀型別的私用方法。

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_expression_bodied_local_functions |
| **規則識別碼** | IDE0061 |
| **適用的語言** | C# 7.0+ |
| **值** | `true` - 偏好針對區域函式使用運算式主體<br /><br />`when_on_single_line` - 當所有區域函式都在同一行時，偏好針對區域函式使用運算式主體<br /><br />`false` - 偏好針對區域函式使用區塊主體 |
| **Visual Studio 預設值** | `false:silent` |

程式碼範例：

```csharp
// csharp_style_expression_bodied_local_functions = true
void M()
{
    Hello();
    void Hello() => Console.WriteLine("Hello");
}

// csharp_style_expression_bodied_local_functions = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

### <a name="pattern-matching"></a>模式比對

本節中的樣式規則是關於在 C# 中使用[模式比對](/dotnet/csharp/pattern-matching)。

Editorconfig ** 檔案範例︰

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="csharp_style_pattern_matching_over_is_with_cast_check"></a>csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_pattern_matching_over_is_with_cast_check |
| **規則識別碼** | IDE0020 |
| **適用的語言** | C# 7.0+ |
| **值** | `true` - 偏好模式比對，而非具有類型轉換的 `is` 運算式<br /><br />`false` - 偏好具有類型轉換的 `is` 運算式，而非模式比對 |
| **Visual Studio 預設值** | `true:suggestion` |

程式碼範例：

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

#### <a name="csharp_style_pattern_matching_over_as_with_null_check"></a>csharp\_style\_pattern\_matching\_over\_as\_with\_null_check

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_pattern_matching_over_as_with_null_check |
| **規則識別碼** | IDE0019 |
| **適用的語言** | C# 7.0+ |
| **值** | `true` - 偏好使用模式比對，而非具有 Null 檢查的 `as` 運算式，以判斷是否為特定類型<br /><br />`false` - 偏好使用具有 Null 檢查的 `as` 運算式，而非模式比對，以判斷是否為特定類型 |
| **Visual Studio 預設值** | `true:suggestion` |

程式碼範例：

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

### <a name="inlined-variable-declarations"></a>內嵌變數宣告

這個樣式規則考量 `out` 變數是否宣告內嵌。 從 C# 7 開始，您可以[在方法呼叫的引數清單中宣告 out 變數](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument)，而非在其他的變數中宣告。

#### <a name="csharp_style_inlined_variable_declaration"></a>csharp\_style\_inlined\_variable_declaration

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_inlined_variable_declaration |
| **規則識別碼** | IDE0018 |
| **適用的語言** | C# 7.0+ |
| **值** | `true` - 偏好盡可能在方法呼叫的引數清單中宣告 `out` 變數內嵌<br /><br />`false` - 偏好先宣告 `out` 變數再宣告方法呼叫 |
| **Visual Studio 預設值** | `true:suggestion` |

程式碼範例：

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Editorconfig ** 檔案範例︰

```ini
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

### <a name="c-expression-level-preferences"></a>C# 運算式層級喜好設定

本節中的樣式規則涉及算式層級喜好設定。

Editorconfig ** 檔案範例︰

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
```

#### <a name="csharp_prefer_simple_default_expression"></a>csharp\_prefer\_simple\_default_expression

當編譯器可以推斷運算式的類型時，這個樣式規則會考慮使用[ `default` 預設值運算式的常值](/dotnet/csharp/language-reference/operators/default#default-literal)。

|屬性|值|
|-|-|
| **規則名稱** | csharp_prefer_simple_default_expression |
| **規則識別碼** | IDE0034 |
| **適用的語言** | C# 7.1+  |
| **值** | `true` - 偏好 `default` 而非 `default(T)`<br /><br />`false` - 偏好 `default(T)` 而非 `default` |
| **Visual Studio 預設值** | `true:suggestion` |

程式碼範例：

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

### <a name="c-null-checking-preferences"></a>C# Null 檢查喜好設定

這些樣式規則是關於 `null` 檢查的語法，包括使用 `throw` 運算式或 `throw` 陳述式，以及叫用 [lambda 運算式](/dotnet/csharp/lambda-expressions)時要執行 null 檢查還是使用條件式聯合運算子 (`?.`)。

Editorconfig ** 檔案範例︰

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="csharp_style_throw_expression"></a>csharp\_style\_throw_expression

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_throw_expression |
| **規則識別碼** | IDE0016 |
| **適用的語言** | C# 7.0+ |
| **值** | `true` - 偏好使用 `throw` 運算式，而不是 `throw` 陳述式<br /><br />`false` - 偏好使用 `throw` 陳述式，而不是 `throw` 運算式 |
| **Visual Studio 預設值** | `true:suggestion` |

程式碼範例：

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

#### <a name="csharp_style_conditional_delegate_call"></a>csharp\_style\_conditional\_delegate_call

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_conditional_delegate_call |
| **規則識別碼** | IDE0041 |
| **適用的語言** | C# 6.0+  |
| **值** | `true` - 叫用 lambda 運算式時，偏好使用條件式聯合運算子 (`?.`)，而非執行 Null 檢查<br /><br />`false` - 偏好先執行 Null 檢查，再叫用 Lambda 運算式，而非使用條件式聯合運算子 (`?.`) |
| **Visual Studio 預設值** | `true:suggestion` |

程式碼範例：

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

### <a name="code-block-preferences"></a>程式碼區塊喜好設定

這個樣式規則是有關使用大括弧 `{ }` 括住程式碼區塊。

Editorconfig ** 檔案範例︰

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

#### <a name="csharp_prefer_braces"></a>csharp\_prefer\_braces

|屬性|值|
|-|-|
| **規則名稱** | csharp_prefer_braces |
| **規則識別碼** | IDE0011 |
| **適用的語言** | C# |
| **值** | `true` - 偏好使用大括弧，即使只有一行程式碼<br /><br />`false` - 如果可以，偏好不使用大括弧<br /><br />`when_multiline` -在多行上偏好大括弧 |
| **Visual Studio 預設值** | `true:silent` |

程式碼範例：

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

### <a name="unused-value-preferences"></a>未使用的值喜好設定

這些樣式規則涉及未使用的運算式和值指派。

Editorconfig ** 檔案範例︰

```ini
# CSharp code style settings:
[*.cs]
csharp_style_unused_value_expression_statement_preference = discard_variable:silent
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
```

#### <a name="csharp_style_unused_value_expression_statement_preference"></a>csharp_style_unused_value_expression_statement_preference

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_unused_value_expression_statement_preference |
| **規則識別碼** | IDE0058 |
| **適用的語言** | C# |
| **值** | `discard_variable` - 偏好將未使用的運算式指派給 [discard](/dotnet/csharp/discards) <br /><br />`unused_local_variable` - 偏好將未使用的運算式指派給區域變數 |
| **Visual Studio 預設值** | `discard_variable:silent` |

程式碼範例：

```csharp
// Original code:
System.Convert.ToInt32("35");

// After code fix for IDE0058:

// csharp_style_unused_value_expression_statement_preference = discard_variable
_ = System.Convert.ToInt32("35");

// csharp_style_unused_value_expression_statement_preference = unused_local_variable
var unused = Convert.ToInt32("35");
```

#### <a name="csharp_style_unused_value_assignment_preference"></a>csharp_style_unused_value_assignment_preference

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_unused_value_assignment_preference |
| **規則識別碼** | IDE0059 |
| **適用的語言** | C# |
| **值** | `discard_variable` - 指派未使用的值時，偏好使用 [discard](/dotnet/csharp/discards)<br /><br />`unused_local_variable` - 指派未使用的值時，偏好使用區域變數 |
| **Visual Studio 預設值** | `discard_variable:suggestion` |

程式碼範例：

```csharp
// csharp_style_unused_value_assignment_preference = discard_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    _ = wordCount.TryGetValue(searchWord, out var count);
    return count;
}

// csharp_style_unused_value_assignment_preference = unused_local_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    var unused = wordCount.TryGetValue(searchWord, out var count);
    return count;
}
```

### <a name="index-and-range-preferences"></a>索引和範圍喜好設定

這些樣式規則涉及使用 C# 8.0 和更新版本中可用的索引和範圍運算子。

Editorconfig ** 檔案範例︰

```ini
# CSharp code style settings:
[*.cs]
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
```

#### <a name="csharp_style_prefer_index_operator"></a>csharp\_style\_prefer\_index_operator

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_prefer_index_operator |
| **規則識別碼** | IDE0056 |
| **適用的語言** | C# 8.0+ |
| **值** | `true` - 從集合結尾計算索引時，偏好使用 `^` 運算子<br /><br />`false` - 從集合結尾計算索引時，不偏好使用 `^` 運算子 |
| **Visual Studio 預設值** | `true:suggestion` |

程式碼範例：

```csharp
// csharp_style_prefer_index_operator = true
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[^1];

// csharp_style_prefer_index_operator = false
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[names.Length - 1];
```

#### <a name="csharp_style_prefer_range_operator"></a>csharp\_style\_prefer\_range_operator

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_prefer_range_operator |
| **規則識別碼** | IDE0057 |
| **適用的語言** | C# 8.0+ |
| **值** | `true` - 擷取集合的「配量」時，偏好使用範圍運算子 `..`<br /><br />`false` - 擷取集合的「配量」時，不偏好使用範圍運算子 `..` |
| **Visual Studio 預設值** | `true:suggestion` |

程式碼範例：

```csharp
// csharp_style_prefer_range_operator = true
string sentence = "the quick brown fox";
var sub = sentence[0..^4];

// csharp_style_prefer_range_operator = false
string sentence = "the quick brown fox";
var sub = sentence.Substring(0, sentence.Length - 4);
```

### <a name="miscellaneous-preferences"></a>其他喜好設定

本節包含其他樣式規則。

Editorconfig ** 檔案範例︰

```ini
# CSharp code style settings:
[*.cs]
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_using_directive_placement = outside_namespace:silent
csharp_prefer_static_local_function = true:suggestion
csharp_prefer_simple_using_statement = true:suggestion
csharp_style_prefer_switch_expression = true:suggestion
```

#### <a name="csharp_style_deconstructed_variable_declaration"></a>csharp\_style\_deconstructed\_variable_declaration

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_deconstructed_variable_declaration |
| **規則識別碼** | IDE0042 |
| **適用的語言** | C# 7.0+ |
| **值** | `true` - 偏好使用解構的變數宣告<br /><br />`false` - 偏好不使用解構的變數宣告 |
| **Visual Studio 預設值** | `true:suggestion` |

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

#### <a name="csharp_style_pattern_local_over_anonymous_function"></a>csharp\_style\_pattern\_local\_over\_anonymous_function

從 C# 7.0 開始，C# 支援「區域函式」[](/dotnet/csharp/programming-guide/classes-and-structs/local-functions)。 區域函式是另一個成員中巢狀型別的私用方法。

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_pattern_local_over_anonymous_function |
| **規則識別碼** | IDE0039 |
| **適用的語言** | C# 7.0+ |
| **值** | `true` - 偏好使用區域函式而不是匿名函式<br /><br />`false` - 偏好使用匿名函式而不是區域函式 |
| **Visual Studio 預設值** | `true:suggestion` |

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

#### <a name="csharp_using_directive_placement"></a>csharp\_using\_directive_placement

|屬性|值|
|-|-|
| **規則名稱** | csharp_using_directive_placement |
| **規則識別碼** | IDE0065 |
| **適用的語言** | C# |
| **值** | `outside_namespace` - 偏好將 `using` 指示詞放在命名空間外<br /><br />`inside_namespace` - 偏好將 `using` 指示詞放在命名空間內 |
| **Visual Studio 預設值** | `outside_namespace:silent` |

程式碼範例：

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{
    ...
}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
    ...
}
```

#### <a name="csharp_prefer_static_local_function"></a>csharp\_prefer\_static\_local_function

|屬性|值|
|-|-|
| **規則名稱** | csharp_prefer_static_local_function |
| **規則識別碼** | IDE0062 |
| **適用的語言** | C# 8.0+ |
| **值** | `true` - 偏好將區域函式標記為 `static`<br /><br />`false` - 不偏好將區域函式標記為 `static` |
| **Visual Studio 預設值** | `true:suggestion` |

程式碼範例：

```csharp
// csharp_prefer_static_local_function = true
void M()
{
    Hello();
    static void Hello()
    {
        Console.WriteLine("Hello");
    }
}

// csharp_prefer_static_local_function = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

#### <a name="csharp_prefer_simple_using_statement"></a>csharp\_prefer\_simple\_using_statement

|屬性|值|
|-|-|
| **規則名稱** | csharp_prefer_simple_using_statement |
| **規則識別碼** | IDE0063 |
| **適用的語言** | C# 8.0+ |
| **值** | `true` - 偏好使用「簡單的」** `using` 陳述式<br /><br />`false` - 不偏好使用「簡單的」** `using` 陳述式 |
| **Visual Studio 預設值** | `true:suggestion` |

程式碼範例：

```csharp
// csharp_prefer_simple_using_statement = true
using var a = b;

// csharp_prefer_simple_using_statement = false
using (var a = b) { }
```

#### <a name="csharp_style_prefer_switch_expression"></a>csharp\_style\_prefer\_switch_expression

|屬性|值|
|-|-|
| **規則名稱** | csharp_style_prefer_switch_expression |
| **規則識別碼** | IDE0066 |
| **適用的語言** | C# 8.0+ |
| **值** | `true` - 偏好使用 `switch` 運算式 (隨 C# 8.0 引進)<br /><br />`false` - 偏好使用 [switch 陳述式](/dotnet/csharp/language-reference/keywords/switch) |
| **Visual Studio 預設值** | `true:suggestion` |
| **引進的版本** | Visual Studio 2019 16.2 版 |

程式碼範例：

```csharp
// csharp_style_prefer_switch_expression = true
return x switch
{
    1 => 1 * 1,
    2 => 2 * 2,
    _ => 0,
};

// csharp_style_prefer_switch_expression = false
switch (x)
{
    case 1:
        return 1 * 1;
    case 2:
        return 2 * 2;
    default:
        return 0;
}
```

## <a name="see-also"></a>另請參閱

- [格式設定慣例](editorconfig-formatting-conventions.md)
- [命名慣例](editorconfig-naming-conventions.md)
- [EditorConfig 的 .NET 編碼慣例設定](editorconfig-code-style-settings-reference.md)
