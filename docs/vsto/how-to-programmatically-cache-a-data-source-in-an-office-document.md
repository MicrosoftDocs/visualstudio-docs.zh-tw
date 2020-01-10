---
title: 以程式設計方式快取 Office 檔中的資料來源
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 241ce42c2d411fdaf611f3a7f2b52eb40c8c32a2
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189577"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>如何：以程式設計方式快取 Office 檔中的資料來源
  您可以藉由呼叫主專案的 `StartCaching` 方法（例如 <xref:Microsoft.Office.Tools.Word.Document>、<xref:Microsoft.Office.Tools.Excel.Workbook>或 <xref:Microsoft.Office.Tools.Excel.Worksheet>），以程式設計方式將資料物件加入檔中的資料快取。 藉由呼叫主專案的 `StopCaching` 方法，從資料快取中移除資料物件。

 `StartCaching` 方法和 `StopCaching` 方法都是私用的，但是它們會出現在 IntelliSense 中。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 當您使用 `StartCaching` 方法將資料物件加入至資料快取時，不需要使用 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 屬性來宣告資料物件。 不過，資料物件必須符合特定需求，才能加入至資料快取。 如需詳細資訊，請參閱快取[資料](../vsto/caching-data.md)。

## <a name="to-programmatically-cache-a-data-object"></a>以程式設計方式快取資料物件

1. 在類別層級宣告資料物件，而不是在方法內。 此範例假設您要宣告名為 `dataSet1` 的 <xref:System.Data.DataSet>，而您想要以程式設計方式快取。

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2. 具現化資料物件，然後呼叫檔或工作表實例的 `StartCaching` 方法，並傳入資料物件的名稱。

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>停止快取資料物件

1. 呼叫檔或工作表實例的 `StopCaching` 方法，並傳入資料物件的名稱。 這個範例假設您有一個名為 `dataSet1` 的 <xref:System.Data.DataSet>，而您想要停止快取。

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    > 請勿從檔或工作表之 `Shutdown` 事件的事件處理常式呼叫 `StopCaching`。 當 `Shutdown` 事件引發時，修改資料快取的時間太晚。 如需 `Shutdown` 事件的詳細資訊，請參閱[Office 專案中的事件](../vsto/events-in-office-projects.md)。

## <a name="see-also"></a>請參閱

- [快取資料](../vsto/caching-data.md)
- [如何：快取資料以供離線使用或用於伺服器](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [如何：快取受密碼保護檔中的資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [存取伺服器上檔中的資料](../vsto/accessing-data-in-documents-on-the-server.md)
- [儲存資料](../data-tools/save-data-back-to-the-database.md)
