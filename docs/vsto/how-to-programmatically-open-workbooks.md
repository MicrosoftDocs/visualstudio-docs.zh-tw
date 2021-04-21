---
title: 如何：以程式設計方式開啟活頁簿
description: 瞭解如何使用 Visual Studio 以程式設計方式開啟 Microsoft Excel 活頁簿或使用現有的活頁簿。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4dba79b1b0eea03ca3aae23e98fb93e6ef776d80
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824779"
---
# <a name="how-to-programmatically-open-workbooks"></a>如何：以程式設計方式開啟活頁簿
  <xref:Microsoft.Office.Interop.Excel.Workbooks>Microsoft Office Excel 中的集合可讓您使用所有開啟的活頁簿，並開啟活頁簿。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>開啟現有的活頁簿

1. 使用 <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> 集合的方法 <xref:Microsoft.Office.Interop.Excel.Workbooks> ，並傳入活頁簿的路徑。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet2":::

## <a name="compile-the-code"></a>編譯程式碼
 這段程式碼範例需要下列項目：

- 名為的活頁簿 `YourWorkbook.xls` 必須存在於 `Test` 磁片磁碟機 C 上的目錄中。

## <a name="see-also"></a>另請參閱
- [使用活頁簿](../vsto/working-with-workbooks.md)
- [如何：以程式設計方式將文字檔開啟為活頁簿](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [如何：以程式設計方式建立新的活頁簿](../vsto/how-to-programmatically-create-new-workbooks.md)
- [如何：以程式設計方式儲存活頁簿](../vsto/how-to-programmatically-save-workbooks.md)
- [如何：以程式設計方式關閉活頁簿](../vsto/how-to-programmatically-close-workbooks.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
