---
title: 如何： 以程式設計方式文字檔開啟為活頁簿 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cafe64ce693972bd9c254a6bdfc1dcbf70f004c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>如何：以程式設計方式將文字檔開啟為活頁簿
  您可以開啟文字檔，為活頁簿。 您必須傳遞您想要開啟的文字檔案的名稱。 您可以指定數個選擇性參數的詳細資訊，例如開始剖析和資料行的格式檔案中資料的資料列編號。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要下列元件：  
  
-   名為逗號分隔的文字檔案`Test.txt`，其中包含至少三行文字。  
  
-   文字檔案`Test.txt`儲存在磁碟機 c。  
  
## <a name="see-also"></a>另請參閱  
 [使用活頁簿](../vsto/working-with-workbooks.md)   
 [如何： 以程式設計方式開啟活頁簿](../vsto/how-to-programmatically-open-workbooks.md)   
 [如何： 以程式設計方式建立新的活頁簿](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [如何： 以程式設計方式儲存活頁簿](../vsto/how-to-programmatically-save-workbooks.md)   
 [如何： 以程式設計方式關閉活頁簿](../vsto/how-to-programmatically-close-workbooks.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  