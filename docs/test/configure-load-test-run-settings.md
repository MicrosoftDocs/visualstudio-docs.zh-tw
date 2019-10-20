---
title: 設定負載測試回合設定
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 35da7997e5a0e3260064e6f3de7ac4f9e0740fa4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665228"
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
|**將其他回合設定新增至負載測試：** 除了執行 [新增負載測試精靈] 時所建立的回合設定以外，您還可以將其他回合設定新增至負載測試，以便在不同的狀況下執行測試。|-   [如何：將其他回合設定新增至負載測試](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**指定要搭配負載測試使用的使用中回合設定：** 您可以使用 [負載測試編輯器] 來選取想要搭配負載測試使用的回合設定。 現用回合設定可由 "[Active]" 後置字元加以識別。|-   [如何：選取負載測試的使用中回合設定](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**編輯回合設定屬性：** 您可以針對記錄選項等項目編輯回合設定屬性 (詳情請參閱下面)，以便決定測試的長度、準備持續期間、所回報錯誤詳細資料的數目上限、取樣率、連接模型 (僅限 Web 效能測試)、結果儲存類型、驗證層級，以及 SQL 追蹤。 回合設定應該反映負載測試的目標。|-   [負載測試回合設定屬性](../test/load-test-run-settings-properties.md)<br />-   [變更回合設定屬性](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**在負載測試回合設定中指定測試反覆項目計數：** 您可以透過設定 [測試反覆項目] 屬性，指定要在所有負載測試情節中執行所有 Web 效能測試和單元測試的次數。|-   [如何：在回合設定中指定測試反覆項目的數目](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**指定負載測試回合設定的採樣速率：** 您可以透過設定 [採樣速率] 屬性，指定負載測試收集效能計數器資料的頻率。|-   [如何：指定採樣速率](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**指定計時詳細資料儲存區選項：** 您可以透過設定 [計時詳細資料儲存區] 屬性，指定負載測試詳細資料的儲存方式。|-   [如何：指定計時詳細資料儲存區屬性](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**指定測試資源保留期間：** 藉由設定 [資源保留時間] 屬性，在指定的期間內保留測試資源，以加速測試 > 修正 > 重新測試的週期。|-   [保留資源以加速負載測試](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts)|
|**使用內容參數：** 您可以使用內容參數將字串參數化。 例如，如果您的負載測試含有使用參數型網頁伺服器的 Web 效能測試，您就可以將內容參數新增至對應不同伺服器的回合設定。|-   [如何：將內容參數新增至回合設定](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**設定測試記錄屬性：** 您可以設定系統將資料寫入與負載測試回合設定建立關聯之記錄檔的頻率。 當您要執行大型或複雜的負載測試時，這個屬性可能很重要，因為記錄檔可能會變成數個 GB。<br /><br /> 您也可以將記錄檔設定為在負載測試失敗時自動儲存，以便協助偵錯和分析應用程式。|-   [修改負載測試記錄設定](../test/modify-load-test-logging-settings.md)|