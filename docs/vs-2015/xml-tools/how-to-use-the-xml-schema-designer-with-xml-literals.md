---
title: 如何：搭配使用 XML 架構設計工具和 XML 常值 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9e82cf8387756cb4a4abe8b4c41d082485cdcdc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656285"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>HOW TO：搭配使用 XML 結構描述設計工具和 XML 常值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題描述如何在 Visual Basic 專案中檢視與 XML 常值相關的結構描述。

### <a name="to-create-a-new-visual-basic-console-application-project"></a>建立新的 Visual Basic 主控台應用程式專案

1. 啟動 Visual Studio 2010。

2. 從 [**檔案**] 功能表中，選取 [**新增**]，然後選取 [**專案**]。 [ **新增專案** ] 對話方塊隨即出現。 針對 [**專案類型**]，選取 [**其他語言]，** 然後選取 [ **Visual Basic**]。 針對 [**範本**]，選取 [主控台應用程式]。 然後在 [**名稱**] 欄位中輸入 `XMLLiterals`，並在 [**位置**] 欄位中輸入專案位置。 按一下 [確定]。

     隨即會建立新專案。 XMLLiterals 專案包含一個 Visual Basic 原始程式檔：Module1.vb。

### <a name="to-add-an-existing-xsd-file-to-the-project"></a>將現有 XSD 檔案加入至專案

1. 在 [記事本] 中開啟新的文字檔。複製[訂單架構](../xml-tools/sample-xsd-file-simple-schema.md)中的 XML 架構範例程式碼，並將它貼到檔案中。

2. 將檔案儲存至某個位置並命名為 PurchaseOrderSchema.xsd。

3. 在 方案總管中，以滑鼠右鍵按一下專案的名稱，選取 **新增**，然後選取 **現有專案**。 [ **AddExisting 專案**] 對話方塊隨即出現。 流覽至 Purchaseorderschema.xsd，選取該檔案，然後按一下 [**新增**]。

     XMLLiterals 專案現在會包含兩個檔案：Module1.vb 和 PurchaseOrderSchema.xsd。

### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>根據專案中包含的 XSD 檔案，加入含有 XML 常值的 Visual Basic 程式碼

1. 以下列程式碼取代 Module1.vb 檔中的程式碼：

    ```
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

     XML 結構描述總管會與一個 Visual Basic 檔案並排顯示，此檔案具有與 XML 結構描述集相關的 XML 常值。
