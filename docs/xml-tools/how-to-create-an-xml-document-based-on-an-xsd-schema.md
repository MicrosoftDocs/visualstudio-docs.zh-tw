---
title: HOW TO：根據 XSD 結構描述建立 XML 文件
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a190790b915ac8dd011bc9843fe8abdf2d7381ae
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2020
ms.locfileid: "88249574"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>如何：根據 XSD 架構建立 XML 檔

[ **產生範例 xml** ] 功能會根據您的 XML 架構 (XSD) 檔來產生範例 xml 檔案。

您可以針對下列案例使用此選項：

- 了解結構描述中各種建構的使用方式。

- 確認結構描述進行預期的作業。

[ **產生範例 XML** ] 功能僅適用于全域元素，而且需要有效的 XML 架構集。

這項功能通常會產生有效的 XML 文件。 不過，如果結構描述包含下列其中一個或多個項目，範例可能就會無效：

- `xs:key`、`xs:keyref` 和 `xs:unique` 識別條件約束。

- `xs:pattern` facet.

- `xs:QName` 型別的列舉型別 (Enumeration)。

- `xs:ENTITY`、 `xs:ENTITIES` 和 `xs:NOTATION` 類型。

此外，請注意，只有當列舉型別出現在 `xs:base64Binary` 的結構描述時，系統才會產生該型別的內容。

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>根據 XSD 檔案產生 XML 執行個體文件

1. 請依照 [如何：建立和編輯 XSD 架構](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)檔案中的步驟執行。

2. 在 [ [XML 架構] Explorer](../xml-tools/xml-schema-explorer.md)中，選取並按住 (或以滑鼠右鍵按一下 `PurchaseOrder` 全域元素) ，然後選取 [ **產生範例 XML**]。

     當您選取此選項時，PurchaseOrder。具有下列 xml 內容範例的*xml* 檔案將會產生，並在 xml 編輯器中開啟：

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PurchaseOrder OrderDate="1900-01-01" xmlns="http://tempuri.org/PurchaseOrderSchema.xsd">
      <ShipTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </ShipTo>
      <ShipTo country="US">
        <name>name2</name>
        <street>street2</street>
        <city>city2</city>
        <state>state2</state>
        <zip>-79228162514264337593543950335</zip>
      </ShipTo>
      <BillTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </BillTo>
    </PurchaseOrder>
    ```
