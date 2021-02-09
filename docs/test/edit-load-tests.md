---
title: 編輯負載測試
description: 瞭解用來定義負載測試的案例、計數器集合和回合設定之間的差異。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: ad79be0850191cd2e7ab28aa7a30ff10d867b271
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887870"
---
# <a name="edit-load-tests"></a>編輯負載測試

負載測試可執行 Web 效能測試或單元測試，以模擬同時存取某部伺服器的多位使用者。 負載測試可讓您獲得應用程式壓力和效能資料。 負載測試可設定為模擬各種負載狀況，例如使用者負載和網路類型。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

負載測試是由「情節」、「計數器集合」和「回合設定」定義。 下圖說明[情節](../test/edit-load-test-scenarios.md)、[計數器集合](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)和[回合設定](../test/load-test-run-settings-properties.md)之間的差異：

![負載測試架構](../test/media/load_test_editor.png)

## <a name="software-requirements"></a>軟體需求

只有 Visual Studio Enterprise 版中可以使用 Web 效能和負載測試專案。

## <a name="edit-load-test-scenario-settings"></a>編輯負載測試情節設定

情節是用來建立一組使用者如何與伺服器應用程式互動的模型。 情節是由負載模式、測試混合模型、測試混合、瀏覽器混合和網路混合所組成。 負載測試可以包含一個以上的情節，而單一情節可以包含 Web 效能測試和單元測試。 藉由將類似的設定組成群組，情節可讓您將具有類似性質的測試組成群組，並且一起執行。

如需詳細資訊，請參閱[編輯負載測試情節](../test/edit-load-test-scenarios.md)和[負載測試情節屬性](../test/load-test-scenario-properties.md)。

## <a name="configure-and-manage-performance-counter-sets"></a>設定和管理效能計數器集合

負載測試會提供依技術所組織的具名計數器集合，在分析效能計數器資料時，非常好用。 計數器集合包括負載測試、IIS、ASP.NET 和 SQL。 當您使用 [新增負載測試精靈] 建立負載測試時，會為您指定要包含在負載測試中的電腦，設定好一組初始預先定義的重要計數器。 請在 [負載測試編輯器] 中管理計數器。

如需詳細資訊，請參閱[在負載測試中指定電腦的計數器集合和臨界值規則](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)。

## <a name="configure-and-manage-load-test-run-settings"></a>設定和管理負載測試回合設定

回合設定是影響負載測試執行方式的屬性， 這些設定會在 [屬性] 視窗中，依照分類進行組織。

如需詳細資訊，請參閱[設定負載測試回合設定](../test/configure-load-test-run-settings.md)和[負載測試回合設定屬性](../test/load-test-run-settings-properties.md)。

## <a name="see-also"></a>另請參閱

- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [分析臨界值規則違規](../test/analyze-threshold-rule-violations-in-load-tests.md)
