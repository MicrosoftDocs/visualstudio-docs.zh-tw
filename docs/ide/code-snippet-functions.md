---
title: 程式碼片段函式
description: '瞭解可搭配 c # 程式碼片段使用的 GenerateSwitchCases (EnumerationLiteral) 、ClassName ( # A3 和 SimpleTypeName (TypeName) 函數。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ce569dabca9e5d867310b8d510975331f5a9f046
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954432"
---
# <a name="code-snippet-functions"></a>程式碼片段函式

有三個函式可用來與 C# 程式碼片段搭配使用。 函式指定於程式碼片段的 [Function](../ide/code-snippets-schema-reference.md#function-element) 項目中。 如需建立程式碼片段的資訊，請參閱[程式碼片段](../ide/code-snippets.md)。

## <a name="functions"></a>函式

下表描述可用於與程式碼片段中的 `Function` 項目搭配使用的函式。

|函式|描述|語言|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(EnumerationLiteral)`|針對 `EnumerationLiteral` 參數所指定列舉的成員，產生 switch 陳述式和一組 case 陳述式。 `EnumerationLiteral` 參數必須是列舉常值或列舉類型的參考。|C#|
|`ClassName()`|傳回包含已插入程式碼片段的類別名稱。|C#|
|`SimpleTypeName(TypeName)`|在叫用程式碼片段的內容中，將 *TypeName* 參數降低為其最簡單形式。|C#|

## <a name="generateswitchcases-example"></a>GenerateSwitchCases 範例

下列範例會示範如何使用 `GenerateSwitchCases` 函式。 插入此程式碼片段並將列舉輸入至 `$switch_on$` 常值時，`$cases$` 常值會為列舉中的每個值產生 `case` 陳述式。

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>switch</Title>
            <Shortcut>switch</Shortcut>
            <Description>Code snippet for switch statement</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>expression</ID>
                    <ToolTip>Expression to switch on</ToolTip>
                    <Default>switch_on</Default>
                </Literal>
                <Literal Editable="false">
                    <ID>cases</ID>
                    <Function>GenerateSwitchCases($expression$)</Function>
                    <Default>default:</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    switch ($expression$)
                    {
                        $cases$
                    }
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="classname-example"></a>ClassName 範例

下列範例會示範如何使用 `ClassName` 函式。 插入此程式碼片段時，會將 `$classname$` 常值取代為程式碼檔案中該位置的封入類別名稱。

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Common constructor pattern</Title>
            <Shortcut>ctor</Shortcut>
            <Description>Code Snippet for a constructor</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>type</ID>
                    <Default>int</Default>
                </Literal>
                <Literal>
                    <ID>name</ID>
                    <Default>field</Default>
                </Literal>
                <Literal default="true" Editable="false">
                    <ID>classname</ID>
                    <ToolTip>Class name</ToolTip>
                    <Function>ClassName()</Function>
                    <Default>ClassNamePlaceholder</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp" Format="CData">
                <![CDATA[
                    public $classname$ ($type$ $name$)
                    {
                        this._$name$ = $name$;
                    }
                    private $type$ _$name$;
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="simpletypename-example"></a>SimpleTypeName 範例

此範例示範如何使用 `SimpleTypeName` 函式。 將此程式碼片段插入至程式碼檔案時，會將 `$SystemConsole$` 常值取代為叫用程式碼片段之內容中 <xref:System.Console> 類型的最簡單表單。

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Console_WriteLine</Title>
            <Shortcut>cw</Shortcut>
            <Description>Code snippet for Console.WriteLine</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal Editable="false">
                    <ID>SystemConsole</ID>
                    <Function>SimpleTypeName(global::System.Console)</Function>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    $SystemConsole$.WriteLine();
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>另請參閱

- [Function 項目](../ide/code-snippets-schema-reference.md#function-element)
- [程式碼片段結構描述參考](../ide/code-snippets-schema-reference.md)
