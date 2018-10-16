---
title: 如何： 建立 XML 文件根據 XSD 結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 54d7ead9f759e990b741ac9c5219af693d10a412
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287288"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>HOW TO：根據 XSD 結構描述建立 XML 文件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
**產生範例 XML**功能會產生範例 XML 檔案，根據 XML 結構描述 (XSD) 檔案。  
  
 您可以針對下列案例使用此選項：  
  
-   了解結構描述中各種建構的使用方式。  
  
-   確認結構描述進行預期的作業。  
  
 **產生範例 XML**功能僅可用於全域項目，而且需要有效的 XML 結構描述設定。  
  
 這項功能通常會產生有效的 XML 文件。 不過，如果結構描述包含下列其中一個或多個項目，範例可能就會無效：  
  
-   `xs:key`、`xs:keyref` 和 `xs:unique` 識別條件約束。  
  
-   `xs:pattern` Facet。  
  
-   `xs:QName` 型別的列舉型別 (Enumeration)。  
  
-   `xs:ENTITY`、`xs:ENTITIES` 和 `xs:NOTATION` 型別。  
  
 此外，請注意，只有當列舉型別出現在 `xs:base64Binary` 的結構描述時，系統才會產生該型別的內容。  
  
### <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>根據 XSD 檔案產生 XML 執行個體文件  
  
1.  請依照下列中的步驟[如何： 建立和編輯 XSD 結構描述檔案](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)。  
  
2.  在  [XML 結構描述總管](../xml-tools/xml-schema-explorer.md)，以滑鼠右鍵按一下`PurchaseOrder`全域項目。 選取 **產生範例 XML**。  
  
     當您選取此選項時，會產生含有下列範例 XML 內容的 PurchaseOrder.xml 檔，並在 XML 編輯器中開啟。  
  
    ```  
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



