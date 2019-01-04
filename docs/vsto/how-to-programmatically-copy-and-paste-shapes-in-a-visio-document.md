---
title: HOW TO：以程式設計方式複製並貼上 Visio 文件中的圖形
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a7994d605d22b38b64219a384e5afb0b002ff755
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856484"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>HOW TO：以程式設計方式複製並貼上 Visio 文件中的圖形
  您可以程式設計方式，將文件頁面上的圖形複製貼到同一份文件的另一個新頁面上。 您可以選擇將圖形貼到預設位置 (使用中視窗的中央)，或是貼到與原始頁面一樣的座標位置。  
  
## <a name="copy-and-paste-shapes"></a>複製並貼上圖形  
 如需物件模型的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle)、 [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval)、 [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)和 [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) 方法以及 [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) 旗標的 VBA 參考文件。  
  
### <a name="to-copy-shapes-to-the-center-of-another-page"></a>若要將圖形複製至另一頁的中央  
  
-   下列範例會示範如何從第一個頁面複製圖形，並貼到第二個頁面的中央。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copy-and-paste-shapes-with-the-same-positions"></a>複製並貼上以相同位置的圖形  
 如需物件模型的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle)、 [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval)、 [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)和 [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) 方法以及 [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) 旗標的 VBA 參考文件。  
  
 如果您需要控制貼上資訊的格式，以及 （選擇性） 建立連結至原始程式檔 （例如，Microsoft Office Word 文件），使用 PasteSpecial 方法。  
  
### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>若要將圖形和圖形位置複製到另一頁  
  
-   下列範例會示範如何從第一個頁面複製圖形，並以其原始座標位置貼到第二個頁面。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>另請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [使用 Visio 圖案](../vsto/working-with-visio-shapes.md)   
 [如何：以程式設計方式在 Visio 文件中加入圖形](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
