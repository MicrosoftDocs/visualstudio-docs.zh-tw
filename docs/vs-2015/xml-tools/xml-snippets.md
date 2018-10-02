---
title: XML 程式碼片段 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bae360d1aea43006138397b3bed2857a2b1dad59
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499873"
---
# <a name="xml-snippets"></a>XML 片段
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[XML 程式碼片段](https://docs.microsoft.com/visualstudio/xml-tools/xml-snippets)。  
  
  
XML 編輯器會提供一項功能，稱為*XML 程式碼片段*，可讓您更快速地建置 XML 檔案。 您可藉由將 XML 片段插入檔案來重複使用它們。 還可根據 XML 結構描述定義語言 (XSD) 結構描述，產生 XML 資料。  
  
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
  
 插入片段的方式有兩種。 **插入程式碼片段**命令會將 XML 程式碼片段插入游標位置。 **環繞**命令會以 XML 片段環繞選定文字。 這兩個命令有可能是從**IntelliSense**下方的子功能表**編輯** 功能表中，或編輯器捷徑功能表。  
  
 如需詳細資訊，請參閱 <<c0> [ 如何： 使用 XML 片段](../xml-tools/how-to-use-xml-snippets.md)。  
  
## <a name="schema-generated-xml-snippets"></a>結構描述產生的 XML 片段  
 XML 編輯器還具有從 XML 結構描述產生 XML 片段的功能。 此功能可讓您以從該項目的結構描述資訊產生的 XML 項目來填入項目。  
  
 如需詳細資訊，請參閱 <<c0> [ 如何： 產生的 XML 程式碼片段從 XML 結構描述](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)。  
  
## <a name="create-new-xml-snippets"></a>建立新的 XML 片段  
 除了隨附的程式碼片段[!INCLUDE[msCoName](../includes/msconame-md.md)]Visual Studio 根據預設，您也可以建立及使用您自己的 XML 片段。  
  
 如需詳細資訊，請參閱 <<c0> [ 如何： 建立 XML 片段](../xml-tools/how-to-create-xml-snippets.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XML 編輯器](../xml-tools/xml-editor.md)



