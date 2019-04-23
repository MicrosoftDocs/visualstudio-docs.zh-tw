---
title: HOW TO：以程式設計方式將文字檔開啟為活頁簿
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 61e51f6274bc22ed0d34d33f5ff85bfbfbd927bd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060134"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>HOW TO：以程式設計方式將文字檔開啟為活頁簿
  您可以開啟文字檔案，為活頁簿。 您必須傳遞您想要開啟的文字檔案的名稱。 您可以指定數個選擇性參數的詳細資訊，例如若要開始剖析，以及檔案中資料的資料行格式的資料列編號。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要下列元件：

- 以逗號分隔的文字檔案，名為`Test.txt`包含至少三行文字。

- 文字檔`Test.txt`儲存在磁碟機 c。

## <a name="see-also"></a>另請參閱
- [使用活頁簿](../vsto/working-with-workbooks.md)
- [如何：以程式設計方式開啟活頁簿](../vsto/how-to-programmatically-open-workbooks.md)
- [如何：以程式設計方式建立新的活頁簿](../vsto/how-to-programmatically-create-new-workbooks.md)
- [如何：以程式設計方式儲存活頁簿](../vsto/how-to-programmatically-save-workbooks.md)
- [如何：以程式設計方式關閉活頁簿](../vsto/how-to-programmatically-close-workbooks.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
