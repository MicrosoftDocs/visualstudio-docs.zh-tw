---
title: 設定負載測試回合設定
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ffc9d6c2e563fcd16a61e91eaa94889de8607efc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595978"
---
# <a name="configure-load-test-run-settings"></a>設定負載測試回合設定

「回合設定」** 是會影響負載測試執行方式的一組屬性。 這些設定會在 [屬性]**** 視窗中，依照分類進行組織。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

您可以在一個負載測試中擁有多個回合設定；不過，每個回合只能有其中一個回合設定在使用中。 其他的回合設定則會對後續的測試回合提供能夠快速選取替代設定的方法。

當您使用 [新增負載測試精靈]**** 來建立負載測試時，就會建立初始回合設定。

![負載測試回合設定](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>工作

|工作|相關主題|
|-|-|
|**向負載測試添加更多回合設定：** 除了運行 **"新負載測試精靈**"時創建的回合設定外，還可以向負載測試添加更多回合設定，以便在不同條件下運行測試。|-   [如何：向負載測試添加其他回合設定](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**指定要搭配負載測試使用的使用中回合設定：** 您可以使用 [負載測試編輯器] 來選取想要搭配負載測試使用的回合設定。 現用回合設定可由 "[Active]" 後置字元加以識別。|-   [如何：為負載測試選擇活動回合設定](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**編輯回合設定屬性：** 您可以編輯回合設定屬性，以便進行日誌記錄選項（見下文更多）、確定測試長度、預熱持續時間、報告的最大錯誤詳細資訊數、取樣速率、連接模型（僅限 Web 效能測試）、結果存儲類型、驗證級別和 SQL 追蹤。 回合設定應該反映負載測試的目標。|-   [載入測試回合設置屬性](../test/load-test-run-settings-properties.md)<br />-   [更改回合設定屬性](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**在負載測試回合設定中指定測試反覆運算計數：** 通過配置**測試反覆運算**屬性，可以指定在負載測試的所有方案中運行所有 Web 性能和單元測試的次數。|-   [如何：指定回合設定中的測試反覆運算次數](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**指定負載測試回合設定的採樣速率：** 您可以透過設定 [採樣速率]**** 屬性，指定負載測試收集效能計數器資料的頻率。|-   [如何：指定採樣速率](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**指定計時詳細資料儲存區選項：** 您可以透過設定 [計時詳細資料儲存區]**** 屬性，指定負載測試詳細資料的儲存方式。|-   [如何：指定時間詳細資訊存儲屬性](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**指定測試資源保留期間：** 藉由設定 [資源保留時間]**** 屬性，在指定的期間內保留測試資源，以加速測試 > 修正 > 重新測試的週期。|-   [保留資源以加速負載測試](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts)|
|**使用內容參數：** 您可以使用內容參數將字串參數化。 例如，如果您的負載測試含有使用參數型網頁伺服器的 Web 效能測試，您就可以將內容參數新增至對應不同伺服器的回合設定。|-   [如何：將內容參數新增至回合設定](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**設定測試記錄屬性：** 您可以設定系統將資料寫入與負載測試回合設定建立關聯之記錄檔的頻率。 當您要執行大型或複雜的負載測試時，這個屬性可能很重要，因為記錄檔可能會變成數個 GB。<br /><br /> 您也可以將記錄檔設定為在負載測試失敗時自動儲存，以便協助偵錯和分析應用程式。|-   [修改負載測試記錄設定](../test/modify-load-test-logging-settings.md)|
