---
title: 如何： 建立根據 XSD 結構描述的 XML 文件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 042b5d2975468cbaa8260d830235381904dad7e4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>HOW TO：根據 XSD 結構描述建立 XML 文件
**產生範例 XML**功能會產生範例 XML 檔案，根據 XML 結構描述 (XSD) 檔案。  
  
 您可以針對下列案例使用此選項：  
  
-   了解結構描述中各種建構的使用方式。  
  
-   確認結構描述進行預期的作業。  
  
**產生範例 XML**功能僅適用於全域項目，而且需要有效的 XML 結構描述設定。  
  
這項功能通常會產生有效的 XML 文件。 不過，如果結構描述包含下列其中一個或多個項目，範例可能就會無效：  
  
-   `xs:key`、`xs:keyref` 和 `xs:unique` 識別條件約束。  
  
-   `xs:pattern` Facet。  
  
-   `xs:QName` 型別的列舉型別 (Enumeration)。  
  
-   `xs:ENTITY`、`xs:ENTITIES` 和 `xs:NOTATION` 型別。  
  
此外，請注意，只有當列舉型別出現在 `xs:base64Binary` 的結構描述時，系統才會產生該型別的內容。  
  
### <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>根據 XSD 檔案產生 XML 執行個體文件  
  
1.  請依照[How to： 建立和編輯 XSD 結構描述檔案](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)。  
  
2.  在[XML 結構描述總管](../xml-tools/xml-schema-explorer.md)，以滑鼠右鍵按一下`PurchaseOrder`全域項目。 選取**產生範例 XML**。  
  
     當您選取此選項時，會產生含有下列範例 XML 內容的 PurchaseOrder.xml 檔，並在 XML 編輯器中開啟。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [使用 XML 資料](../xml-tools/working-with-xml-data.md)