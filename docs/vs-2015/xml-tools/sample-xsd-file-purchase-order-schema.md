---
title: 範例 XSD 檔案： 採購單結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f92b63b5-ec61-43b5-ae1e-63432a7a7e30
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6b421c1e7113bbabaea8cfd21659926053a009e7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49272294"
---
# <a name="sample-xsd-file-purchase-order-schema"></a>範例 XSD 檔案：採購單結構描述
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XSD 結構描述設計工具文件中的數個範例使用下列 XSD 檔案。 這個檔案是採購單結構描述。  
  
```xml  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
          xmlns:tns="http://tempuri.org/PurchaseOrderSchema.xsd"   
          targetNamespace="http://tempuri.org/PurchaseOrderSchema.xsd"   
          elementFormDefault="qualified">  
  <xsd:element name='comment' type='xsd:string'/>  
  
  <xsd:element name='purchaseOrder' type='tns:PurchaseOrderType'/>  
  
  <xsd:complexType name='USAddress'>  
    <xsd:annotation>  
      <xsd:documentation>  
        Purchase order schema for Example.Microsoft.com.  
      </xsd:documentation>  
    </xsd:annotation>  
    <xsd:sequence>  
      <xsd:element name='name'   type='xsd:string'/>  
      <xsd:element name='street' type='xsd:string'/>  
      <xsd:element name='city'   type='xsd:string'/>  
      <xsd:element name='state'  type='xsd:string'/>  
      <xsd:element name='zip'    type='xsd:decimal'/>  
    </xsd:sequence>  
    <xsd:attribute name='country' type='xsd:NMTOKEN' fixed='US'/>  
  </xsd:complexType>  
  
  <xsd:simpleType name='SKU'>  
    <xsd:restriction base='xsd:string'>  
      <xsd:pattern value='\d{3}\w{3}'/>  
    </xsd:restriction>  
  </xsd:simpleType>  
  
  <xsd:complexType name='Items'>  
    <xsd:sequence>  
      <xsd:element name='item' minOccurs='0' maxOccurs='unbounded'>  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element name='productName' type='xsd:string'/>  
            <xsd:element name='quantity'>  
              <xsd:simpleType>  
                <xsd:restriction base='xsd:positiveInteger'>  
                  <xsd:minInclusive value='1'/>  
                  <xsd:maxExclusive value='100'/>  
                </xsd:restriction>  
              </xsd:simpleType>  
            </xsd:element>  
            <xsd:element name='USPrice'  type='xsd:decimal'/>  
            <xsd:element ref='tns:comment'/>  
            <xsd:element name='shipDate' type='xsd:date' minOccurs='0'/>  
          </xsd:sequence>  
          <xsd:attribute name='partNum' type='tns:SKU'/>  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
  
  <xsd:complexType name='PurchaseOrderType'>  
    <xsd:sequence>  
      <xsd:element name='shipTo' type='tns:USAddress'/>  
      <xsd:element name='billTo' type='tns:USAddress'/>  
      <xsd:element ref='tns:comment' minOccurs='0'/>  
      <xsd:element name='items'  type='tns:Items'/>  
    </xsd:sequence>  
    <xsd:attribute name='orderDate' type='xsd:date'/>  
    <xsd:attribute name='confirmDate' type='xsd:date' use='required'/>  
  </xsd:complexType>  
</xsd:schema>  
```



