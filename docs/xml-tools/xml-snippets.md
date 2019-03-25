---
title: XML 片段
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66736431b295f974bda1ca855d88cd5f5f868e7d
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526151"
---
# <a name="xml-snippets"></a>XML 片段

XML 編輯器會提供一項功能，稱為*XML 程式碼片段*，可讓您更快速地建置 XML 檔案。 您可藉由將 XML 片段插入檔案來重複使用它們。 您也可以產生的 XML 結構描述定義語言 (XSD) 結構描述為基礎的 XML 資料。

## <a name="reusable-xml-snippets"></a>可重複使用的 XML 程式碼片段

XML 編輯器包括許多片段，涵蓋一些常見工作。 這可讓您更容易地建立 XML 檔案。 例如，如果您在撰寫 XML 結構描述，使用 「 複雜型別順序項目 」 及 「 簡單型別項目 」 的程式碼片段插入下列 XML 文字至您的檔案。 然後，您可視需要變更 `name` 值。

```xml
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

插入片段的方式有兩種。 **插入程式碼片段**命令會將 XML 程式碼片段插入游標位置。 **環繞**命令會以 XML 片段環繞選定文字。 可能會提供這兩個命令從**IntelliSense**下方的子功能表**編輯** 功能表中，或以滑鼠右鍵按一下功能表編輯器中。

如需詳細資訊，請參閱[如何：使用 XML 片段](../xml-tools/how-to-use-xml-snippets.md)。

## <a name="schema-generated-xml-snippets"></a>結構描述產生 XML 片段

XML 編輯器也會有從 XML 結構描述產生 XML 片段的能力。 此功能可讓您以從該項目的結構描述資訊產生的 XML 項目來填入項目。 如需詳細資訊，請參閱[如何：從 XML 結構描述產生 XML 片段](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)。

## <a name="create-new-xml-snippets"></a>建立新的 XML 片段

除了隨附於 Visual Studio 預設的程式碼片段，您也可以建立及使用您自己的 XML 片段。 如需詳細資訊，請參閱[如何：建立 XML 片段](../xml-tools/how-to-create-xml-snippets.md)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的程式碼片段](../ide/code-snippets.md)
- [XML 編輯器](../xml-tools/xml-editor.md)