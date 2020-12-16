---
title: 如何：以程式設計方式在檔中找到的專案之間執行迴圈
description: 瞭解如何使用 Visual Studio，以程式設計方式執行在 Microsoft Word 檔中找到的專案之間的迴圈。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- loops, through found items in documents
- documents [Office development in Visual Studio], searching
- text [Office development in Visual Studio], searching in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 634012cae7f12f5346ec83bbd2b41c1019ef066d
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525616"
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>如何：以程式設計方式在檔中找到的專案之間執行迴圈
  <xref:Microsoft.Office.Interop.Word.Find>類別具有 <xref:Microsoft.Office.Interop.Word.Find.Found%2A> 屬性，每當找到搜尋的專案時，它就會傳回 **true** 。 您可以使用 <xref:Microsoft.Office.Interop.Word.Range> 方法在 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 中找到的所有執行個體間執行迴圈。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-loop-through-found-items"></a>在找到的項目之間執行迴圈

1. 宣告 <xref:Microsoft.Office.Interop.Word.Range> 物件。

    下列程式碼範例可用於文件層級自訂。

    [!code-vb[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#79)]
    [!code-csharp[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#79)]

    下列程式碼範例可用於 VSTO 增益集。 本範例使用現用文件。

    [!code-vb[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#79)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#79)]

2. 在迴圈中使用 <xref:Microsoft.Office.Interop.Word.Find.Found%2A> 屬性來搜尋該文件中所有相符字串，每當找到字串，就將整數變數遞增 1。

    [!code-vb[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#80)]
    [!code-csharp[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#80)]

3. 顯示在訊息方塊中找不到字串的次數。

    [!code-vb[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#81)]
    [!code-csharp[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#81)]

   下列範例示範完整的方法：

## <a name="document-level-customization-example"></a>檔層級自訂範例

### <a name="to-loop-through-items-in-a-document-level-customization"></a>在文件層級自訂的項目間執行迴圈

1. 下列範例顯示文件層級自訂的完整程式碼。 若要使用此程式碼，請從專案的 `ThisDocument` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#78)]

## <a name="vsto-add-in-example"></a>VSTO 增益集範例

### <a name="to-loop-through-items-in-a-vsto-add-in"></a>若要在 VSTO 增益集中的專案之間執行迴圈

1. 下列範例顯示 VSTO 增益集的完整程式碼。 若要使用此程式碼，請從專案的 `ThisAddIn` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#78)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式搜尋和取代檔中的 rext](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [如何：以程式設計方式在 Word 中設定搜尋選項](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [如何：以程式設計方式定義和選取檔中的範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [如何：以程式設計方式在搜尋後還原選取專案](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
