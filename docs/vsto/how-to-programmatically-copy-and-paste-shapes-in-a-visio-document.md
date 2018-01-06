---
title: "如何： 以程式設計方式複製並貼上 Visio 文件中的圖形 |Microsoft 文件"
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
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
ms.assetid: 762d95cf-2d5c-4dea-988b-8f4da88fa1f1
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5b1f3a402d4f39b3648bbcf577ff48a130625b50
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>如何：以程式設計方式在 Visio 文件中複製並貼上圖形
  您可以程式設計方式，將文件頁面上的圖形複製貼到同一份文件的另一個新頁面上。 您可以選擇將圖形貼到預設位置 (使用中視窗的中央)，或是貼到與原始頁面一樣的座標位置。  
  
## <a name="copying-and-pasting-shapes"></a>複製並貼上圖形  
 如需物件模型的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx)、 [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx)、 [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)和 [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) 方法以及 [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](https://msdn.microsoft.com/library/office/ff765187.aspx) 旗標的 VBA 參考文件。  
  
#### <a name="to-copy-shapes-to-the-center-of-another-page"></a>若要將圖形複製至另一頁的中央  
  
-   下列範例會示範如何從第一個頁面複製圖形，並貼到第二個頁面的中央。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copying-and-pasting-shapes-with-the-same-positions"></a>複製圖形並以相同位置貼上圖形  
 如需物件模型的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx)、 [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx)、 [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)和 [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) 方法以及 [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](https://msdn.microsoft.com/library/office/ff765187.aspx) 旗標的 VBA 參考文件。  
  
 如果您需要控制貼上資訊的格式，以及 （選擇性） 建立的原始程式檔 （例如，Microsoft Office Word 文件） 的連結，請使用 PasteSpecial 方法。  
  
#### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>若要將圖形和圖形位置複製到另一頁  
  
-   下列範例會示範如何從第一個頁面複製圖形，並以其原始座標位置貼到第二個頁面。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [使用 Visio 圖案](../vsto/working-with-visio-shapes.md)   
 [如何：以程式設計方式將圖形新增至 Visio 文件](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  