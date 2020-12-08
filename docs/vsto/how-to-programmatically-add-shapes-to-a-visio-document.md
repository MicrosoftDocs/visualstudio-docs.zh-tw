---
title: 如何：以程式設計方式將圖形新增至 Visio 檔
description: 瞭解如何藉由從樣板中取出主機板並將圖形放在使用中的頁面上，來將圖形新增至 Microsoft Office Visio 檔。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 819560d584f267bfa54ae2bcfc61a162f45e0383
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848023"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>如何：以程式設計方式將圖形新增至 Visio 檔
  您可以從樣板擷取主圖形並把圖形放在使用中的頁面上，即可在 Microsoft Office Visio 文件中加入圖形。

 如需詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) 方法、 [Microsoft.Office.Interop.Visio.Application.ActivePage](/office/vba/api/Visio.Application.ActivePage) 屬性和 [Microsoft.Office.Interop.Visio.Page.Drop](/office/vba/api/Visio.Page.Drop) 方法的 VBA 參考文件。

## <a name="add-shapes-to-a-visio-document"></a>將圖形新增至 Visio 檔

### <a name="to-add-shapes-to-a-visio-document"></a>在 Visio 文件中加入圖形

- 以使用中的文件，從 Documents.Masters 集合中擷取主圖形，然後將圖形放在使用中的文件。 您可以使用索引或主圖形名稱來擷取主圖形。

     下列程式碼範例會建立空白的 Visio 文件，然後用停駐的 [基本圖形]  樣板開啟它。 程式碼接著會擷取數個圖形，並將它們放在使用中的頁面上。

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]

## <a name="see-also"></a>另請參閱
- [Visio 方案](../vsto/visio-solutions.md)
- [Visio 物件模型總覽](../vsto/visio-object-model-overview.md)
- [使用 Visio 圖形](../vsto/working-with-visio-shapes.md)
- [如何：以程式設計方式在 Visio 檔中複製並貼上圖形](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)
