---
title: XML 程式碼片段 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bc8946d62f47291a6e0e3f26032589bfdf0de16
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669355"
---
# <a name="xml-snippets"></a>XML 片段
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 編輯器提供稱為「 *xml 程式碼片段*」的功能，可讓您更快速地建立 XML 檔案。 您可藉由將 XML 片段插入檔案來重複使用它們。 還可根據 XML 結構描述定義語言 (XSD) 結構描述，產生 XML 資料。

## <a name="reusable-xml-snippets"></a>可重複使用的 XML 片段
 XML 編輯器包括許多片段，涵蓋了某些通用工作。 這可讓您更容易地建立 XML 檔案。 例如，如果您在撰寫 XML 結構描述，則使用「複雜型別順序項目」及「簡單型別項目」片段會將下列 XML 文字插入檔案。 然後，您可視需要變更 `name` 值。

```
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

 插入片段的方式有兩種。 [**插入程式碼片段**] 命令會在游標位置插入 XML 程式碼片段。 [**環繞于**] 命令會將 XML 程式碼片段包裝在選取的文字周圍。 這兩個命令都可以從 [**編輯**] 功能表下的 [ **IntelliSense** ] 子功能表，或從編輯器快捷方式功能表中取得。

 如需詳細資訊，請參閱[如何：使用 XML 程式碼片段](../xml-tools/how-to-use-xml-snippets.md)。

## <a name="schema-generated-xml-snippets"></a>結構描述產生的 XML 片段
 XML 編輯器還具有從 XML 結構描述產生 XML 片段的功能。 此功能可讓您以從該項目的結構描述資訊產生的 XML 項目來填入項目。

 如需詳細資訊，請參閱[如何：從 Xml 架構產生 Xml 程式碼片段](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)。

## <a name="create-new-xml-snippets"></a>建立新的 XML 片段
 除了 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio 所包含的程式碼片段，您也可以建立及使用您自己的 XML 程式碼片段。

 如需詳細資訊，請參閱[如何：建立 XML 片段](../xml-tools/how-to-create-xml-snippets.md)。

## <a name="see-also"></a>請參閱
 [XML 編輯器](../xml-tools/xml-editor.md)
