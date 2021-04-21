---
title: 如何：以程式設計方式列出最近使用的活頁簿檔案
description: 瞭解如何使用 Visual Studio，以程式設計方式列出最近使用過的 Microsoft Excel 活頁簿檔案。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ba7ca717af4330e8fb3c102b3a5fe5bf7d9162b6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825325"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>如何：以程式設計方式列出最近使用的活頁簿檔案
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A>屬性會傳回集合，其中包含最近使用之檔案的 Microsoft Office Excel 清單中出現的所有檔案的名稱。 清單的長度會根據使用者選取要保留的檔案數目而有所不同。 您可以在範圍中顯示結果。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>列出範圍物件中最近使用過的活頁簿

1. 在最近使用的檔案清單中執行迴圈，並在相對於物件的儲存格中顯示名稱 <xref:Microsoft.Office.Interop.Excel.Range> 。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet9":::

## <a name="see-also"></a>另請參閱
- [使用活頁簿](../vsto/working-with-workbooks.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
