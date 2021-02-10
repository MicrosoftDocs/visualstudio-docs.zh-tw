---
title: HOW TO：建立 XML 片段
description: 瞭解如何使用 Visual Studio 中的 XML 編輯器建立 XML 程式碼片段，讓您更快速地建立 XML 檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ad907175f0826a5dd040f77c03517e00d4e1391c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959775"
---
# <a name="how-to-create-xml-snippets"></a>如何：建立 XML 片段

XML 編輯器可以用來建立新的 XML 片段。 該編輯器包括名為 Snippet 的 XML 片段，其為建立新 XML 片段的重複使用片段。

## <a name="to-create-a-new-xml-snippet"></a>建立新的 XML 片段

若要建立新的 XML 程式碼片段，請建立新的 XML 檔案，並使用 [ **插入程式碼片段** ] 功能。

1. **在 [檔案**] 功能表上 **，按一下 [****新增**]，然後按一下 [檔案]。

2. 按一下 [ **XML** 檔案]，然後按一下 [ **開啟**]。

3. 在編輯器窗格中按一下滑鼠右鍵，然後選取 [ **插入程式碼片段**]。

4. 從清單中選取 [ **程式碼片段** ]，然後按 **enter** 鍵。

5. 對新片段進行任何變更。

6. 在 [ **檔案** ] 功能表中，選取 [ **儲存 XMLFile.xml**。

     [ **另存** 新檔] 對話方塊隨即顯示。

7. 輸入新程式碼片段的名稱，然後從 [**存檔類型**] 下拉式清單中選取 [**程式碼片段** 檔案]。

8. 使用 [ **儲存于** ] 下拉式清單，將檔案位置變更為 [ *My Documents\Visual Studio 2005 \ Code Snippets\XML\My XML 程式碼片段* ] 資料夾，然後按 [ **儲存**]。

## <a name="snippet-description"></a>程式碼片段描述

本節說明重複使用片段中的某些索引鍵項目。 如需 XML 程式碼片段所使用之架構元素的詳細資訊，請參閱 [程式碼片段架構參考](../ide/code-snippets-schema-reference.md)。

### <a name="snippettype-element"></a>SnippetType 項目

編輯器支援兩種片段型別：

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

`Expansion`當您叫用 [**插入程式碼片段**] 命令時，此類型會決定是否要顯示程式碼片段。 此 `SurroundsWith` 類型會決定當您叫 **用 [使用圍住** ] 命令時，是否要顯示程式碼片段。

### <a name="code-element"></a>程式碼項目

`Code` 項目定義叫用片段時將插入的 XML 文字。

> [!NOTE]
> XML 片段文字必須包含在 `<![CDATA[...]]>` 區段中。

以下是重複使用片段建立的 `Code` 項目。

```xml
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

`Code` 項目包含三個變數。

- $name$ 為使用者定義的變數。 它可建立 `name` 項目，其具有預設為 name 的可編輯值。 使用者定義變數使用 `Literal` 項目來定義。

- $selected$ 為預先定義的變數。 它代表在叫用程式碼片段之前，在 XML 編輯器中選取的文字。 這個變數的位置決定了所選文字在環繞該選取內容之程式碼片段中出現的位置。

- $end$ 為預先定義的變數。 當使用者按下 **Enter 鍵** 完成編輯程式碼片段欄位時，此變數會決定插入插入號 (^) 的位置。

  上面的 `Code` 項目會插入下列 XML 文字：

```xml
<test>
  <name>name</name>
</test>
```

將名稱項目的值標記為可編輯區域。

### <a name="literal-element"></a>Literal 項目

`Literal` 項目用於識別插入檔案後可自訂的取代文字。 例如，常值字串、數值及某些可以宣告為常值的變數名稱。 您可以在 XML 片段中定義任意數目的常值，並可在片段中多次參考它們。 以下是定義預設值為 name 之 $name$ 變數的 `Literal` 項目範例。

```xml
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

常值亦可參考函式。 XML 編輯器包含名為 **LookupPrefix** 的函數。 **LookupPrefix** 函式會從 XML 檔中的位置查閱指定的命名空間 URI，以從中叫用此程式碼片段，並傳回為該命名空間定義的命名空間前置詞（如果有的話），並在該名稱中包含冒號 (： ) 。 以下是 `Literal` 使用 **LookupPrefix** 函數的元素範例。

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

$prefix$ 變數即可在 XML 片段中的其他位置使用。

## <a name="see-also"></a>另請參閱

- [XML 片段](../xml-tools/xml-snippets.md)
- [如何：使用 XML 程式碼片段](../xml-tools/how-to-use-xml-snippets.md)
- [如何：從 XML 架構產生 XML 片段](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
