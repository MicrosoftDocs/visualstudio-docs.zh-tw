---
title: EditorConfig 檔案的 .NET 命名慣例
ms.date: 08/07/2019
ms.topic: reference
helpviewer_keywords:
- naming conventions [EditorConfig]
- EditorConfig naming conventions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13da6cd34df3996fe837aee89ce4f379027dd409
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72000154"
---
# <a name="net-naming-conventions-for-editorconfig"></a>EditorConfig 的 .NET 命名慣例

命名慣例關係到程式碼項目的命名，例如類別、屬性和方法。 例如，您可以指定公用成員必須以大寫形式命名，或非同步方法必須以 "Async" 結尾。 您可以藉由在 [.editorconfig 檔案](../ide/create-portable-custom-editor-options.md)中指定來強制執行這些規則。 違反命名規則的項目會出現在 [錯誤清單] 或在名稱下方以建議的形式出現，取決於您為規則選擇的嚴重性。 您不需要建置專案，也能看見違規項目。

針對每一個命名慣例，您必須使用以下描述的屬性來指定其適用的符號、命名樣式以及嚴重性，以強制執行慣例。 屬性的順序不重要。

若要開始，請為您將在每個所需要用來完整描述規則的屬性中使用的命名規則選擇一個標題。 例如：`public_members_must_be_capitalized` 是一個良好且具描述性的命名規則名稱。 此頁面將會在下列各節中以 **<namingRuleTitle\>** 來代稱您選擇的標題。

## <a name="symbols"></a>符號

首先，請先識別欲套用命名規則的符號群組。 此屬性具有下列格式：

`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`

以具描述性的標題取代 **<symbolTitle\>** 的值來給予符號群組一個名稱。例如：`public_symbols`。 您將會在三個描述套用規則之符號的屬性名稱使用 **<symbolTitle\>** 的值 (符號的類型、存取層級，以及修飾詞)。

### <a name="kinds-of-symbols"></a>符號的類型

描述要套用命名規則的符號類型。請使用下列格式指定一個屬性：

`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = <values>`

以下清單會顯示允許的值，您可以逗號分隔來指定多個值。

- \*(請使用此值來指定所有符號)
- namespace
- Class - 類別
- struct
- interface
- enum
- 屬性
- 方法
- Field - 欄位
- event
- Delegate - 委派
- 參數 (parameter)
- type_parameter
- 本機
- local_function

### <a name="accessibility-levels-of-symbols"></a>符號的存取層級

描述您欲套用命名規則之符號的存取層級。請使用下列格式來指定一個屬性名稱：

`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = <values>`

以下清單會顯示允許的值，您可以逗號分隔來指定多個值。

- \* (請使用此值來指定所有存取層級)
- public
- internal 或 friend
- private
- protected
- protected\_internal 或 protected_friend
- private\_protected
- 本機

   `local` 存取層級適用於在方法內定義的符號。 當符號的存取性無法在程式碼中定義時，這非常有用。 例如，如果您在常數的命名慣例 (`required_modifiers = const`) 上指定 `applicable_accessibilities = local`，則該規則只套用至在方法內定義的常數，而不套用至在型別中定義的。

   ```csharp
   class TypeName
   {
     // Constant defined in a type.
     const int X = 3;

     void Method()
     {
       // Constant defined in a method with "local" accessibility.
       const int Y = 4;
     }
   }
   ```

### <a name="symbol-modifiers-optional"></a>符號修飾詞 (選擇性)

描述您要套用命名規則之符號的修飾詞。請使用下列格式來指定一個屬性名稱：

`dotnet_naming_symbols.<symbolTitle>.required_modifiers = <values>`

以下清單會顯示允許的值 (以逗號分隔多個值)：

- `abstract` 或 `must_inherit`
- `async`
- `const`
- `readonly`
- `static` 或 `shared`

   > [!NOTE]
   > 如果您有 `static` 或 `shared` 符號的命名規則，則它也套用到 `const` 符號，因為它們是隱含靜態的。 如果您不想要 `static` 命名規則套用到 `const` 符號，請針對 `const` 符號建立個別的命名規則。

命名規則會比對擁有 `required_modifiers` 中指定之「所有」修飾詞的簽章。 如果您省略此屬性時，則會使用空白清單的預設值；換句話說，不需要比對特定修飾詞。 這表示不論是否套用此規則，符號的修飾詞都不會造成影響。

> [!TIP]
> 不要為 `required_modifiers` 指定 `*` 的值。 相反地，只需完全省略 `required_modifiers` 屬性，而您的命名規則將套用至任何種類的修飾詞。

## <a name="style"></a>樣式

您已識別要套用命名規則的符號群組，現在您可以描述命名樣式。 樣式可以是包含特定前置詞或後置詞的名稱，或是名稱中的每個個別文字都以特定的字元分隔。 您也可以指定大寫樣式。 樣式屬性具有下列格式：

`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`

藉由將 **<styleTitle\>** 的值取代為具描述性的標題來給予樣式一個名稱。例如：`first_word_upper_case_style`。 您將會在描述命名樣式 (前置詞、後置詞、文字分隔符號字元，以及大寫) 的屬性名稱中使用 **<styleTitle\>** 的值。 請使用一或多個屬性來描述您的樣式。

### <a name="require-a-prefix"></a>需要前置詞

若要指定符號名稱必須以特定字元起始，請使用此屬性：

`dotnet_naming_style.<styleTitle>.required_prefix = <prefix>`

### <a name="require-a-suffix"></a>需要後置詞

若要指定符號名稱必須以特定字元結束，請使用此屬性：

`dotnet_naming_style.<styleTitle>.required_suffix = <suffix>`

### <a name="require-a-certain-word-separator"></a>需要特定的文字分隔符號

若要指定符號名稱中的每個個別文字都必須以特定的字元分隔，請使用此屬性：

`dotnet_naming_style.<styleTitle>.word_separator = <separator character>`

### <a name="require-a-capitalization-style"></a>需要大寫樣式

若要為符號名稱指定特定的大寫樣式，請使用此屬性：

`dotnet_naming_style.<styleTitle>.capitalization = <value>`

此屬性允許的值為：

- pascal_case
- camel_case
- first\_word_upper
- all\_upper
- all_lower

> [!NOTE]
> 您必須將大寫樣式指定為您命名樣式的一部分，否則您的命名樣式可能會遭到忽略。

## <a name="severity"></a>Severity

若要描述違反您命名規則的嚴重性，請使用下列格式指定一個屬性：

`dotnet_naming_rule.<namingRuleTitle>.severity = <value>`

下表顯示了允許的嚴重性值，以及其代表的意涵：

Severity | 作用
------------ | -------------
none | 規則已完全隱藏。
重構或無訊息 | 未遵循此樣式時，不要向使用者顯示任何內容；但自動產生的程式碼會遵循此樣式。
建議 | 當未遵循此樣式時，向使用者顯示為建議 (在前兩個字元下方以點狀方式呈現)。 它在編譯時期沒有任何作用。
warning | 當未遵循此樣式時，在 [錯誤清單] 中顯示編譯器警告。
error | 當未遵循此樣式時，在 [錯誤清單] 中顯示編譯器錯誤。

> [!NOTE]
> 您不需要建置您的專案，也能看到違反命名規則的項目。 它們會在 [錯誤清單] 中 (或作為建議)，以編輯過後的程式碼方式呈現。

## <a name="rule-order"></a>規則順序

::: moniker range="vs-2017"

在 EditorConfig 檔案中的命名慣例應該以最為明確到最不明確的順序排序。 第一個遇到的可套用規則，會是唯一套用的規則。 但是，如果有多個具有相同名稱的規則*屬性*，則最近找到具有該名稱的屬性優先。 如需詳細資訊，請參閱[檔案階層和優先順序](create-portable-custom-editor-options.md#file-hierarchy-and-precedence)。

::: moniker-end

::: moniker range=">=vs-2019"

從 Visual Studio 2019 16.2 版開始，在 EditorConfig 檔案中定義命名規則的順序並不重要。 相反地，Visual Studio 會根據規則本身的定義自動排序命名規則。 [EditorConfig 語言服務延伸](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig)模組可以分析 EditorConfig 檔案和報表案例，其中檔案中的規則順序與編譯器在執行時間會使用的不同。

如果您使用的是舊版 Visual Studio，則 EditorConfig 檔案中的命名慣例應該以最為明確到最不明確的順序排序。 第一個遇到的可套用規則，會是唯一套用的規則。 但是，如果有多個具有相同名稱的規則*屬性*，則最近找到具有該名稱的屬性優先。 如需詳細資訊，請參閱[檔案階層和優先順序](create-portable-custom-editor-options.md#file-hierarchy-and-precedence)。

::: moniker-end

## <a name="default-naming-styles"></a>預設命名樣式

如果您不指定任何自訂命名規則，Visual Studio 便會使用下列預設樣式：

- 針對具有 `public`、`private`、`internal`、`protected` 或 `protected_internal` 存取範圍的類別、結構、列舉、屬性及事件，預設的命名樣式為 Pascal 命名法。

- 針對具有 `public`、`private`、`internal`、`protected` 或 `protected_internal` 存取範圍的介面，預設的命名樣式為 Pascal 命名法，且必須具有前置詞 **I**。

## <a name="example"></a>範例

下列 .editorconfig 檔案所包含的命名慣例指定公用屬性、方法、欄位、事件及委派必須為大寫。 請注意，此命名慣例指定了多種要套用規則的符號類型，並使用逗號分隔值。

```ini
# Public members must be capitalized (public_members_must_be_capitalized)
[*.{cs,vb}]
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

下列螢幕擷取畫面顯示在編輯器中套用此命名慣例後的效果。 兩個公用變數在沒有將第一個字母以大寫方式呈現的情況下命名。 其中一個是 `const`，另一個則是 `readonly`。 因為命名規則僅適用於 `readonly` 符號，所有只有 `readonly` 變數才會顯示命名規則建議。

![命名規則建議](media/editorconfig-naming-rule-suggestion.png)

現在讓我們將違規嚴重性變更為 `warning`：

```ini
dotnet_naming_rule.public_members_must_be_capitalized.severity = warning
```

如果您關閉並重新開啟程式碼檔案，而不是在名稱違規之下看到建議，您會在錯誤清單中看到綠色波浪線和警告：

![命名規則警告](media/editorconfig-naming-rule-warning.png)

## <a name="see-also"></a>另請參閱

- [語言慣例](editorconfig-language-conventions.md)
- [格式設定慣例](editorconfig-formatting-conventions.md)
- [Roslyn 命名慣例](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63) \(英文\)
- [建立可攜式自訂編輯器選項](../ide/create-portable-custom-editor-options.md)
- [EditorConfig 的 .NET 編碼慣例設定](editorconfig-code-style-settings-reference.md)
