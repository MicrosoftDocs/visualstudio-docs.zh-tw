---
title: "如何： 以程式設計方式將圖形加入至 Visio 文件 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4d73c59ac9ba89a5814a264bb8e8fe3c83b9789e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>如何：以程式設計方式將圖形加入至 Visio 文件
  您可以從樣板擷取主圖形並把圖形放在使用中的頁面上，即可在 Microsoft Office Visio 文件中加入圖形。  
  
 如需詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) 方法、 [Microsoft.Office.Interop.Visio.Application.ActivePage](http://msdn.microsoft.com/library/office/ff765484.aspx) 屬性和 [Microsoft.Office.Interop.Visio.Page.Drop](http://msdn.microsoft.com/library/office/ff765054.aspx) 方法的 VBA 參考文件。  
  
## <a name="adding-shapes-to-a-visio-document"></a>在 Visio 文件中加入圖形  
  
#### <a name="to-add-shapes-to-a-visio-document"></a>在 Visio 文件中加入圖形  
  
-   以使用中的文件，從 Documents.Masters 集合中擷取主圖形，然後將圖形放在使用中的文件。 您可以使用索引或主圖形名稱來擷取主圖形。  
  
     下列程式碼範例會建立空白的 Visio 文件，然後用停駐的 [基本圖形]  樣板開啟它。 程式碼接著會擷取數個圖形，並將它們放在使用中的頁面上。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [使用 Visio 圖案](../vsto/working-with-visio-shapes.md)   
 [如何：以程式設計方式在 Visio 文件中複製並貼上圖形](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  