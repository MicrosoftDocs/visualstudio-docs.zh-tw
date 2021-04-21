---
title: 以程式設計方式在 Visio 檔中複製並貼上圖形
description: 瞭解如何以程式設計方式複製檔頁面上的圖形，並將其貼入相同檔中的新頁面。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b7cda46330967ef2b2b08db2109a030bbef8cace
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828549"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>如何：以程式設計方式在 Visio 檔中複製並貼上圖形
  您可以程式設計方式，將文件頁面上的圖形複製貼到同一份文件的另一個新頁面上。 您可以選擇將圖形貼到預設位置 (使用中視窗的中央)，或是貼到與原始頁面一樣的座標位置。

## <a name="copy-and-paste-shapes"></a>複製並貼上圖形
 如需物件模型的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle)、 [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval)、 [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)和 [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) 方法以及 [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) 旗標的 VBA 參考文件。

### <a name="to-copy-shapes-to-the-center-of-another-page"></a>若要將圖形複製至另一頁的中央

- 下列範例會示範如何從第一個頁面複製圖形，並貼到第二個頁面的中央。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet14":::

## <a name="copy-and-paste-shapes-with-the-same-positions"></a>複製並貼上具有相同位置的圖形
 如需物件模型的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle)、 [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval)、 [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)和 [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) 方法以及 [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) 旗標的 VBA 參考文件。

 如果您需要控制貼上資訊的格式，並 (選擇性地) 建立原始程式檔的連結 (例如 Microsoft Office Word 檔) ，請使用 PasteSpecial 方法。

### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>若要將圖形和圖形位置複製到另一頁

- 下列範例會示範如何從第一個頁面複製圖形，並以其原始座標位置貼到第二個頁面。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet15":::

## <a name="see-also"></a>另請參閱
- [Visio 方案](../vsto/visio-solutions.md)
- [Visio 物件模型總覽](../vsto/visio-object-model-overview.md)
- [使用 Visio 圖形](../vsto/working-with-visio-shapes.md)
- [如何：以程式設計方式將圖形新增至 Visio 檔](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)
