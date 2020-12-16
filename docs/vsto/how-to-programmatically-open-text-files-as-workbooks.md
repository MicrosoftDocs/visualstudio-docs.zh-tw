---
title: 如何：以程式設計方式將文字檔開啟為活頁簿
description: 瞭解如何使用 Visual Studio 以程式設計方式將文字檔開啟為 Microsoft Excel 活頁簿。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 5f471161a8563718f69f14ea341ab099fbf138d8
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525537"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>如何：以程式設計方式將文字檔開啟為活頁簿
  您可以將文字檔開啟為活頁簿。 您必須傳入要開啟之文字檔的名稱。 您可以指定數個選擇性參數，例如要開始剖析的資料列編號，以及檔案中資料的資料行格式。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]

## <a name="compile-the-code"></a>編譯程式碼
 此範例需要下列元件：

- 名為的逗號分隔文字檔 `Test.txt` ，其中至少包含三行文字。

- `Test.txt`要儲存在磁片磁碟機 C 上的文字檔。

## <a name="see-also"></a>另請參閱
- [使用活頁簿](../vsto/working-with-workbooks.md)
- [如何：以程式設計方式開啟活頁簿](../vsto/how-to-programmatically-open-workbooks.md)
- [如何：以程式設計方式建立新的活頁簿](../vsto/how-to-programmatically-create-new-workbooks.md)
- [如何：以程式設計方式儲存活頁簿](../vsto/how-to-programmatically-save-workbooks.md)
- [如何：以程式設計方式關閉活頁簿](../vsto/how-to-programmatically-close-workbooks.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
