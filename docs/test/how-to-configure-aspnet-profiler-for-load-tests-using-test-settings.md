---
title: 設定 ASP.NET 分析工具以進行負載測試
description: 瞭解如何使用 ASP.NET profiler 診斷資料介面卡來收集 ASP.NET profiler 資訊。
ms.custom: SEO-VS-2020
ms.date: 10/13/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 6222d4ff9107a44c52846d2904668dab225e35a6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966769"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>如何：在 Visual Studio 中使用測試設定來設定 ASP.NET 分析工具以進行負載測試

您可以使用 ASP.NET 分析工具診斷資料配接器，收集 ASP.NET 分析工具資訊。 這個診斷資料配接器會收集 ASP.NET 應用程式的效能資料。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> 此診斷資料配接器無法用於使用 Microsoft Test Manager (在 Visual Studio 2017) 中淘汰的測試。 ASP.NET 分析工具診斷配接器只能與使用網站的負載測試搭配使用，且需要 Visual Studio Enterprise。

ASP.NET 分析工具診斷資料配接器可讓您在執行負載測試時，從應用程式層中收集 ASP.NET 分析工具資料。 若為長時間的負載測試 (例如，執行時間超過一小時的負載測試)，您就不應該執行分析工具， 因為分析工具檔案可能會變得很龐大，高達數百 MB。 而是，請使用 ASP.NET 分析工具來執行較短的負載測試，這樣做仍然會提供您深入診斷效能問題的優勢。

> [!NOTE]
> ASP.NET 分析工具診斷資料配接器會分析 Internet Information Services (IIS) 處理序， 因此不會針對開發 Web 伺服器執行。 若要在負載測試中分析網站，您必須在 IIS 執行所在的電腦上安裝測試代理程式。 測試代理程式不會產生負荷，只用於收集資料。 如需詳細資訊，請參閱[安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)。

如需詳細資訊，請參閱[如何：建立分散式負載測試的測試設定](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)。

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>針對測試設定來設定 ASP.NET 分析工具

執行這個程序中的步驟之前，您必須先從 Visual Studio 開啟測試設定，然後選取 [資料和診斷] 頁面。

1. 選取要用來收集 ASP.NET 分析工具資料的角色。

    > [!WARNING]
    > 這個角色必須是 Web 伺服器。

2. 選取 [ASP.NET 分析工具] 以啟用收集 ASP.NET 分析資料，然後選擇 [設定]。

     設定 ASP.NET 分析資料收集的對話方塊隨即顯示。

3. 在 [分析工具取樣間隔] 中鍵入值，指出 ASP.NET 分析取樣過程中，要等待的未暫止 CPU 時脈週期數。

4. 若要啟用階層互動分析，請選取 [啟用階層互動分析]。

     階層互動分析會計算針對每個成品 (例如 *MyPage.aspx* 或 *CompanyLogo.gif*) 傳送至網頁伺服器的要求數目，以及服務每個要求所需的時間。 此外，階層互動分析也會收集頁面要求進行時所使用的 ADO.NET 連線，以及在服務該要求時所執行的查詢和預存程序呼叫數目。

     收集兩組不同的計時資訊：

    - 服務每個 Web 要求的計時資訊 (最小值、最大值、平均和總計)。

    - 執行每個查詢的計時資訊 (最小值、最大值、平均和總計)。

在測試設定中設定 ASP.NET 分析工具診斷資料配接器之後，您現在可以對 ASP.NET Web 應用程式收集 ASP.NET 分析資料。

## <a name="see-also"></a>另請參閱

- [使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)
- [如何：建立分散式負載測試的測試設定](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [測試控制器和測試代理程式](configure-test-agents-and-controllers-for-load-tests.md)