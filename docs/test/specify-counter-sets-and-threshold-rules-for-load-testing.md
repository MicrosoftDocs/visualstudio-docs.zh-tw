---
title: 用於負載測試的計數器集合與臨界值規則
description: 瞭解如何在負載測試中指定計數器集合和臨界值規則。 將受測伺服器新增至要收集計數器的電腦清單。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- load tests, thresholds
- counter sets
- load tests, performance
- load tests, counter sets
- load tests, threshold rules
ms.assetid: 9e14d955-f3a4-4717-bbfe-7f08cdda5678
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 04348eb2d88c560e9687c687486e6b44d8394371
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328947"
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>在負載測試中指定電腦的計數器集合與臨界值規則

負載測試提供具名計數器集合，這些在分析效能計數器資料時非常好用。 這些計數器集合會依技術加以組織，並且包含 [應用程式]、[ASP.NET]、[.NET 應用程式]、[IIS] 和 [SQL]。 當您使用 [新增負載測試精靈] 建立負載測試時，您會新增初始的計數器集合。 這些都會為您的負載測試提供一組預先定義且重要的計數器集合。 請在 [負載測試編輯器] 中管理計數器。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> 如果您的負載測試已分配給遠端電腦，控制器和代理程式計數器就會對應至控制器和代理程式計數器集合。 如需如何在負載測試中使用遠端電腦的詳細資訊，請參閱[測試控制器和測試代理程式](configure-test-agents-and-controllers-for-load-tests.md)。

計數器集合是在您指定的電腦上收集而來的。 計數器集合與執行負載測試期間所使用之電腦間的關聯為「計數器集合對應」。 例如，您所測試的 Web 伺服器可能具有 ASP.NET、IIS 和 .NET 應用程式計數器集合對應。

根據預設，效能計數器是在控制器和代理程式上收集的。 如需詳細資訊，請參閱 [測試控制器和測試代理](configure-test-agents-and-controllers-for-load-tests.md)程式。

因此，請務必將受測試的伺服器加入至收集計數器的電腦清單中。 如此，就可以在執行負載測試期間收集並監視任何重要的系統資料。

## <a name="tasks"></a>工作

|工作|相關主題|
|-|-----------------------|
|**管理負載測試的計數器集合：** 建立負載測試之後，您就可以在 [負載測試編輯器] 中編輯 [計數器集合]。 對應計數器集合包含選擇您要從中收集效能資料的電腦集合，並指派一組計數器集合收集每一部個別電腦。 您可以在 [負載測試編輯器] 中管理計數器。|-   [如何：管理計數器集合](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**將計數器集合新增至負載測試：** 當您使用 [新增負載測試精靈] 建立負載測試時，可以新增初始的計數器集合。 這些都會為您的負載測試提供一組預先定義的計數器集合。 當您建立負載測試之後，您可以使用 [負載測試編輯器] 將新的計數器加入至現有的計數器集合。|-   [如何：將計數器新增至計數器集合](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [如何：新增自訂計數器集合](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**為負載測試指定使用計數器的臨界值規則：** 臨界值規則是設定在單獨之效能計數器上的規則，用來監視負載測試期間的系統資源使用狀況。 計數器集合定義包含許多關鍵效能計數器之預先定義的臨界值規則。 負載測試中的臨界值規則會將效能計數器值與常數值或其他效能計數器值做比較。|-   [如何：新增臨界值規則](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**為計數器集合對應的電腦指派易記名稱：** 您可以新增電腦標記，讓您將容易辨認的名稱套用至電腦。 這些標記會顯示在 [負載測試編輯器] 樹狀目錄的 [計數器集合對應] 節點中。 更重要的是，這些標記會顯示在 Excel 報表中，可協助專案關係人識別電腦在負載測試中扮演的角色，例如 "Web Server1 in lab2" 或 "SQL Server2 in Phoenix office"。<br /><br /> 如需詳細資訊，請參閱[針對測試比較或趨勢分析報告負載測試結果](../test/compare-load-test-results.md)。||

## <a name="use-counter-sets"></a>使用計數器集合

負載測試工具會持續利用計數器收集效能資料，並以圖形來表示這些資料。 在執行負載測試期間，計數器資料是依照使用者定義間隔收集的。 如需詳細資訊，請參閱[如何：指定採樣速率](../test/how-to-specify-the-sample-rate-for-a-load-test.md)。 您可以使用「負載測試分析器」在執行階段檢視計數器，或在負載測試回合之後檢視。

計數器資料是在伺服器和任何執行測試的電腦上收集而來的。 如果您已經設定了一組要執行測試的代理程式電腦，則也會在那些電腦上收集計數器。

共有三種計數器類別：百分比、計數和平均， 例如 CPU 使用比例、SQL Server 鎖定計數和每秒的 IIS 要求。

![負載測試計數器集合](../test/media/loadtestcountersets.png)

執行測試的電腦會報告個別 HTTP 要求的效能資料。 例如，代理程式電腦。 對於要求，您可以監視諸如收到第一個位元組的平均時間、回應時間和每秒要求數等資料。

為了讓您輕鬆收集 Web 伺服器上的效能資料，Visual Studio Enterprise 也以負載測試中使用的技術做為基礎，提供了預先定義的具名計數器集合。 當您分析執行 IIS、ASP.NET 或 SQL Server 的伺服器時，這些集合會有所幫助。 至於預設計數器集合中未提供的計數器，則可以利用負載測試編輯器來新增。 請務必將受測試的電腦或伺服器加入至負載測試，以確保您可以監視這些電腦上的資源使用情況。 如需詳細資訊，請參閱[如何：管理計數器集合](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)。

為了了解要收集哪些資料、在何處設定臨界值規則，以及如何在度量反映應用程式中的特定問題時發出通知，負載回合的結果分析通常需要特定的定義域知識。 如需詳細資訊，請參閱[關於臨界值規則](#about-threshold-rules)。

### <a name="performance-counter-sampling-interval-considerations"></a>效能計數器取樣間隔考量

根據負載測試的長度，為負載測試回合設定中的 [採樣速率] 屬性選取適當的值。 較小的取樣率 (例如五秒的預設值) 會在負載測試結果資料庫中佔用較多空間。 若為較長的負載測試，增加取樣率會降低所收集的資料量。 如需詳細資訊，請參閱[如何：指定採樣速率](../test/how-to-specify-the-sample-rate-for-a-load-test.md)。

以下是一些取樣率的方針。

|負載測試持續期間|建議取樣率|
|-|-----------------------------|
|\< 1 小時|5 秒|
|1 - 8 小時|15 秒|
|8 - 24 小時|30 秒|
|> 24 小時|60 秒|

## <a name="store-performance-data"></a>儲存效能資料

在負載測試回合期間，會收集效能計數器資料，並將資料儲存在「負載測試結果儲存機制」中。 如需詳細資訊，請參閱[管理負載測試結果存放庫中的負載測試結果](../test/manage-load-test-results-in-the-load-test-results-repository.md)。

## <a name="about-threshold-rules"></a>關於臨界值規則

「臨界值規則」是設定在單獨之效能計數器上的規則，用來監視負載測試期間的系統資源使用狀況。 計數器集合定義包含許多關鍵效能計數器之預先定義的臨界值規則。 如需詳細資訊，請參閱[使用計數器集合協助分析負載測試中的效能計數器資料](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)。

## <a name="threshold-rules-and-levels"></a>臨界值規則與層級

當您在負載測試中建立臨界值規則時，可以在兩種規則之間選擇：

比較常數&mdash;比較效能計數器值與常數值。

比較計數器&mdash;比較某個效能計數器值與另一個效能計數器值。

當您建立臨界值規則時，也同時設定了規則的層級。 層級有警告臨界值和嚴重臨界值。 當您檢視負載測試回合時，警告層級的臨界值違規會以黃色符號表示，而嚴重層級的臨界值違規則會以紅色符號表示。

## <a name="the-alert-if-over-property"></a>超出時提醒屬性

將 [超出時提醒] 屬性設定為 [True]，表示超過臨界值會是一個問題。 例如，如果臨界值規則設定在 [% 處理器時間]，而且您希望值超過 90 時獲得警示，請使用 [比較常數] 規則類型，將 [關鍵臨界值] 設定為 90，並將 [超出時提醒] 設定為 [True]。

將 [超出時提醒] 屬性設定為 [False]，表示未達臨界值會是一個問題。 例如，如果臨界值規則設定在 [要求/秒]，而且您希望值低於 50 時獲得警示，請使用 [比較常數] 規則類型，將 [關鍵臨界值] 設定為 50，並將 [超出時提醒] 設定為 [False]。

## <a name="see-also"></a>另請參閱

- [如何：新增臨界值規則](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [分析臨界值規則違規](../test/analyze-threshold-rule-violations-in-load-tests.md)
