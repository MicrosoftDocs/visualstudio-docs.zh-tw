---
title: 以程式設計方式快取 Office 檔中的資料來源
description: 瞭解如何藉由呼叫主專案的 StartCaching 方法，以程式設計方式將資料物件新增至檔中的資料快取。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: c0b739a7671f19b126b0566dfc8f4775a2c91063
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845008"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>如何：以程式設計方式快取 Office 檔中的資料來源
  您可以藉由呼叫 `StartCaching` 主專案的方法（例如、或），以程式設計方式將資料物件新增至檔中的資料快取 <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Excel.Workbook> <xref:Microsoft.Office.Tools.Excel.Worksheet> 。 藉由呼叫主專案的方法，從資料快取中移除資料物件 `StopCaching` 。

 `StartCaching`方法和 `StopCaching` 方法都是私用的，但會出現在 IntelliSense 中。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 當您使用 `StartCaching` 方法將資料物件加入至資料快取時，不需要使用屬性來宣告資料物件 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 。 但是，資料物件必須符合要加入至資料快取的特定需求。 如需詳細資訊，請參閱快取 [資料](../vsto/caching-data.md)。

## <a name="to-programmatically-cache-a-data-object"></a>以程式設計方式快取資料物件

1. 在類別層級宣告資料物件，而不是在方法內。 此範例假設您要宣告您想要以程式設計方式快取的 <xref:System.Data.DataSet> 名稱 `dataSet1` 。

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2. 將資料物件具現化，然後呼叫 `StartCaching` 檔或工作表實例的方法，並傳入資料物件的名稱。

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>停止快取資料物件

1. 呼叫 `StopCaching` 檔或工作表實例的方法，並傳入資料物件的名稱。 此範例假設您有想要停止快取的 <xref:System.Data.DataSet> 命名 `dataSet1` 。

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    > 請勿 `StopCaching` 從事件處理常式呼叫 `Shutdown` 檔或工作表的事件。 `Shutdown`引發事件時，修改資料快取的時間太晚。 如需事件的詳細資訊 `Shutdown` ，請參閱 [Office 專案中的事件](../vsto/events-in-office-projects.md)。

## <a name="see-also"></a>另請參閱

- [快取資料](../vsto/caching-data.md)
- [如何：快取資料供離線使用或在伺服器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [如何：快取受密碼保護檔中的資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [存取伺服器檔中的資料](../vsto/accessing-data-in-documents-on-the-server.md)
- [儲存資料](../data-tools/save-data-back-to-the-database.md)
