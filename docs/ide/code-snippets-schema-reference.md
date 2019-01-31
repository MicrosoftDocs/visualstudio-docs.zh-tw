---
title: 程式碼片段結構描述參考
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- schema reference [Visual Studio]
- snippets [Visual Studio], schema reference
- code snippets [Visual Studio], schema reference
- IntelliSense Code Snippets, XML Schema
ms.assetid: 58a60621-725f-4763-93b7-62ea5424ef88
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8e0f253dbd1f97bc2b485b2e18dd6a5d40db1c2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002030"
---
# <a name="code-snippets-schema-reference"></a>程式碼片段結構描述參考

IntelliSense 程式碼片段是預先設計的程式碼片段，可用以插入使用 Visual Studio 的應用程式。 您可以提供程式碼片段來縮短輸入重複程式碼或搜尋範例所花費的時間，藉此提高產能。 您可以使用 IntelliSense 程式碼片段 XML 結構描述建立自己的程式碼片段，並新增至 Visual Studio 已包含的程式碼片段中。

## <a name="assembly-element"></a>Assembly 元素

指定程式碼片段所參考的組件名稱。

**Assembly** 項目的文字值有兩種，即組件的易記文字名稱，例如 `System.dll`，或是組件的強式名稱，例如 `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`。

```xml
<Assembly>
    AssemblyName
</Assembly>
```

|父項目|說明|
| - |-----------------|
|[Reference 項目](../ide/code-snippets-schema-reference.md#reference-element)|包含有關程式碼片段所需之組件參考的資訊。|

 需要文字值。 此文字會指定程式碼片段參考的組件。

## <a name="author-element"></a>Author 元素

指定程式碼片段作者名稱。 [程式碼片段管理員] 會顯示儲存在程式碼片段 `Author` 項目中的名稱。

```xml
<Author>
   Code Snippet Author
</Author>
```

|父項目|說明|
| - |-----------------|
|[Header 項目](../ide/code-snippets-schema-reference.md#header-element)|包含有關該程式碼片段的一般資訊。|

 需要文字值。 此文字會指定程式碼片段的作者。

## <a name="code-element"></a>程式碼項目

提供簡短程式碼區塊的容器。

### <a name="keywords"></a>關鍵字

`Code` 項目的文字可以使用兩個保留字：`$end$` 和 `$selected$`。 `$end$` 會標記程式碼片段插入後，放置游標的位置。 `$selected$` 表示在文件中選取的文字，該文字會在叫用時插入程式碼片段中。 例如，假設程式碼片段包含：

```
$selected$ is a great color.
```

如果使用者叫用範本時選取的文字是 "Blue"，結果為：

```
Blue is a great color.
```

您不可以在程式碼片段中多次使用 `$end$` 或 `$selected$`。 如果這麼做，系統只會辨認第二個執行個體。 假設程式碼片段包含：

```
$selected$ is a great color. I love $selected$.
```

如果選取的文字是 "Blue"，結果為：

```
 is a great color. I love Blue.
```

由於 `$selected$` 和 `is` 之間有一個空格，因此開頭會出現空格。

所有其他 `$` 關鍵字都會在 `<Literal>` 和 `<Object>` 標記中動態定義。

以下是程式碼項目的結構：

```xml
<Code Language="Language"
    Kind="method body/method decl/type decl/page/file/any"
    Delimiter="Delimiter">
    Code to insert
</Code>
```

需要文字值。 此文字會指定程式碼以及常值和物件，讓您可以在將此程式碼片段插入程式碼檔時使用。

### <a name="attributes"></a>屬性

程式碼項目有三個屬性可用：

- **Language** - _Required_ 屬性，指定程式碼片段的語言。 值可以是下列其中一項：

   |值|說明|
   |-----|-----------|
   |`VB`|識別 Visual Basic 程式碼片段。|
   |`CSharp`|識別 C# 程式碼片段。|
   |`CPP`|識別 C++ 程式碼片段。|
   |`XML`|識別 XML 程式碼片段。|
   |`JavaScript`|識別 JavaScript 程式碼片段。|
   |`SQL`|識別 SQL 程式碼片段。|
   |`HTML`|識別 HTML 程式碼片段。|

- **Kind** - _Optional_ 屬性，指定程式碼片段包含的程式碼種類，以及程式碼片段必須插入以供編譯的位置。 值可以是下列其中一項：

   |值|說明|
   |-----|-----------|
   |`method body`|指定程式碼片段為方法主體，因此必須在方法宣告中插入。|
   |`method decl`|指定程式碼片段為方法，因此必須在類別或模組中插入。|
   |`type decl`|指定程式碼片段為類型，因此必須在類別、模組或命名空間中插入。|
   |`file`|指定程式碼片段為完整的程式碼檔。 這些程式碼片段可以單獨插入程式碼檔中或命名空間內。|
   |`any`|指定程式碼片段可以插入任何位置。 這個標記可用於與內容無關的程式碼片段，例如註解。|

- **Delimiter** - _Optional_ 屬性，指定在程式碼中用來描述常值和物件的分隔符號。 根據預設，分隔符號為 `$`。

### <a name="parent-element"></a>父項目

|父項目|說明|
| - |-----------------|
|[Snippet 項目](../ide/code-snippets-schema-reference.md#snippet-element)|包含程式碼片段的參考、匯入、宣告和程式碼。|

## <a name="codesnippet-element"></a>CodeSnippet 元素

讓您指定可插入 Visual Studio 程式碼檔中的標題和多個 IntelliSense 程式碼片段。

```xml
<CodeSnippet Format="x.x.x">
    <Header>... </Header>
    <Snippet>... </Snippet>
</CodeSnippet>
```

|屬性|說明|
|---------------|-----------------|
|`Format`|必要屬性。 指定程式碼片段的結構描述版本。 Format 屬性必須是語法為 x.x.x 的字串，其中每個 "x" 代表版本號碼的一個數值。 Visual Studio 會忽略具有它所不了解之 `Format` 屬性的程式碼片段。|

|子項目|說明|
|-------------------|-----------------|
|[Header 項目](../ide/code-snippets-schema-reference.md#header-element)|必要項目。 包含有關該程式碼片段的一般資訊。 程式碼片段中只能有一個 `Header` 項目。|
|[Snippet 項目](../ide/code-snippets-schema-reference.md#snippet-element)|必要項目。 包含 Visual Studio 將插入的程式碼。 程式碼片段中只能有一個 `Snippet` 項目。|

|父項目|說明|
| - |-----------------|
|[CodeSnippets 項目](../ide/code-snippets-schema-reference.md#codesnippets-element)|程式碼片段 XML 結構描述的根項目。|

## <a name="codesnippets-element"></a>CodeSnippets 元素

將 [CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element) 項目設為群組。 `CodeSnippets` 項目是程式碼片段 XML 結構描述的根項目。

```xml
<CodeSnippets>
    <CodeSnippet>... </CodeSnippet>
</CodeSnippets>
```

|子項目|說明|
|-------------------|-----------------|
|[CodeSnippet 項目](../ide/code-snippets-schema-reference.md#codesnippet-element)|選擇性項目。 所有程式碼片段資料的父項目。 `CodeSnippet` 項目中可能有零個或多個 `CodeSnippets` 項目。|

## <a name="declarations-element"></a>Declarations 元素

指定構成您可以編輯的程式碼片段部分的常值和物件。

```xml
<Declarations>
    <Literal>... </Literal>
    <Object>... </Object>
</Declarations>
```

|子項目|說明|
|-------------------|-----------------|
|[Literal 項目](../ide/code-snippets-schema-reference.md#literal-element)|選擇性項目。 定義您可以編輯的程式碼片段常值。 `Literal` 項目中可能有零個或多個 `Declarations` 項目。|
|[Object 項目](../ide/code-snippets-schema-reference.md#object-element)|選擇性項目。 定義您可以編輯的程式碼片段物件。 `Object` 項目中可能有零個或多個 `Declarations` 項目。|

|父項目|說明|
| - |-----------------|
|[Snippet 項目](../ide/code-snippets-schema-reference.md#snippet-element)|包含程式碼片段的參考、匯入、宣告和程式碼。|

## <a name="default-element"></a>Default 元素

指定 IntelliSense 程式碼片段中常值或物件的預設值。

```xml
<Default>
    Default value
</Default>
```

|父項目|說明|
| - |-----------------|
|[Literal 項目](../ide/code-snippets-schema-reference.md#literal-element)|定義您可以編輯之程式碼片段的常值欄位。|
|[Object 項目](../ide/code-snippets-schema-reference.md#object-element)|定義您可以編輯之程式碼片段的物件欄位。|

 需要文字值。 這項文字是指定填入您可以編輯的程式碼片段中，各欄位的常值或物件的預設值。

## <a name="description-element"></a>Description 元素

指定有關 IntelliSense 程式碼片段內容的描述性資訊。

```xml
<Description>
    Code Snippet Description
</Description>
```

|父項目|說明|
| - |-----------------|
|[Header 項目](../ide/code-snippets-schema-reference.md#header-element)|包含有關該程式碼片段的一般資訊。|

 需要文字值。 此文字描述程式碼片段。

## <a name="function-element"></a>Function 項目

指定常值或物件在 Visual Studio 中得到焦點時要執行的函式。

> [!NOTE]
> 只有 C# 程式碼片段支援 `Function` 元素。

```xml
<Function>
    FunctionName
</Function>
```

|父項目|說明|
| - |-----------------|
|[Literal 項目](../ide/code-snippets-schema-reference.md#literal-element)|定義您可以編輯之程式碼片段的常值欄位。|
|[Object 項目](../ide/code-snippets-schema-reference.md#object-element)|定義您可以編輯之程式碼片段的物件欄位。|

 需要文字值。 此文字指定常值或物件欄位在 Visual Studio 中得到焦點時要執行的函式。

## <a name="header-element"></a>Header 元素

指定有關 IntelliSense 程式碼片段的一般資訊。

```xml
<Header>
    <Title>... </Title>
    <Author>... </Author>
    <Description>... </Description>
    <HelpUrl>... </HelpUrl>
    <SnippetTypes>... </SnippetTypes>
    <Keywords>... </Keywords>
    <Shortcut>... </Shortcut>
</Header>
```

|子項目|說明|
|-------------------|-----------------|
|[Author 項目](../ide/code-snippets-schema-reference.md#author-element)|選擇性項目。 程式碼片段作者的人員或公司名稱。 `Author` 項目中可能有零個或一個 `Header` 項目。|
|[Description 項目](../ide/code-snippets-schema-reference.md#description-element)|選擇性項目。 程式碼片段的描述。 `Description` 項目中可能有零個或一個 `Header` 項目。|
|[HelpUrl 項目](../ide/code-snippets-schema-reference.md#helpurl-element)|選擇性項目。 包含程式碼片段詳細資訊的 URL。 Header 項目中可能有零個或一個 `HelpURL` 項目。 **注意：** Visual Studio 不會使用 `HelpUrl` 元素。 此項目是 IntelliSense 程式碼片段 XML 結構描述的一部分，任何包含此項目的程式碼片段都會生效，但是不會使用此項目的值。|
|[Keywords 項目](../ide/code-snippets-schema-reference.md#keywords-element)|選擇性項目。 將 `Keyword` 項目設為群組。 `Keywords` 項目中可能有零個或一個 `Header` 項目。|
|[Shortcut 項目](../ide/code-snippets-schema-reference.md#shortcut-element)|選擇性項目。 指定可用來插入程式碼片段的捷徑文字。 `Shortcut` 項目中可能有零個或一個 `Header` 項目。|
|[SnippetTypes 項目](../ide/code-snippets-schema-reference.md#snippettypes-element)|選擇性項目。 將 `SnippetType` 項目設為群組。 `SnippetTypes` 項目中可能有零個或一個 `Header` 項目。 如果沒有 `SnippetTypes` 項目，程式碼片段永遠有效。|
|[Title 項目](../ide/code-snippets-schema-reference.md#title-element)|必要項目。 程式碼片段的易記名稱。 `Title` 項目中只能有一個 `Header` 項目。|

|父項目|說明|
| - |-----------------|
|[CodeSnippet 項目](../ide/code-snippets-schema-reference.md#codesnippet-element)|所有程式碼片段資料的父項目。|

## <a name="helpurl-element"></a>HelpUrl 元素

指定提供程式碼片段詳細資訊的 URL。

> [!NOTE]
> Visual Studio 不會使用 `HelpUrl` 元素。 此項目是 IntelliSense 程式碼片段 XML 結構描述的一部分，任何包含此項目的程式碼片段都會生效，但是不會使用此項目的值。

```xml
<HelpUrl>
    www.microsoft.com
</HelpUrl>
```

|父項目|說明|
| - |-----------------|
|[Header 項目](../ide/code-snippets-schema-reference.md#header-element)|包含有關該程式碼片段的一般資訊。|

可選擇使用文字值。 此文字指定可瀏覽程式碼片段詳細資訊的 URL。

## <a name="id-element"></a>ID 元素

指定 `Literal` 或 `Object` 項目的唯一識別項。 相同程式碼片段中兩個常值或物件的 `ID` 項目中不能有相同的文字值。 常值和物件不能包含值為 end 的 `ID` 項目。 已保留 `$end$` 值，並且在插入程式碼片段以後，用來標示放置游標的位置。

```xml
<ID>
    Unique Identifier
</ID>
```

|父項目|說明|
| - |-----------------|
|[Literal 項目](../ide/code-snippets-schema-reference.md#literal-element)|定義您可以編輯之程式碼片段的常值欄位。|
|[Object 項目](../ide/code-snippets-schema-reference.md#object-element)|定義您可以編輯之程式碼片段的物件欄位。|

需要文字值。 此文字會指定物件或常值的唯一識別項。

## <a name="import-element"></a>Import 元素

指定 IntelliSense 程式碼片段使用的匯入命名空間。

> [!NOTE]
> 只有 Visual Basic 專案支援 `Import` 項目。

```xml
<Import>
    <Namespace>... </Namespace>
</Import>
```

|子項目|說明|
|-------------------|-----------------|
|[Namespace 項目](../ide/code-snippets-schema-reference.md#namespace-element)|必要項目。 指定程式碼片段所使用的命名空間。 `Namespace` 項目中只能有一個 `Import` 項目。|

|父項目|說明|
| - |-----------------|
|[Imports 項目](../ide/code-snippets-schema-reference.md#imports-element)|將 **Import** 項目的項目設為群組。|

## <a name="imports-element"></a>Imports 元素

將個別 `Import` 項目設為群組。

> [!NOTE]
> 只有 Visual Basic 專案支援 `Imports` 項目。

```xml
<Imports>
    <Import>... </Import>
</Imports>
```

|子項目|說明|
|-------------------|-----------------|
|[Import 項目](../ide/code-snippets-schema-reference.md#import-element)|選擇性項目。 包含程式碼片段的已匯入命名空間。 `Imports` 項目中可能有零或多個 **Import** 項目。|

|父項目|說明|
| - |-----------------|
|[Snippet 項目](../ide/code-snippets-schema-reference.md#snippet-element)|包含程式碼片段的參考、匯入、宣告和程式碼。|

## <a name="keyword-element"></a>Keyword 元素

指定程式碼片段的自訂關鍵字。 這些程式碼片段關鍵字是由 Visual Studio 使用，而且代表線上內容提供者加入自訂關鍵字進行搜尋或分類的標準方式。

```xml
<Keyword>
    Code Snippet Keyword
</Keyword>
```

|父項目|說明|
| - |-----------------|
|[Keywords 項目](../ide/code-snippets-schema-reference.md#keywords-element)|將個別 `Keyword` 項目設為群組。|

需要文字值。 程式碼片段的關鍵字。

## <a name="keywords-element"></a>Keywords 元素

將個別 `Keyword` 項目設為群組。 這些程式碼片段關鍵字是由 Visual Studio 使用，而且代表線上內容提供者加入自訂關鍵字進行搜尋或分類的標準方式

```xml
<Keywords>
    <Keyword>... </Keyword>
    <Keyword>... </Keyword>
</Keywords>
```

|子項目|說明|
|-------------------|-----------------|
|[Keyword 項目](../ide/code-snippets-schema-reference.md#keyword-element)|選擇性項目。 包含程式碼片段的個別關鍵字。 `Keyword` 項目中可能有零個或多個 `Keywords` 項目。|

|父項目|說明|
| - |-----------------|
|[Header 項目](../ide/code-snippets-schema-reference.md#header-element)|包含有關該程式碼片段的一般資訊。|

## <a name="literal-element"></a>Literal 項目

定義您可以編輯的程式碼片段常值。 `Literal` 項目是用以辨認整個包含在程式碼片段中一小段程式碼的取代，但有可能會在插入程式碼後加以自訂。 例如常值字串、數值以及一些應宣告為常值的變數名稱。

常值和物件不能包含值為 selected 或 end 的 **ID** 項目。 `$selected$` 值代表在文件中選取的文字，這些文字會在叫用時插入程式碼片段中。 `$end$` 會標記程式碼片段插入後，放置游標的位置。

```xml
<Literal Editable="true/false">
   <ID>... </ID>
   <ToolTip>... </ToolTip>
   <Default>... </Default>
   <Function>... </Function>
</Literal>
```

|屬性|說明|
|---------------|-----------------|
|`Editable`|選擇性 `Boolean` 屬性。 指定在程式碼片段插入後您是否可以編輯常值。 此屬性的預設值為 `true`。|

|子項目|說明|
|-------------------|-----------------|
|[Default 項目](../ide/code-snippets-schema-reference.md#default-element)|必要項目。 當您插入程式碼片段時，指定常值的預設值。 `Default` 項目中只能有一個 `Literal` 項目。|
|[Function 項目](../ide/code-snippets-schema-reference.md#function-element)|選擇性項目。 指定常值在 Visual Studio 中獲得焦點時要執行的函式。 `Function` 項目中可能有零個或一個 `Literal` 項目。|
|[ID 項目](../ide/code-snippets-schema-reference.md#id-element)|必要項目。 指定常值的唯一識別項。 `ID` 項目中只能有一個 `Literal` 項目。|
|[ToolTip 項目](../ide/code-snippets-schema-reference.md#tooltip-element)|選擇性項目。 描述常值需要的值和使用方式。 `Literal` 項目中可能有零或一個 **Tooltip** 項目。|

|父項目|說明|
| - |-----------------|
|[Declarations 項目](../ide/code-snippets-schema-reference.md#declarations-element)|包含您可以編輯之程式碼片段的常值和物件。|

## <a name="namespace-element"></a>Namespace 元素

指定必須匯入的命名空間，匯入後程式碼片段才能進行編譯和執行。 在 `Namespace` 項目中指定的命名空間會自動加入至程式碼開頭的 `Imports` 陳述式中 (如果不存在的話)。

> [!NOTE]
> 只有 Visual Basic 專案支援 `Namespace` 項目。

```xml
<Namespace>
    Namespace
</Namespace>
```

|父項目|說明|
| - |-----------------|
|[Import 項目](../ide/code-snippets-schema-reference.md#import-element)|匯入指定的命名空間。|

需要文字值。 此文字會指定程式碼片段假設已匯入的命名空間。

## <a name="object-element"></a>Object 元素

定義您可以編輯的程式碼片段物件。 `Object` 項目是用以識別程式碼片段所需的項目，但有可能定義在程式碼片段本身的外面。 例如，Windows Form 控制項、ASP.NET 控制項、物件執行個體以及類型執行個體應該宣告為物件。 物件宣告需要指定類型，可透過 `Type` 項目指定。

```xml
<Object Editable="true/false">
    <ID>... </ID>
    <Type>... </Type>
    <ToolTip>... </ToolTip>
    <Default>... </Default>
    <Function>... </Function>
</Object>
```

|屬性|說明|
|---------------|-----------------|
|`Editable`|選擇性 `Boolean` 屬性。 指定在程式碼片段插入後您是否可以編輯常值。 此屬性的預設值為 `true`。|

|子項目|說明|
|-------------------|-----------------|
|[Default 項目](../ide/code-snippets-schema-reference.md#default-element)|必要項目。 當您插入程式碼片段時，指定常值的預設值。 `Default` 項目中只能有一個 `Literal` 項目。|
|[Function 項目](../ide/code-snippets-schema-reference.md#function-element)|選擇性項目。 指定常值在 Visual Studio 中獲得焦點時要執行的函式。 `Function` 項目中可能有零個或一個 `Literal` 項目。|
|[ID 項目](../ide/code-snippets-schema-reference.md#id-element)|必要項目。 指定常值的唯一識別項。 `ID` 項目中只能有一個 `Literal` 項目。|
|[ToolTip 項目](../ide/code-snippets-schema-reference.md#tooltip-element)|選擇性項目。 描述常值需要的值和使用方式。 `Literal` 項目中可能有零或一個 **Tooltip** 項目。|
|[Type 項目](../ide/code-snippets-schema-reference.md#type-element)|必要項目。 指定物件類型。 `Type` 項目中只能有一個 `Object` 項目。|

|父項目|說明|
| - |-----------------|
|[Declarations 項目](../ide/code-snippets-schema-reference.md#declarations-element)|包含您可以編輯之程式碼片段的常值和物件。|

## <a name="reference-element"></a>Reference 元素

指定程式碼片段所需之組件參考的相關資訊。

```xml
<Reference>
    <Assembly>... </Assembly>
    <Url>... </Url>
</Reference>
```

|子項目|說明|
|-------------------|-----------------|
|[Assembly 項目](../ide/code-snippets-schema-reference.md#assembly-element)|必要項目。 包含程式碼片段參考的組件名稱。 `Assembly` 項目中只能有一個 `Reference` 項目。|
|[Url 項目](../ide/code-snippets-schema-reference.md#url-element)|選擇性項目。 包含可提供參考組件詳細資訊的 URL。 `Url` 項目中可能有零個或一個 `Reference` 項目。|

|父項目|說明|
| - |-----------------|
|[References 項目](../ide/code-snippets-schema-reference.md#references-element)|`Reference` 項目的群組項目。|

## <a name="references-element"></a>References 元素

將個別 `Reference` 項目設為群組。

```xml
<References>
    <Reference>... </Reference>
</References>
```

|子項目|說明|
|-------------------|-----------------|
|[Reference 項目](../ide/code-snippets-schema-reference.md#reference-element)|選擇性項目。 包含程式碼片段的組件參考資訊。 `Reference` 項目中可能有零個或多個 `References` 項目。|

|父項目|說明|
| - |-----------------|
|[Snippet 項目](../ide/code-snippets-schema-reference.md#snippet-element)|包含程式碼片段的參考、匯入、宣告和程式碼。|

## <a name="shortcut-element"></a>Shortcut 元素

指定用來插入程式碼片段的捷徑文字。 `Shortcut` 項目的文字值只能包含英數字元、短破折號 ( - ) 及底線 ( _ )。

> [!CAUTION]
> C++ 程式碼片段捷徑不支援 _ 和 - 字元。

```xml
<Shortcut>
    Shortcut Text
</Shortcut>
```

|父項目|說明|
| - |-----------------|
|[Header 項目](../ide/code-snippets-schema-reference.md#header-element)|包含有關該程式碼片段的一般資訊。|

 可選擇使用文字值。 此文字是做為插入程式碼片段的捷徑。

## <a name="snippet-element"></a>Snippet 元素

指定程式碼片段的參考、匯入、宣告及程式碼。

```xml
<Snippet>
    <References>... </References>
    <Imports>... </Imports>
    <Declarations>... </Declarations>
    <Code>... </Code>
</Snippet>
```

|子項目|說明|
|-------------------|-----------------|
|[Code 項目](../ide/code-snippets-schema-reference.md#code-element)|必要項目。 指定您要插入文件檔的程式碼。 `Code` 項目中只能有一個 `Snippet` 項目。|
|[Declarations 項目](../ide/code-snippets-schema-reference.md#declarations-element)|選擇性項目。 指定構成您可以編輯的程式碼片段部分的常值和物件。 `Declarations` 項目中可能有零個或一個 `Snippet` 項目。|
|[Imports 項目](../ide/code-snippets-schema-reference.md#imports-element)|選擇性項目。 將個別 `Import` 項目設為群組。 `Imports` 項目中可能有零個或一個 `Snippet` 項目。|
|[References 項目](../ide/code-snippets-schema-reference.md#references-element)|選擇性項目。 將個別 `Reference` 項目設為群組。 `References` 項目中可能有零個或一個 `Snippet` 項目。|

|父項目|說明|
| - |-----------------|
|[CodeSnippet 項目](../ide/code-snippets-schema-reference.md#codesnippet-element)|讓您指定可插入 Visual Studio 程式碼檔中的標題和多個 IntelliSense 程式碼片段。|

## <a name="snippettype-element"></a>SnippetType 項目

指定 Visual Studio 如何插入程式碼片段。

```xml
<SnippetType>
    SurroundsWith/Expansion
</SnippetType>
```

|父項目|說明|
| - |-----------------|
|[SnippetTypes 項目](../ide/code-snippets-schema-reference.md#snippettypes-element)|將 `SnippetType` 項目設為群組。|

文字值必須是下列其中一個值：

-   `SurroundsWith`：允許將程式碼片段放置在所選取程式碼的前後。

-   `Expansion`：允許在游標所在位置插入程式碼片段。

-   `Refactoring`：指定在 C# 重構期間使用程式碼片段。 `Refactoring` 無法在自訂程式碼片段中使用。

## <a name="snippettypes-element"></a>SnippetTypes 元素

將個別 `SnippetType` 項目設為群組。 如果沒有 `SnippetTypes` 項目，程式碼片段就可以插入程式碼中的任何位置。

```xml
<SnippetTypes>
    <SnippetType>... </SnippetType>
    <SnippetType>... </SnippetType>
</SnippetTypes>
```

|子項目|說明|
|-------------------|-----------------|
|[SnippetType 項目](../ide/code-snippets-schema-reference.md#snippettype-element)|選擇性項目。 指定 Visual Studio 如何將程式碼片段插入程式碼中。 `SnippetType` 項目中可能有零個或多個 `SnippetTypes` 項目。|

|父項目|說明|
| - |-----------------|
|[Header 項目](../ide/code-snippets-schema-reference.md#header-element)|指定有關程式碼片段的一般資訊。|

## <a name="title-element"></a>Title 元素

指定程式碼片段的標題。 儲存在程式碼片段之 `Title` 項目中的標題會出現在 [程式碼片段選擇器] 中，以及出現在 [程式碼片段管理員] 的程式碼片段描述中。

```xml
<Title>
    Code Snippet Title
</Title>
```

|父項目|說明|
| - |-----------------|
|[Header 項目](../ide/code-snippets-schema-reference.md#header-element)|指定有關程式碼片段的一般資訊。|

 需要文字值。 此文字會指定程式碼片段的標題。

## <a name="tooltip-element"></a>ToolTip 元素

描述程式碼片段中常值或物件的預期值和使用方式，這會在 Visual Studio 將程式碼片段插入專案時，顯示在工具提示中。 在插入程式碼片段後，當滑鼠停留在常值或物件上時，就會顯示工具提示文字。

```xml
<ToolTip>
    ToolTip description
</ToolTip>
```

|父項目|說明|
| - |-----------------|
|[Literal 項目](../ide/code-snippets-schema-reference.md#literal-element)|定義您可以編輯之程式碼片段的常值欄位。|
|[Object 項目](../ide/code-snippets-schema-reference.md#object-element)|定義您可以編輯之程式碼片段的物件欄位。|

 需要文字值。 此文字會指定要與程式碼片段中的物件或常值相關聯的工具提示描述。

## <a name="type-element"></a>Type 項目

指定物件類型。 `Object` 項目是用以識別程式碼片段所需的項目，但有可能定義在程式碼片段本身的外面。 例如，Windows Form 控制項、ASP.NET 控制項、物件執行個體以及類型執行個體應該宣告為物件。 物件宣告需要指定類型，可透過 `Type` 項目指定。

```xml
<Type>
    Type
</Type>
```

|父項目|說明|
| - |-----------------|
|[Object 項目](../ide/code-snippets-schema-reference.md#object-element)|定義您可以編輯之程式碼片段的物件欄位。|

 需要文字值。 此文字會指定物件的類型。

## <a name="url-element"></a>Url 元素

指定提供所參考組件相關詳細資訊的 URL。

> [!NOTE]
> 只有 Visual Basic 專案支援 `Url` 項目。

```xml
<Url>
    www.microsoft.com
</Url>
```

|父項目|說明|
| - |-----------------|
|[Reference 項目](../ide/code-snippets-schema-reference.md#reference-element)|指定程式碼片段所需的組件參考。|

需要文字值。 此文字會指定參考組件詳細資訊的 URL。 當參考無法加入至專案時，就會顯示此 URL。

## <a name="see-also"></a>另請參閱

- [程式碼片段](../ide/code-snippets.md)
- [逐步解說：建立程式碼片段](../ide/walkthrough-creating-a-code-snippet.md)
