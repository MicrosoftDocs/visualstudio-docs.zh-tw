---
title: HOW TO：搭配使用 XML 結構描述設計工具和 XML 常值
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1483077142d1c60d3309458aedbe1abd7e2e2b00
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53863390"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>HOW TO：使用 XML 常值中的 XML 結構描述設計工具

本主題描述如何在 Visual Studio 專案中檢視與 XML 常值相關的結構描述。

## <a name="to-create-a-new-visual-basic-console-application-project"></a>建立新的 Visual Basic 主控台應用程式專案

1.  啟動 Visual Studio。

2.  從**檔案**功能表上，選取**新增**，然後選取**專案**。 [ **新增專案** ] 對話方塊隨即出現。 針對**專案類型**，選取**其他語言**，然後選取**Visual Basic**。 針對**範本**，選取 主控台應用程式。 然後輸入`XMLLiterals`中**名稱**欄位和中的專案位置**位置**欄位。 按一下 [確定 **Deploying Office Solutions**]。

     隨即會建立新專案。 XMLLiterals 專案包含一個 Visual Basic 來源檔案， *Module1.vb*。

## <a name="to-add-an-existing-xsd-file-to-the-project"></a>將現有 XSD 檔案加入至專案

1.  在記事本中開啟新的文字檔。 XML 結構描述範例程式碼複製[採購單結構描述](../xml-tools/sample-xsd-file-simple-schema.md)和並貼到檔案中。

2.  將檔案儲存在某個位置名稱*PurchaseOrderSchema.xsd*。

3.  在**方案總管**，以滑鼠右鍵按一下專案名稱，然後選取**新增**，然後選取**現有項目**。 **加入現有項目** 對話方塊隨即出現。 瀏覽至*PurchaseOrderSchema.xsd*檔案，加以選取，然後按一下 **新增**。

     XMLLiterals 專案現在會包含兩個檔案：*Module1.vb*並*PurchaseOrderSchema.xsd*。

## <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>根據專案中包含的 XSD 檔案，加入含有 XML 常值的 Visual Basic 程式碼

1. 中的程式碼取代*Module1.vb*為下列程式碼的檔案：

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

2. 以滑鼠右鍵按一下 XML 常值或 XML 命名空間匯入中的任何 XML 節點，然後選取**在結構描述總管中顯示**。

    **XML 結構描述總管**與 XML 常值 XML 結構描述集合相關聯的 Visual Basic 檔案並排顯示。