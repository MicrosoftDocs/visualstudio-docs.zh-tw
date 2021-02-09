---
title: 設定負載測試回合設定
description: 瞭解回合設定，這是影響負載測試執行方式的屬性。 這些設定會在 [屬性] 視窗中，依照分類進行組織。
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: a606f2cb9547250db79de9defba57dc95a402bf1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868084"
---
# <a name="configure-load-test-run-settings"></a>設定負載測試回合設定

「回合設定」是會影響負載測試執行方式的一組屬性。 這些設定會在 [屬性] 視窗中，依照分類進行組織。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

您可以在一個負載測試中擁有多個回合設定；不過，每個回合只能有其中一個回合設定在使用中。 其他的回合設定則會對後續的測試回合提供能夠快速選取替代設定的方法。

當您使用 [新增負載測試精靈] 來建立負載測試時，就會建立初始回合設定。

![負載測試回合設定](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>工作

|工作|相關主題|
|-|-|
|**將其他回合設定新增至負載測試：** 除了執行 **新負載測試精靈** 時所建立的回合設定以外，您還可以將其他回合設定加入至負載測試，以便在不同的狀況下執行測試。|-   [如何：將其他回合設定加入至負載測試](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**指定要搭配負載測試使用的使用中回合設定：** 您可以使用 [負載測試編輯器] 來選取想要搭配負載測試使用的回合設定。 現用回合設定可由 "[Active]" 後置字元加以識別。|-   [如何：選取負載測試的使用中回合設定](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**編輯回合設定屬性：** 您可以針對記錄選項來編輯回合設定屬性， (查看以下) 、判斷測試的長度、準備持續期間、報告的錯誤詳細資料詳細資料、取樣率、連接模型 (的 web 效能測試) 、結果儲存類型、驗證層級和 SQL 追蹤。 回合設定應該反映負載測試的目標。|-   [負載測試回合設定屬性](../test/load-test-run-settings-properties.md)<br />-   [變更回合設定屬性](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**在負載測試回合設定中指定測試反復專案計數：** 您可以設定 [ **測試** 反復專案] 屬性，以指定在負載測試的所有案例中，執行所有 web 效能和單元測試的次數。|-   [如何：在回合設定中指定測試反復專案的數目](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**指定負載測試回合設定的採樣速率：** 您可以透過設定 [採樣速率] 屬性，指定負載測試收集效能計數器資料的頻率。|-   [如何：指定採樣速率](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**指定計時詳細資料儲存區選項：** 您可以透過設定 [計時詳細資料儲存區] 屬性，指定負載測試詳細資料的儲存方式。|-   [如何：指定計時詳細資料儲存區屬性](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**指定測試資源保留期間：** 藉由設定 [資源保留時間] 屬性，在指定的期間內保留測試資源，以加速測試 > 修正 > 重新測試的週期。|-   [保留資源以加速負載測試](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts&preserve-view=true)|
|**使用內容參數：** 您可以使用內容參數將字串參數化。 例如，如果您的負載測試含有使用參數型網頁伺服器的 Web 效能測試，您就可以將內容參數新增至對應不同伺服器的回合設定。|-   [如何：將內容參數新增至回合設定](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**設定測試記錄屬性：** 您可以設定系統將資料寫入與負載測試回合設定建立關聯之記錄檔的頻率。 當您要執行大型或複雜的負載測試時，這個屬性可能很重要，因為記錄檔可能會變成數個 GB。<br /><br /> 您也可以將記錄檔設定為在負載測試失敗時自動儲存，以便協助偵錯和分析應用程式。|-   [修改負載測試記錄設定](../test/modify-load-test-logging-settings.md)|