---
title: 以程式設計方式跨工作表複製資料和格式
description: 瞭解如何使用 FillAcrossSheets 方法，將資料從某個工作表的某個範圍複製到活頁簿中的所有其他工作表。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0696c99e78ee1b6a7acd174e5463bbdc514fe160
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828562"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>如何：以程式設計方式跨工作表複製資料和格式
  您可以使用方法，將資料從某個工作表的某個範圍複製到活頁簿中的所有其他工作表 <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> 。 指定範圍，以及是否要複製資料、格式化或兩者。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>範例
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet44":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet44":::

## <a name="compile-the-code"></a>編譯程式碼
 此範例需要 `rangeData` 在工作表中命名的範圍。

## <a name="see-also"></a>另請參閱
- [使用工作表](../vsto/working-with-worksheets.md)
- [如何：以程式設計方式在活頁簿中加入新的工作表](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [如何：以程式設計方式變更包含選定儲存格的工作表資料列格式](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
