---
title: 'How to: Programmatically Open Text Files as Workbooks | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.prod: visual-studio-dev14
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
ms.assetid: 056ae3d0-7fe7-4c28-a2a5-5a948baee0e6
caps.latest.revision: 47
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 9966164165f768f438516ba9df993c09a6197b5b
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>How to: Programmatically Open Text Files as Workbooks
  You can open a text file as a workbook. You must pass in the name of the text file you want to open. You can specify several optional parameters, such as which row number to start parsing on and the column format of the data in the file.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Example  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)] [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]  
  
## <a name="compiling-the-code"></a>Compiling the Code  
 This example requires the following components:  
  
-   A comma-delimited text file named `Test.txt` that contains at least three lines of text.  
  
-   The text file `Test.txt` to be stored on drive C.  
  
## <a name="see-also"></a>See Also  
 [Working with Workbooks](../vsto/working-with-workbooks.md)   
 [How to: Programmatically Open Workbooks](../vsto/how-to-programmatically-open-workbooks.md)   
 [How to: Programmatically Create New Workbooks](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [How to: Programmatically Save Workbooks](../vsto/how-to-programmatically-save-workbooks.md)   
 [How to: Programmatically Close Workbooks](../vsto/how-to-programmatically-close-workbooks.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)  
  
  
