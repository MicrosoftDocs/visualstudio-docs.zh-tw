---
title: HOW TO：搭配使用 XML 結構描述設計工具和 XML 常值
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: ed987a54004004fe8c4fbfba686ae1a35d12bb06
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601843"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>如何：搭配使用 XML 架構設計工具和 XML 常值

本主題描述如何在 Visual Basic 專案中檢視與 XML 常值相關的結構描述。

## <a name="create-a-new-visual-basic-project"></a>建立新的 Visual Basic 專案

1. 開啟 Visual Studio。

2. 建立名為**XMLLiterals**的新 Visual Basic**主控台應用程式**專案。

     新專案包含一個 Visual Basic 的原始檔（ *Module1*）。

## <a name="add-an-existing-xsd-file"></a>新增現有的 XSD 檔案

1. 在 [記事本] 中開啟新的文字檔。 從[採購單架構](../xml-tools/sample-xsd-file-simple-schema.md)複製 XML 架構範例程式碼，並將它貼入檔案。

2. 將檔案儲存在名稱為*purchaseorderschema.xsd*的某個位置。

3. 在**方案總管**中，以滑鼠右鍵按一下專案的名稱，選取 [**新增**]，然後選取 [**現有專案**]。 [ **AddExisting 專案**] 對話方塊隨即出現。 流覽至*purchaseorderschema.xsd* ，選取該檔案，然後按一下 [**新增**]。

     XMLLiterals 專案現在包含兩個檔案： [ *Module1* ] 和 [ *purchaseorderschema.xsd*]。

## <a name="add-code"></a>新增程式碼

若要使用 XML 常值來加入 Visual Basic 程式碼，請根據專案中包含的 XSD 檔案：

1. 將 [ *Module1* ] 檔案中的程式碼取代為下列程式碼：

   ```vb
   Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">

   Module Module1
      Sub Main()

          Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">
                               <ns:ShipTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:ShipTo>
                               <ns:BillTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:BillTo>
                           </ns:PurchaseOrder>

      End Sub
   End Module
   ```

2. 以滑鼠右鍵按一下 XML 常值或 XML 命名空間匯入中的任何 XML 節點，然後選取 [**在架構瀏覽器中顯示**]。

   **Xml 架構瀏覽器**會與 Visual Basic 檔案並排顯示，該檔案具有與 xml 架構集相關聯的 xml 常值。