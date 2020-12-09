---
title: 驗證和偵錯工具代碼 |Microsoft Docs
description: 驗證和偵錯工具代碼。 使用 IntelliTrace 來檢查方案中過去的事件和目前狀態。 使用單元測試以確保您的方法能夠正常運作。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ce891e40552c0f8927bfd4ce006b750b6e5f8a54
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914500"
---
# <a name="verify-and-debug-sharepoint-code"></a>驗證和偵錯工具代碼
您可以藉由使用 IntelliTrace 和單元測試更輕鬆地對 SharePoint 方案進行偵錯，並確保方案中的每一個方法都能正確運作。 您可以遵循與其他類型專案相同的程式，在 Visual Studio 中使用 SharePoint 專案的這些功能。

## <a name="intellitrace"></a>Intellitrace
藉由使用 IntelliTrace，您不但可以判斷目前 SharePoint 方案的狀態，也可以判斷過去發生的事件以及發生的內容。 您可以來回巡覽至 SharePoint 方案中記錄相關事件的各個時間點，並檢閱每一個時間點的狀態與變數值。 藉由使用這個動態巡覽，您就可以快速輕鬆地對 SharePoint 方案進行偵錯，而不需要設定大量中斷點。 您也可以將偵錯工具儲存到 IntelliTrace 記錄檔 (*. .itrace*) 檔案，稍後在 Visual Studio Enterprise 中開啟，然後執行損毀後的偵錯工具。 *.Itrace* 檔案包含特定 SharePoint 錯誤發生時間和位置的詳細資訊，讓您可以更輕鬆地找出造成錯誤的原因。 *.Itrace* 檔案中的資訊是 SharePoint 所建立之統一記錄系統 (ULS) 的完整錯誤記錄檔的子集。 這項資訊包括 SharePoint 專屬的事件，像是使用者設定檔何時開啟或關閉，以及 SharePoint 專案中的屬性何時載入、讀取或變更。 您可以設定 IntelliTrace 記錄的事件。 如需詳細資訊，請參閱[使用儲存的 IntelliTrace 資料](../debugger/using-saved-intellitrace-data.md)。

當 SharePoint 中發生錯誤時，錯誤對話方塊會顯示該特定錯誤的「相互關聯識別碼」識別項。 您也可以從 *.itrace* 檔案中所列的事件取得相互關聯識別碼。 若要顯示指定相互關聯識別碼所發生之所有事件的清單，您可以在 [IntelliTrace 摘要] 頁面的 [ **分析** ] 區段中輸入識別碼。 在該區段中，您可以選擇僅顯示發生的事件名稱，或是顯示事件名稱與其呼叫資訊，像是函式名稱、結束和進入點、參數及傳回值。

您可以選擇 **F5** 鍵取得 IntelliTrace 中的 Visual Studio 事件。 不過，若要取得 SharePoint 專屬的事件，您必須使用 Microsoft Monitoring Agent 收集 SharePoint 方案中的 IntelliTrace 資料。 此工具會收集 IntelliTrace 資料，並針對 Visual Studio 外部部署的應用程式建立 *.itrace 檔。* 如需詳細資訊，請參閱 [Intellitrace 功能](../debugger/intellitrace-features.md) 和 [使用 intellitrace 獨立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)。

## <a name="unit-test"></a>單元測試
您可以執行單元測試，在測試方法內撰寫和執行測試程式碼，以更輕鬆地在程式碼中找到錯誤。 這些方法包含空白變數和 Assert 語句，可讓您用來根據 SharePoint 物件模型來驗證專案的邏輯和功能。 如需詳細資訊，請參閱[對程式碼進行單元測試](../test/unit-test-your-code.md)。

### <a name="support-for-microsoft-fakes-framework"></a>Microsoft Fakes 架構的支援
SharePoint 專案支援 Microsoft Fakes，它是一種隔離架構，您可以利用該架構在 .NET Framework 為基礎的應用程式中建立委派為主的測試 Stub 和填充碼。 使用 Fakes 架構可以在單元測試中建立、維護及插入虛擬實作。 這些 Stub 和填充碼會將您的單元測試與環境隔離。 您可以建立 Stub 測試利用介面的程式碼，或是具有可覆寫方法的非密封類別。 您可以建立填充碼將對具有靜態或不可覆寫方法之密封類別的硬式編碼呼叫重新導向至替代填充碼實作。 您也可以使用具有 Stub 類型和填充碼類型的委派，動態自訂個別 Stub 成員的行為。 如需詳細資訊，請參閱 [使用 Microsoft Fakes 隔離測試中的程式碼](../test/isolating-code-under-test-with-microsoft-fakes.md)。

## <a name="related-articles"></a>相關文章

|標題|描述|
|-----------|-----------------|
|[IntelliTrace](../debugger/intellitrace.md)|描述如何使用 IntelliTrace 更輕鬆地對 Visual Studio 方案進行偵錯。|
|[逐步解說：使用 IntelliTrace 來對 SharePoint 應用程式進行偵錯工具](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|示範如何使用 IntelliTrace 尋找 SharePoint 專案中的編碼錯誤。|
|[對程式碼進行單元測試](../test/unit-test-your-code.md)|描述如何使用單元測試找出程式碼中的邏輯錯誤。|

## <a name="see-also"></a>另請參閱

- [改善程式碼品質](../test/improve-code-quality.md)