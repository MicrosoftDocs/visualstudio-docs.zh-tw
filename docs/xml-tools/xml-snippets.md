---
title: XML 片段
description: 瞭解 XML 編輯器中的 XML 程式碼片段功能，可讓您重複使用 XML 程式碼片段並將其插入檔案中，以更快速地建立 XML 檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 158f51ddc8db8f83d98c34aa03b3ee4f5a1a4d01
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874817"
---
# <a name="xml-snippets"></a>XML 片段

XML 編輯器提供稱為 *XML 程式碼片段* 的功能，可讓您更快速地建立 xml 檔案。 您可藉由將 XML 片段插入檔案來重複使用它們。 您也可以根據 XML 架構定義語言 (XSD) 架構來產生 XML 資料。

## <a name="reusable-xml-snippets"></a>可重複使用的 XML 片段

XML 編輯器包含許多涵蓋一些常見工作的程式碼片段。 這可讓您更容易地建立 XML 檔案。 例如，如果您撰寫的是 XML 架構，則使用「複雜型別順序元素」和「簡單類型專案」程式碼片段會將下列 XML 文字插入您的檔案。 然後，您可視需要變更 `name` 值。

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

插入片段的方式有兩種。 [ **插入程式碼片段** ] 命令會在游標位置插入 XML 程式碼片段。 「範圍語句」命令會將所選文字周圍的 XML 程式碼片段包裝 **起來** 。 這兩個命令都可從 [**編輯**] 功能表下的 [ **IntelliSense** ] 子功能表，或從編輯器內的滑鼠右鍵功能表使用。

如需詳細資訊，請參閱 [如何：使用 XML 程式碼片段](../xml-tools/how-to-use-xml-snippets.md)。

## <a name="schema-generated-xml-snippets"></a>架構產生的 XML 片段

XML 編輯器也可以從 XML 架構產生 XML 片段。 此功能可讓您以從該項目的結構描述資訊產生的 XML 項目來填入項目。 如需詳細資訊，請參閱 [如何：從 xml 架構產生 xml 片段](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)。

## <a name="create-new-xml-snippets"></a>建立新的 XML 片段

除了 Visual Studio 預設隨附的程式碼片段，您也可以建立並使用自己的 XML 程式碼片段。 如需詳細資訊，請參閱 [如何：建立 XML 片段](../xml-tools/how-to-create-xml-snippets.md)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的程式碼片段](../ide/code-snippets.md)
- [XML 編輯器](../xml-tools/xml-editor.md)
