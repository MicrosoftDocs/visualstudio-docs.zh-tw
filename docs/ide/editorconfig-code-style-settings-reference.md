---
title: "EditorConfig 的 .NET 程式碼慣例設定 | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 1
author: kaseyu
ms.author: kaseyu
manager: davidcsa
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 223750aef8d997c6ae017f49ea0a9522bdba72bc
ms.openlocfilehash: c5687a3971d4b670e73e55294e6dfd0c7c3f91d0
ms.contentlocale: zh-tw
ms.lasthandoff: 08/10/2017

---

# <a name="net-coding-convention-settings-for-editorconfig"></a>EditorConfig 的 .NET 程式碼慣例設定
.NET 程式碼慣例是使用 [EditorConfig](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options) 檔案設定。 EditorConfig 檔案可讓您「啟用/停用個別的 .NET 程式碼慣例」並「設定要強制執行慣例的程度」 (透過嚴重性層級)。 若要深入了解使用 EditorConfig 在程式碼基底上強制一致性的方式，請參閱[此文章](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options)。

有三個支援的 .NET 程式碼慣例類別：
- **[語言慣例](#language)**為和 C# 或 Visual Basic 語言相關的規則，例如 `var`/明確類型、使用運算式主體成員。
- **[格式化規則​​](#formatting)**為針對程式碼配置及結構的規則，目的是為了使程式碼更加容易閱讀，例如 Allman 大括號、控制區塊中的間距。
- **[命名慣例](#naming)**為關於物件命名方式的規則，例如 `async` 方法必須以 "Async" 作為結尾。 

# <a name="language"> 語言慣例 </a>
## <a name="overview"></a>概觀
**規則格式：**
`options_name = false|true : none|suggestion|warning|error`

針對程式碼樣式選項，您必須指定 **true** (建議選項) 或 **false** (不建議選項)、冒號 (`:`)，和嚴重性 (`none`、`silent`、`suggestion`、`warning` 或 `error`)。 嚴重性表示要在程式碼基底中為該樣式強制的層級。

`none` 和 `silent` 為同義，並代表不應對使用者顯示任何類型的指示。 這具有停用此規則的效果。

嚴重性 | effect
------------ | -------------
none/silent | 當未遵循此樣式時不要顯示任何項目給使用者，不過程式碼產生功能將會以此樣式產生。 
建議 | 當未遵循此樣式時，向使用者顯示為建議 (前兩個字元上的基礎點)。
warning | 當未遵循此樣式時，顯示編譯器警告。
個錯誤 | 當未遵循此樣式時，顯示編譯器錯誤。

## <a name="net-language-convention-options"></a>.NET 語言慣例選項

- **[.NET 程式碼樣式設定](#this_and_me)**
    - ["This." 和 "Me."限定性條件](#this_and_me)
        - [欄位](#this_and_me_fields)
        - [屬性](#this_and_me_properties)
        - [方法](#this_and_me_methods)
        - [事件](#this_and_me_events)
    - [語言關鍵字 (int、string 等等) 與類型參考的 Framework 類型名稱](#language_keywords)
        - [區域變數、參數和成員](#language_keywords_variables)
        - [成員存取運算式](#language_keywords_member_access)
    - [運算式層級喜好設定](#expression_level)
        - [物件初始設定式](#expression_level_object_initializers)
        - [集合初始設定式](#expression_level_collection_initializers)
        - [明確的 Tuple 名稱](#expression_level_tuple_names)
        - ["null" 檢查中的聯合運算式](#expression_level_null_checking)
        - ["null" 檢查中的 Null 傳播](#expression_level_null_propogation)
- **[CSharp 程式碼樣式設定](#csharp_codestyle)**
    - ["var"](#var)
        - [內建類型的 "var"](#var_built_in)
        - [類型明顯時的 "var"](#var_apparent)
        - [他處的 "var"](#var_elsewhere)
    - [運算式主體成員](#expression_body)
        - [方法](#expression_bodied_members_methods)
        - [建構函式](#expression_bodied_members_constructors)
        - [運算子](#expression_bodied_members_operators)
        - [屬性](#expression_bodied_members_properties)
        - [索引子](#expression_bodied_members_indexers)
        - [存取子](#expression_bodied_members_accessors)
    - [模式比對](#pattern_matching)
        - [具有 "cast" 的 "is" 檢查](#pattern_matching_is_cast)
        - [具有 "null" 的 "as" 檢查](#pattern_matching_as_null)
    - [內嵌變數宣告](#inlined_variable_declarations)
    - [運算式層級喜好設定](#expression_level_csharp) -[簡化 `default` 運算式](#expression_level_default)
    - ["Null" 檢查喜好設定](#null_checking)
        - [Throw 運算式](#null_checking_throw_expressions)
        - [條件式的委派呼叫](#null_checking_conditional_delegate_calls)
    - [程式碼區塊喜好設定](#code_block)
        - [偏好大括弧](#prefer_braces)

## <a name="this_and_me">"This." 和 "Me."限定性條件</a>
### <a name="this_and_me_fields">欄位 (IDE0003/IDE0009)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `dotnet_style_qualification_for_field` | C# 和 Visual Basic | false:none | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 用於非靜態方法中的所有非靜態欄位，偏好在 C# 中開頭加上 `this.`，或在 Visual Basic 中開頭加上 `Me.`。 | **C#:** <br>`this.capacity = 0;` <br><br> **Visual Basic:** <br> `Me.capacity = 0`
| False | 用於非靜態方法中的所有非靜態欄位，偏好在 C# 中開頭不要加上 `this.`，或在 Visual Basic 中開頭不要加上 `Me.`。 | **C#:** <br>`capacity = 0;` <br><br> **Visual Basic:** <br>`capacity = 0`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="this_and_me_properties">屬性 (IDE0003/IDE0009) </a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_qualification_for_property`| C# 和 Visual Basic | false:none | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 用於非靜態方法中的所有非靜態屬性，偏好在 C# 中開頭加上 `this.`，或在 Visual Basic 中開頭加上 `Me.`。| **C#:** <br>`this.ID = 0;` <br><br> **Visual Basic:** <br>`Me.ID = 0`
| False | 用於非靜態方法中的所有非靜態屬性，偏好在 C# 中開頭「不要」加上 `this.`，或在 Visual Basic 中開頭不要加上 `Me.`。 | **C#:** <br>`ID = 0;` <br><br> **Visual Basic:** <br> `ID = 0`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```

### <a name="this_and_me_methods">方法 (IDE0003/IDE0009) </a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_qualification_for_method`| C# 和 Visual Basic | false:none | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 從非靜態方法內呼叫的所有非靜態方法，偏好在 C# 中開頭加上 `this.`，在 VB 中開頭加上 `Me.`。| **C#:** <br>`this.Display();` <br><br> **Visual Basic:** <br> `Me.Display()`
| False | 從非靜態方法內呼叫的所有非靜態方法，偏好在 C# 中開頭「不要」加上 `this.`，在 VB 中開頭不要加上 `Me.`。 | **C#:** <br>`Display();` <br><br> **Visual Basic:** <br> `Display()`


#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="this_and_me_events">事件 (IDE0003/IDE0009) </a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_qualification_for_event`| C# 和 Visual Basic | false:none | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 從非靜態方法內參考的所有非靜態事件，偏好在 C# 中開頭加上 `this.`，在 VB 中開頭加上 `Me.`。| **C#:** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic:** <br> `AddHandler Me.Elapsed, AddressOf Handler`
| False | 從非靜態方法內參考的所有非靜態事件，偏好在 C# 中開頭「不要」加上 `this.`，在 VB 中開頭不要加上 `Me.`。 | **C#:** <br>`Elapsed += Handler;` <br><br> **Visual Basic:** <br>`AddHandler Elapsed, AddressOf Handler`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">語言關鍵字 (int、string 等等) 與類型參考的 Framework 類型名稱</a>
### <a name="language_keywords_variables"> 區域變數、參數和成員 (IDE0012/IDE0014)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_predefined_type_for_locals_parameters_members`| C# 和 Visual Basic | true:none | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 針對區域變數、參數和類型成員，有語言關鍵字表示它們的類型 (`int`、`double`、`float`、`short`、`long`、`decimal`、`string`) 偏好使用關鍵字，而不是類型名稱 (`Int32`、`Int64` 等)。| **C#:** <br>`private int _member;` <br><br> **Visual Basic:**`Private _member As Integer`
| False | 針對區域變數、參數和類型成員，有語言關鍵字表示它們的類型 (`int`、`double`、`float`、`short`、`long`、`decimal`、`string`) 偏好使用類型名稱 (`Int32`、`Int64` 等) 而不是關鍵字。  | **C#:** <br>`private Int32 _member;` <br><br> **Visual Basic:** <br> `Private _member As Int32`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="language_keywords_member_access">成員存取運算式 (IDE0013/IDE0015)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_predefined_type_for_member_access`| C# 和 Visual Basic | true:none | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 每當成員存取運算式用於有關鍵字表示的類型時 (`int`、`double`、`float`、`short`、`long`、`decimal`、`string`)，偏好使用關鍵字。| **C#:** <br>`var local = int.MaxValue;` <br><br> **Visual Basic:** <br> `Dim local = Integer.MaxValue`
| False | 每當成員存取運算式用於有關鍵字表示的類型時 (`int`、`double`、`float`、`short`、`long`、`decimal`、`string`)，偏好使用類型名稱。 | **C#:** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic:** <br> `Dim local = Int32.MaxValue`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="expression_level">運算式層級喜好設定</a>
### <a name="expression_level_object_initializers">物件初始設定式 (IDE0017)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_object_initializer`| C# 和 Visual Basic | true:suggestion | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好盡可能使用物件初始設定式來初始化物件。| **C#:** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic:** <br> `Dim c = New Customer() With { .Age = 21 }`
| False | 偏好「不」使用物件初始設定式來初始化物件。 | **C#:** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic:** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="expression_level_collection_initializers">集合初始設定式 (IDE0028)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_collection_initializer`| C# 和 Visual Basic | true:suggestion | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好盡可能使用集合初始設定式來初始化集合。| **C#:** <br>`var list = new List<int>{ 1, 2, 3 };` <br><br> **Visual Basic:** <br> `Dim list = new List(Of Integer) From { 1, 2, 3}`
| False | 偏好「不」使用集合初始設定式來初始化物件。 | **C#:** <br>`var list = new List<int>();`<br>`list.Add(1);`<br>`list.Add(2);`<br>`list.Add(3);` <br><br> **Visual Basic:** <br>`Dim list = new List(Of Integer)`<br>`list.Add(1)`<br>`list.Add(2)`<br>`list.Add(3)`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_collection_initializer = true:suggestion
```

### <a name="expression_level_tuple_names">明確的 Tuple 名稱 (IDE0033)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_explicit_tuple_names`| C# 7.0+ 和 Visual Basic 15+ | true:suggestion | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好 Tuple 名稱勝過 ItemX 屬性。| **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.name;` <br><br> **Visual Basic:** <br> `Dim customer As (name As String, age As Integer) = GetCustomer()`<br>`Dim name = customer.name`
| False | 偏好 ItemX 屬性勝過 Tuple 名稱。 | **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.Item1;` <br><br> **Visual Basic:** <br>`Dim customer As (name As String, age As Integer) = GetCustomer()`<br> `Dim name = customer.Item1`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_explicit_tuple_names = true:suggestion
``` 

### <a name="expression_level_null_checking">"null" 檢查中的聯合運算式 (IDE0029)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_coalesce_expression`| C# 和 Visual Basic | true:suggestion | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好 null 聯合運算式勝過三元運算子檢查。| **C#:** <br>`var v = x ?? y;` <br><br> **Visual Basic:** <br> `Dim v = If(x, y)`
| False | 偏好三元運算子檢查勝過 null 聯合運算式。 | **C#:** <br>`var v = x != null ? x : y; // or`<br>`var v = x == null ? y : x;` <br><br> **Visual Basic:** <br>`Dim v = If(x Is Nothing, y, x) ' or`<br> `Dim v = If(x IsNot Nothing, x, y)`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_coalesce_expression = true:suggestion
``` 

### <a name="expression_level_null_propogation">"null" 檢查中的 Null 傳播 (IDE0031)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_null_propagation`| C# 6.0+ 和 Visual Basic 14+ | true:suggestion | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好盡可能使用 null 條件運算子。| **C#:** <br>`var v = o?.ToString();` <br><br> **Visual Basic:** <br> `Dim v = o?.ToString()`
| False | 偏好盡可能使用三元 null 檢查。 | **C#:** <br>`var v = o == null ? null : o.ToString(); // or`<br>`var v = o != null ? o.String() : null;` <br><br> **Visual Basic:** <br>`Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or`<br> `Dim v = If(o IsNot Nothing, o.ToString(), Nothing)`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_null_propagation = true:suggestion
``` 

# <a name="csharp_codestyle">CSharp 程式碼樣式設定</a>
## <a name="var">"var" 和明確類型</a>
### <a name="var_built_in">內建類型的 "var" (IDE0007、IDE0008)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_var_for_built_in_types`| C# | true:none | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好針對內建系統類型，例如 `int` 使用 `var`。| **C#:** <br>`var x = 5;`
| False | 偏好不針對內建系統類型，例如 `int` 使用 `var`。 | **C#:** <br>`int x = 5;`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
``` 

### <a name="var_apparent">類型明顯時的 "var" (IDE0007、IDE0008)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_var_when_type_is_apparent`| C# | true:none | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 在宣告運算式右側已提到類型時偏好使用 `var`。| **C#:** <br>`var obj = new C();`
| False | 在宣告運算式右側已提到類型時偏好不使用 `var`。 | **C#:** <br>`C obj = new C();`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp code style settings:
[*.cs]
csharp_style_var_when_type_is_apparent = true:suggestion
``` 

### <a name="var_elsewhere">他處的 "var" (IDE0007、IDE0008) </a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_var_elsewhere`| C# | true:none | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 在所有情況下，除非由另一個程式碼樣式規則覆寫，否則偏好使用 `var`。| **C#:** <br>`var f = this.Init();`
| False | 在所有情況下，除非由另一個程式碼樣式規則覆寫，否則偏好不使用 var。| **C#:** <br>`bool f = this.Init();`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp code style settings:
[*.cs]
csharp_style_var_elsewhere = true:suggestion
``` 

##<a name="expression_bodied_members">運算式主體成員</a>
### <a name="expression_bodied_members_methods">方法 (IDE0022)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_methods`| C# 6.0+ | false:none | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好針對方法使用運算式主體的成員。| **C#:** <br>`public int GetAge() => this.Age;`
| False | 偏好針對方法不使用運算式主體的成員。| **C#:** <br>`public int GetAge() { return this.Age; }`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
``` 

### <a name="expression_bodied_members_constructors">建構函式 (IDE0021)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_constructors`| C# 7.0+ | false:none | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好針對建構函式使用運算式主體的成員。| **C#:** <br>`public Customer(int age) => Age = age;`
| False | 偏好針對建構函式不使用運算式主體的成員。| **C#:** <br>`public Customer(int age) { Age = age; }`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_constructors = false:none
``` 

### <a name="expression_bodied_members_operators">運算子 (IDE0023、IDE0024)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_operators` | C# 7.0+ | false:none | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好針對運算子使用運算式主體的成員。| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`=> new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);`
| False | 偏好針對運算子不使用運算式主體的成員。| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_operators = false:none
``` 

### <a name="expression_bodied_members_properties">屬性 (IDE0025)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_properties` | C# 7.0+ | true:none | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好針對屬性使用運算式主體的成員。| **C#:** <br>`public int Age => _age;`
| False | 偏好針對屬性不使用運算式主體的成員。| **C#:** <br>`public int Age { get { return _age; }}`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_properties = true:none
``` 

### <a name="expression_bodied_members_indexers">索引子 (IDE0026)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_indexers` | C# 7.0+ | true:none | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好針對索引子使用運算式主體的成員。| **C#:** <br>`public T this[int i] => _value[i];`
| False | 偏好針對索引子不使用運算式主體的成員。| **C#:** <br>`public T this[int i] { get { return _values[i]; } }`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_indexers = false:none
``` 

### <a name="expression_bodied_members_accessors">存取子 (IDE0027)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_accessors` | C# 7.0+ | true:none | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好針對存取子使用運算式主體的成員。| **C#:** <br>`public int Age { get => _age; set => _age = value; }`
| False | 偏好針對存取子不使用運算式主體的成員。| **C#:** <br>`public int Age { get { return _age; } set { _age = value; } }`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_accessors = false:none
``` 

## <a name="pattern_matching">模式比對</a>
### <a name="pattern_matching_is_cast">具有 "cast" 的 "is" 檢查 (IDE0020)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_pattern_matching_over_is_with_cast_check` | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好模式比對，而非具有類型轉換的 `is`運算式。| **C#:** <br>`if (o is int i) {...}`
| False | 偏好具有類型轉換的 `is` 運算式，而非模式比對。| **C#:** <br>`if (o is int) {var i = (int)o; ... }`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
```

### <a name="pattern_matching_as_null">具有 "null" 的 "as" 檢查 (IDE0019)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_pattern_matching_over_as_with_null_check` | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好模式比對，而非具有 null 檢查的 `as` 運算式，以判斷是否為特定類型。| **C#:** <br>`if (o is string s) {...}`
| False | 偏好具有 null 檢查的 `as` 運算式，而非模式比對，以判斷是否為特定類型。| **C#:** <br>`var s = o as string; if (s != null) {...}`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

### <a name="inlined_variable_declarations">內嵌變數宣告 (IDE0018)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_inlined_variable_declaration` | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好盡可能內嵌宣告 `out` 變數。 | **C#:** <br>`if (int.TryParse(value, out int i) {...}`
| False | 偏好明確宣告 `out` 變數。| **C#:** <br>`int i; if (int.TryParse(value, out i) {...}`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```
## <a name="expression_level_csharp">運算式層級喜好設定</a>
### <a name="expression_level_default">簡化 `default` 運算式 (IDE0034) </a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_prefer_simple_default_expression` | C# 7.1+ | true:suggestion | Visual Studio 2017 v. 15.3 |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好 `default` 而非 `default(T)` | **C#:** <br>`void DoWork(CancellationToken cancellationToken = default){ ... }`
| False | 偏好。 | **C#:** <br>`void DoWork(CancellationToken cancellationToken = default(CancellationToken)){ ... }`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
``` 

## <a name="null_checking">"Null" 檢查喜好設定</a>
### <a name="null_checking_throw_expressions">Throw 運算式 (IDE0016)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_throw_expression`  | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好使用 throw 運算式，而不是 throw 陳述式。 | **C#:** <br>`this.s = ss ?? throw new ArgumentNullException(nameof(s));`
| False | 偏好使用 throw 陳述式，而不是 throw 運算式。| **C#:** <br>`if (s==null) {throw new ArgumentNullException(nameof(s));} this.s = s;`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
```

### <a name="null_checking_conditional_delegate_calls">偏好條件式委派呼叫 (IDE0041)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_conditional_delegate_call`  | C# 6.0+ | true:suggestion | Visual Studio 2017 RTW |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 叫用 lambda 時偏好使用條件式聯合運算 (`?.`) 而不是執行 null 檢查。 | **C#:** <br>`func?.Invoke(args);`
| False | 偏好先執行 null 檢查，再叫用 Lambda，而不使用條件式聯合運算子 (`?.`)。| **C#:** <br>`if (func!=null) { func(args); }`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp code style settings:
[*.cs]
csharp_style_conditional_delegate_call = false:suggestion
```

## <a name="code_block">程式碼區塊喜好設定</a>
### <a name="prefer_braces">偏好大括弧 (IDE0011)</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_prefer_braces`  | C#  | true:none | Visual Studio 2017 v. 15.3 |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好大括弧 | **C#:** <br>`if (test) { this.Display(); }`
| False | 偏好盡可能不使用大括弧 | **C#:** <br>`if (test) this.Display();`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:none
```

# <a name="formatting"> 格式化規則 </a>
## <a name="overview"></a>概觀
**規則格式：**
`options_name = false|true`

針對格式化選項，您必須指定 **true** (建議選項) 或 **false** (不建議選項)。但是在某些例外情況下，您必須改為指定想要套用規則的條件。

## <a name="net-formatting-options"></a>.NET 格式化選項

- **[.NET 格式化設定](#usings)**
    - [組合管理 Using](#usings)
        - [優先對 System 指示詞進行排序](#usings_sort_system_first)
- **[C# 格式化設定](#newline)**
    - [新行字元選項](#newline)
        - [於左大括號 (`{`) 之前加入新行字元](#newline_before_brace)
        - [於 `else` 之前加入新行字元](#newline_before_else)
        - [於 `catch` 之前加入新行字元](#newline_before_catch)
        - [於 `finally` 之前加入新行字元](#newline_before_finally)
        - [於物件初始設定式中的成員之前加入新行字元](#newline_before_object)
        - [於匿名類型中的成員之前加入新行字元](#newline_before_anonymous)
        - [於查詢運算式子句中的成員之前加入新行字元](#newline_before_query)
    - [縮排選項](#indent)
        - [對 `switch` 案例內容進行縮排](#indent_switch)
        - [縮排 `switch` 標籤](#indent_switch_labels)
        - [標籤位置](#label)
    - [間距選項](#spacing)
        - [於轉換之後加入空格](#space_after_cast)
        - [於控制流程陳述式中的關鍵字之後加入空格](#space_control_flow)
        - [於方法宣告參數清單括號之間加入空格](#space_parameter_list)
        - [於方法呼叫引數清單的括號之內加入空格](#space_method_call)
        - [於其他選項的括號之內加入空格](#space_other)
    - [換行選項](#wrapping)
        - [將陳述式和成員宣告保留在同一行上](#wrapping_statement)
        - [將區塊保留在單行上](#wrapping_block)

## <a name="usings">組合管理 Using</a>
### <a name="usings_sort_system_first">優先對 System 指示詞進行排序</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_sort_system_directives_first`  |  C# 和 Visual Basic | true | Visual Studio 2017 v. 15.3  |


| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 依字母順序對 System.* Using 進行排序，並將它們置於其他 Using 之前。| **C#:** <br>`using System.Collections.Generic;`<br> `using System.Threading.Tasks;`<br> `using Octokit;`
| False | 針對 Using 的排序沒有任何需求 | **C#:** <br>`using System.Collections.Generic;`<br> `using Octokit;` <br> `using System.Threading.Tasks;`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# .NET formatting settings:
[*.cs, *.vb]
dotnet_sort_system_directives_first = true
``` 

# <a name="csharp_formatting">C# 格式化設定</a>
## <a name="newline">新行字元選項</a>
### <a name="newline_before_brace"> 於左大括號 (`{`) 之前加入新行字元</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_new_line_before_open_brace`  |  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 說明 
| ------------- |:-------------|
| accessors、anonymous_methods、anonymous_types、control_blocks、events、indexers、lambdas、local_functions、methods、object_collection、properties、types。 (請以 ',' 分隔多個項目)。 | 針對指定運算式要求大括號位於新行上 (Allman 樣式) |
| 全部 | 針對所有運算式要求大括號位於新行上 (Allman) |
| 無 | 針對所有運算式要求大括號位於同一行上 (K&R) |

#### <a name="applied"></a>已套用：
```csharp
// csharp_new_line_before_open_brace = all
void MyMethod() 
{
    if (...) 
    {
        ...
    }
}
```

```csharp
// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
``` 

### <a name="newline_before_else"> 於 `else` 之前加入新行字元</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_new_line_before_else` |  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 說明 
| ------------- |:-------------|
| True | 將 `else` 陳述式置於新行上。  |
| False | 將 `else` 陳述式置於同一行上。  |

#### <a name="applied"></a>已套用：
```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}
```

```csharp
// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_else = true
``` 

### <a name="newline_before_catch"> 於 `catch` 之前加入新行字元</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_catch`|  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 說明 
| ------------- |:-------------|
| True | 將 `catch` 陳述式置於新行上。  |
| False | 將 `catch` 陳述式置於同一行上。 |

#### <a name="applied"></a>已套用：
```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}
```

```csharp
// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_catch = true
``` 

### <a name="newline_before_finally"> 於 `finally` 之前加入新行字元</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_finally`|  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 說明 
| ------------- |:-------------|
| True | 要求 `finally` 陳述式位於右大括號之後的新行上。  |
| False | 要求 `finally` 陳述式位於右大括號的同一行上。  |

#### <a name="applied"></a>已套用：
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
```

```csharp
// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_finally = true
``` 

### <a name="newline_before_object"> 於物件初始設定式中的成員之前加入新行字元</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_members_in_object_initializers`|  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 說明 
| ------------- |:-------------|
| True | 要求物件初始設定式的成員位於不同行上。  |
| False | 要求物件初始設定式的成員位於同一行上。  |

#### <a name="applied"></a>已套用：
```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_object_initializers = true
``` 

### <a name="newline_before_anonymous"> 於匿名類型中的成員之前加入新行字元</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_members_in_anonymous_types` |  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 說明 
| ------------- |:-------------|
| True | 要求匿名類型的成員位於不同行上。  |
| False | 要求匿名類型的成員位於同一行上。  |

#### <a name="applied"></a>已套用：
```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_anonymous_types = true
``` 

### <a name="newline_before_query"> 於查詢運算式子句中的成員之前加入新行字元</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_new_line_within_query_expression_clauses`  |  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 說明 
| ------------- |:-------------|
| True | 要求查詢運算式子句的元素位於不同行上。  |
| False | 要求查詢運算式子句的元素位於同一行上。  |

#### <a name="applied"></a>已套用：
```csharp
// csharp_new_line_within_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;
```

```csharp
// csharp_new_line_within_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_within_query_expression_clauses = true
``` 

## <a name="indent">縮排選項</a>
### <a name="indent_switch"> 對 `switch` 案例內容進行縮排</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_indent_case_contents`  |  C#  | true | Visual Studio 2017 v. 15.3  |

| 值 | 說明 
| ------------- |:-------------|
| True | 對 `switch` 案例內容進行縮排  |
| False | 不對 `switch` 案例內容進行縮排 |

#### <a name="applied"></a>已套用：
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
```

```csharp
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

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
``` 

### <a name="indent_switch_labels"> 縮排 `switch` 標籤 </a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_indent_switch_labels`  |  C#  | true | Visual Studio 2017 v. 15.3  |

| 值 | 說明 
| ------------- |:-------------|
| True | 縮排 `switch` 標籤  |
| False | 不要縮排 `switch` 標籤 |

#### <a name="applied"></a>已套用：
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
```

```csharp
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

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_indent_switch_labels = true
``` 

### <a name="label">標籤位置</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_indent_labels`  |  C#  | one_less | Visual Studio 2017 v. 15.3  |


| 值 | 說明 
| ------------- |:-------------|
| one_less | 將標籤置於比目前內容的縮排少一個單位的位置 |
| no_change | 將標籤置於和目前內容相同縮排的位置 |

#### <a name="applied"></a>已套用：
```csharp
// csharp_indent_labels = one_less
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
error:
    throw new Exception(...);
}

```

```csharp
// csharp_indent_labels= no_change
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
    error:
    throw new Exception(...);
}
```

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_indent_labels = one_less
``` 

## <a name="spacing">間距選項</a>
### <a name="space_after_cast"> 於轉換之後加入空格 </a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_space_after_cast` |  C#  | false | Visual Studio 2017 v. 15.3  |


| 值 | 描述 | 已套用 |
| ------------- |:-------------|:-------------|
| True | 要求在轉換和值之間加入空格  | **C#:** <br>`int y = (int) x;`
| False | 在轉換和值之間不需要加入空格 | **C#:** <br>`int y = (int)x;`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
``` 

### <a name="space_control_flow"> 於控制流程陳述式中的關鍵字之後加入空格 </a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_space_after_keywords_in_control_flow_statements` |  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 描述 | 已套用 |
| ------------- |:-------------|:-------------|
| True | 要求在關鍵字之後加入空格 | **C#:** <br>`for (int i;i<x;i++) { ... }`
| False | 在關鍵字之後不需要加入空格 | **C#:** <br>`for(int i;i<x;i++) { ... }`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_keywords_in_control_flow_statements = true
``` 

### <a name="space_parameter_list"> 於方法宣告引數清單括號之間加入空格 </a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_space_between_method_declaration_parameter_list_parentheses` |  C#  | false | Visual Studio 2017 v. 15.3  |


| 值 | 描述 | 已套用 |
| ------------- |:-------------|:-------------|
| True | 要求在關鍵字之後加入空格 | **C#:** <br>`void Bark( int x ) { ... }`
| False | 在關鍵字之後不需要加入空格 | **C#:** <br>`void Bark(int x) { ... }`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_declaration_parameter_list_parentheses = true
```

### <a name="space_method_call"> 於方法呼叫引數清單的括號之內加入空格</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `csharp_space_between_method_call_parameter_list_parentheses` |  C#  | false | Visual Studio 2017 v. 15.3  |


| 值 | 描述 | 已套用 |
| ------------- |:-------------|:-------------|
| true | 在控制流程陳述式的括號之間加入空格 | **C#:** <br>`MyMethod( argument );`
| false | 在運算式的括號之間加入空格 | **C#:** <br>`MyMethod(argument);`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_call_parameter_list_parentheses = control_flow_statements, type_casts
```  

### <a name="space_other"> 於其他選項的括號之內加入空格 </a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `csharp_space_between_parentheses`  |  C#  | false | Visual Studio 2017 v. 15.3  |


| 值 | 描述 | 已套用 |
| ------------- |:-------------|:-------------|
| control_flow_statements | 在控制流程陳述式的括號之間加入空格 | **C#:** <br>`for( int i;i<x;i++ ) { ... }`
| 運算式 | 在運算式的括號之間加入空格 | **C#:** <br>`var z = ( x * y ) - ( ( y - x ) * 3);`
| type_casts | 在類型轉換中的括號之間加入空格 | **C#:**<br>`int y = ( int )x;`

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_parentheses = control_flow_statements, type_casts
``` 

## <a name="wrapping">換行選項</a>
### <a name="wrapping_statement">將陳述式和成員宣告保留在同一行上</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `csharp_preserve_single_line_statements`   |  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 說明 |
| ------------- |:-------------|
| True | 將陳述式和成員宣告保留在同一行上  | 
| False | 將陳述式和成員宣告保留在不同的行上 | 

#### <a name="applied"></a>已套用
```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";
```

```csharp
//csharp_preserve_single_line_statements = false
int i = 0; 
string name = "John";
```

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
``` 

### <a name="wrapping_block">將區塊保留在單行上</a>
| **選項名稱** | **適用的語言** | **Visual Studio 預設** | **支援的版本** |
| ----------- | -------------------- | ----------------------| ----------------  |
|   `csharp_preserve_single_line_blocks`    |  C#  | true | Visual Studio 2017 v. 15.3  |


| 值 | 說明 |
| ------------- |:-------------|
| True | 將區塊保留在單行上 | 
| False | 將區塊保留在不同的行上 | 

#### <a name="applied"></a>已套用
```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }
```

```csharp
//csharp_preserve_single_line_blocks = false
public int MyProperty
{ 
    get; set;
}
```

#### <a name="example-editorconfig-file"></a>Editorconfig 檔案範例︰
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_blocks = true
``` 

# <a name="naming"> 命名慣例 </a>
## <a name="overview"></a>概觀
**規則格式：**<br>
namingRuleTitle：<br>
`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.severity = none|suggestion|warning|error`<br>
<br>
symbolTitle：<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = class, struct, interface, enum, property, method, field, event, namespace, delegate, type_parameter`<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = public, internal, private, protected, protected_internal`<br>
`dotnet_naming_symbols.<symbolTitle>.required_modifiers = abstract, async, const, readonly, static`<br>
<br>
styleTitle：<br>
`dotnet_naming_style.<styleTitle>.capitalization = pascal_case|camel_case|first_word_upper|all_upper|all_lower`<br>
`dotnet_naming_style.<styleTitle>.required_prefix = string`<br>
`dotnet_naming_style.<styleTitle>.required_suffix = string`<br>
`dotnet_naming_style.<styleTitle>.word_separator = string`<br>

## <a name="writing-a-naming-convention"></a>撰寫命名慣例
針對命名慣例，您必須指定「符號」、「樣式」和「嚴重性」。 命名慣例應該以最為明確到最不明確的順序排序。 根據該順序所遇到的第一個適用的規則，將會是系統唯一套用的規則。 

### <a name="severity"></a>嚴重性
下列為命名樣式規則嚴重性的有效選項：`none`、`silent`、`suggestion`、`warning`、`error`。

 `none` 和 `silent` 為同義，並代表不應對使用者顯示任何類型的指示。 這具有停用此規則的效果。

 `suggestion` 代表系統會在錯誤清單及 IDE 中向使用者顯示下列項目。 `suggestion` 嚴重性將會允許命名規則執行，但它將不會造成組建中斷。

嚴重性 | effect
------------ | -------------
none/silent | 當未遵循此樣式時不要顯示任何項目給使用者，不過程式碼產生功能將會以此樣式產生。 
建議 | 當未遵循此樣式時，向使用者顯示為建議 (前兩個字元上的基礎點)。
warning | 當未遵循此樣式時，顯示編譯器警告。
個錯誤 | 當未遵循此樣式時，顯示編譯器錯誤。

### <a name="symbol-specification"></a>符號規格
識別應套用命名規則的「符號」、「修飾詞」及「協助工具層級」。

|  選項名稱 | `dotnet_naming_rule.<namingRuleTitle>.symbols` |
| ------------- |:-------------:|
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_kinds`
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities`
|  | `dotnet_naming_symbols.<symbolTitle>.required_modifiers`

| 符號 | 協助工具選項 | 修飾詞
| ------------- |------------- |------------- |
| `*` | `*` |  `abstract` | 
| `class` | `public` |  `must_inherit` | `async` | 
| `struct` | `internal` (C#) /  | `const` | 
| `interface` | `friend` (Visual Basic) | `readonly` | 
| `enum` | `private`  | `static` | 
| `property` | `protected` | `shared` |
| `method` |`protected_internal` (C#) | |
| `field` | `protected_friend` (Visual Basic) | |
| `event` | | |
| `delegate` | | |


### <a name="style-specification"></a>樣式規格
識別要套用至符號的命名樣式。

|  選項名稱 | `dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>` |
| ------------- |:-------------:|
|  | `dotnet_naming_style.<styleTitle>.capitalization`|
|  | `dotnet_naming_style.<styleTitle>.required_prefix`|
|  | `dotnet_naming_style.<styleTitle>.required_suffix`|
|  | `dotnet_naming_style.<styleTitle>.word_separator`|


| 樣式 | 說明 |
| ------------- |:-------------:|
| 前置詞 | 必須出現在識別項之前的必要字元。 |
| 尾碼 | 必須出現在識別項之後的必要字元。 |
| 文字分隔符號 | 要求在識別項中的文字之間加入分隔符號。 |
| 大小寫 |`pascal_case`, `camel_case`, `first_word_upper`, `all_upper`, `all_lower` | 


### <a name="example-naming-convention"></a>範例命名慣例
```
# CSharp formatting settings:
[*.cs]
dotnet_naming_rule.async_methods_end_in_async.symbols  = any_async_methods
dotnet_naming_rule.async_methods_end_in_async.style    = end_in_async
dotnet_naming_rule.async_methods_end_in_async.severity = suggestion

dotnet_naming_symbols.any_async_methods.applicable_kinds           = method
dotnet_naming_symbols.any_async_methods.applicable_accessibilities = *
dotnet_naming_symbols.any_async_methods.required_modifiers         = async

dotnet_naming_style.end_in_async.required_suffix = Async
dotnet_naming_style.end_in_async.capitalization  = pascal_case
``` 

