---
title: 如何： 以程式設計方式開啟活頁簿 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a243e4972bcee77aa9d76957ab5cce289e30e120
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-open-workbooks"></a>如何：以程式設計方式開啟活頁簿
  <xref:Microsoft.Office.Interop.Excel.Workbooks> Microsoft Office Excel 中的集合可讓您將使用的所有開啟的活頁簿並開啟活頁簿。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-open-an-existing-workbook"></a>若要開啟現有的活頁簿  
  
1.  使用<xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A>方法<xref:Microsoft.Office.Interop.Excel.Workbooks>集合，將路徑傳遞至活頁簿。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個程式碼範例需要下列項目：  
  
-   名為活頁簿`YourWorkbook.xls`必須存在於一個名為目錄`Test`上磁碟機 c。  
  
## <a name="see-also"></a>另請參閱  
 [使用活頁簿](../vsto/working-with-workbooks.md)   
 [如何： 以程式設計方式文字檔開啟為活頁簿](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [如何： 以程式設計方式建立新的活頁簿](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [如何： 以程式設計方式儲存活頁簿](../vsto/how-to-programmatically-save-workbooks.md)   
 [如何： 以程式設計方式關閉活頁簿](../vsto/how-to-programmatically-close-workbooks.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
  