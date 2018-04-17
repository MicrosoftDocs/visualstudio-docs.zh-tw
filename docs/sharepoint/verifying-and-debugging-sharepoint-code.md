---
title: 驗證及偵錯 SharePoint 程式碼 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fc294bcd94c7fd4c1ed699d8aaceab66eaecc47b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="verifying-and-debugging-sharepoint-code"></a>驗證及偵錯 SharePoint 程式碼
 
您可以藉由使用 IntelliTrace 和單元測試更輕鬆地對 SharePoint 方案進行偵錯，並確保方案中的每一個方法都能正確運作。 您可以使用 Visual Studio 中的 SharePoint 專案的這些功能，依照其他專案類型的相同程序。

## <a name="intellitrace"></a>IntelliTrace

藉由使用 IntelliTrace，您不但可以判斷目前 SharePoint 方案的狀態，也可以判斷過去發生的事件以及發生的內容。 您可以來回巡覽至 SharePoint 方案中記錄相關事件的各個時間點，並檢閱每一個時間點的狀態與變數值。 藉由使用這個動態巡覽，您就可以快速輕鬆地對 SharePoint 方案進行偵錯，而不需要設定大量中斷點。 您也可以儲存至 IntelliTrace (.iTrace) 記錄檔的偵錯工作階段，稍後在 Visual Studio Enterprise 中開啟和執行當機後偵錯。 .ITrace 檔案包含有關時機和位置特定 SharePoint 錯誤發生，詳細的資訊，以便您更輕鬆地找出造成錯誤。 .iTrace 檔中的資訊是統一記錄系統 (ULS) 在 SharePoint 中建立之完整錯誤記錄的子集。 這項資訊包括 SharePoint 專屬的事件，像是使用者設定檔何時開啟或關閉，以及 SharePoint 專案中的屬性何時載入、讀取或變更。 您可以設定 IntelliTrace 記錄的事件。 如需詳細資訊，請參閱[使用儲存的 IntelliTrace 資料](/visualstudio/debugger/using-saved-intellitrace-data)。

當 SharePoint 中發生錯誤時，錯誤對話方塊會顯示該特定錯誤的「相互關聯識別碼」識別項。 您也可以從 .iTrace 檔中列出的事件取得相互關聯識別碼。 若要顯示所有所指定的相互關聯識別碼發生的事件清單，您可以輸入中的識別碼**分析**IntelliTrace 摘要頁面區段。 在該區段中，您可以選擇僅顯示發生的事件名稱，或是顯示事件名稱與其呼叫資訊，像是函式名稱、結束和進入點、參數及傳回值。

您也可以選擇在 IntelliTrace 中取得 Visual Studio 事件**F5**索引鍵。 不過，若要取得 SharePoint 專屬的事件，您必須使用 Microsoft Monitoring Agent 收集 SharePoint 方案中的 IntelliTrace 資料。 這個工具會收集 IntelliTrace 資料，並針對部署在 Visual Studio 以外的應用程式建立 .iTrace 檔。 如需詳細資訊，請參閱[IntelliTrace 功能](/visualstudio/debugger/intellitrace-features)和[使用 IntelliTrace 獨立收集器](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector)。

## <a name="unit-testing"></a>單元測試

您可以更輕鬆地找到錯誤，程式碼中的執行單元測試，您撰寫並執行測試方法內的測試程式碼。 這些方法會包含空白的變數和 Assert 陳述式可讓您確認的邏輯和您的 SharePoint 物件模型為基礎的專案功能。 如需詳細資訊，請參閱[對程式碼進行單元測試](/visualstudio/test/unit-test-your-code)。

### <a name="support-for-microsoft-fakes-framework"></a>Microsoft Fakes Framework 的支援

SharePoint 專案支援 Microsoft Fakes，它是一種隔離架構，您可以利用該架構在 .NET Framework 為基礎的應用程式中建立委派為主的測試 Stub 和填充碼。 使用 Fakes 架構可以在單元測試中建立、維護及插入虛擬實作。 這些 Stub 和填充碼會將您的單元測試與環境隔離。 您可以建立 Stub 測試利用介面的程式碼，或是具有可覆寫方法的非密封類別。 您可以建立填充碼將對具有靜態或不可覆寫方法之密封類別的硬式編碼呼叫重新導向至替代填充碼實作。 您也可以使用具有 Stub 類型和填充碼類型的委派，動態自訂個別 Stub 成員的行為。 如需詳細資訊，請參閱[隔離測試程式碼在使用 Microsoft Fakes](/visualstudio/test/isolating-code-under-test-with-microsoft-fakes)。

## <a name="related-articles"></a>相關文章

|標題|描述|
|-----------|-----------------|
|[IntelliTrace](/visualstudio/debugger/intellitrace)|描述如何使用 IntelliTrace 更輕鬆地對 Visual Studio 方案進行偵錯。|
|[逐步解說：使用 IntelliTrace 偵錯 SharePoint 應用程式](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|示範如何使用 IntelliTrace 尋找 SharePoint 專案中的編碼錯誤。|
|[對程式碼進行單元測試](/visualstudio/test/unit-test-your-code)|描述如何使用單元測試程式碼中找出邏輯錯誤。|

## <a name="see-also"></a>另請參閱

[改善程式碼品質](/visualstudio/test/improve-code-quality)
