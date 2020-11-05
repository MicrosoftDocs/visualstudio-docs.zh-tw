---
title: 範例 XSD 檔：關聯性
description: 請參閱 XSD 架構設計工具檔中各種範例所使用的注釋和檔，查看訂單架構的範例 XSD 檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
ms.assetid: 60126510-b7dd-4cb4-92d3-9883590b92f2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6dd4e4f3678cd59562f5945ab26f8d828210375c
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398744"
---
# <a name="sample-xsd-file-relationships"></a>範例 XSD 檔案：關聯性

XSD 結構描述設計工具文件中的數個範例使用下列 XSD 檔案。 這個檔案是附帶註釋和文件的採購單結構描述。

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <xs:element name="pet" type="PetType"/>

  <xs:attributeGroup name="NameAgeAttributes">
    <xs:attribute name="age" type="xs:integer" use="required"/>
    <xs:attribute name="name" type="xs:string" use="required"/>
  </xs:attributeGroup>

  <xs:complexType name="PetType">
    <xs:attributeGroup ref="NameAgeAttributes"/>
  </xs:complexType>

  <xs:element name="cat" substitutionGroup="pet">
    <xs:complexType>
      <xs:complexContent>
        <xs:extension base="PetType">
          <xs:sequence>
            <xs:element name="weight" type="xs:integer"/>
            <xs:element name="color" type="xs:string"/>
            <xs:element name="breed" type="xs:integer"/>
          </xs:sequence>
        </xs:extension>
      </xs:complexContent>
    </xs:complexType>
  </xs:element>

  <xs:element name="dog" substitutionGroup="pet">
    <xs:complexType>
      <xs:complexContent>
        <xs:extension base="PetType">
          <xs:sequence>
            <xs:element name="weight" type="xs:integer"/>
            <xs:element name="color" type="xs:string"/>
            <xs:element name="breed" type="xs:integer"/>
          </xs:sequence>
        </xs:extension>
      </xs:complexContent>
    </xs:complexType>
  </xs:element>

</xs:schema>
```

> [!NOTE]
> 此處所描述的範例公司、組織、產品、網域名稱、電子郵件地址、商標、人員、地點與事件均屬虛構。 並非影射任何真實的公司、組織、產品、網域名稱、電子郵件地址、商標、人員、地點或事件。
