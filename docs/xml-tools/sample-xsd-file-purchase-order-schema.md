---
title: XSD 範例檔：採購單結構描述
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: sample
ms.assetid: f92b63b5-ec61-43b5-ae1e-63432a7a7e30
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7b26fdef946d37824c0595821541b3cb2adce20
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941475"
---
# <a name="sample-xsd-file-purchase-order-schema"></a>XSD 範例檔案：訂購單結構描述

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