---
title: 選取負載測試的回合設定
description: 負載測試可以包含「回合設定」，這是指會影響負載測試回合的屬性。 瞭解如何選取使用中的回合設定。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, active
ms.assetid: ed6ff546-acfa-4dd8-b3a2-6e7455930ca4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: c93c636d8321affead3c3fce6f3074801cb9ae87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882644"
---
# <a name="how-to-select-the-active-run-setting-for-a-load-test"></a>如何：選取負載測試的使用中回合設定

使用 [新增負載測試精靈] 建立負載測試之後，您就可以使用 [負載測試編輯器] 來變更情節屬性，以便符合您的測試需求和目標。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

負載測試可以包含一或多個「回合設定」，這是指一組會影響負載測試執行方式的屬性。 這些設定會在 [屬性] 視窗中，依照分類進行組織。 負載測試執行時，它會使用目前設為使用中的回合設定。

> [!NOTE]
> 如需回合設定屬性及其描述的完整清單，請參閱[負載測試回合設定屬性](../test/load-test-run-settings-properties.md)。

如果您的負載測試在 [回合設定] 資料夾下只有一個回合設定節點，該節點則一律為使用中的節點。 如果您的負載測試包含多個回合設定節點，則可以在執行負載測試時選取其中一個使用。 請參閱 [如何：將其他回合設定加入至負載測試](../test/how-to-add-additional-run-settings-to-a-load-test.md)。

在 [負載測試編輯器] 中，使用中的回合設定可由 "[Active]" 後置字元加以辨識。

## <a name="select-the-active-run-setting"></a>選取使用中的回合設定

1. 開啟負載測試。

2. 展開 [回合設定] 資料夾。

3. 以滑鼠右鍵按一下您要設為使用中節點的回合設定節點，然後選擇 [設定為使用中]。

     在 [負載測試編輯器] 中，受影響的回合設定節點會更新成含有 "[Active]" 後置字元。

     選取的回合設定即成為使用中，除非您選取要使用另一個回合設定，否則該設定會維持在使用中狀態。

> [!NOTE]
> 您可以透過設定名為 `Test.UseRunSetting=<run setting name>` 的環境變數，覆寫使用中的回合設定。 當您從命令列或批次 (Batch) 檔執行負載測試時，這種方法會很有用。 這可讓您在不用開啟負載測試的情況下，選擇不同的回合設定。

## <a name="specify-the-run-setting-to-use-from-the-command-line"></a>從命令列指定要使用的回合設定

從命令列設定環境變數，即可覆寫負載測試中的預設回合設定。

**Set Test.UseRunSetting=PreProdEnvironment**

若要執行測試：

**mstest /testcontainer:loadtest1.loadtest**

## <a name="see-also"></a>另請參閱

- [設定負載測試回合設定](../test/configure-load-test-run-settings.md)
- [在負載測試中指定電腦的計數器集合和臨界值規則](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [如何：將其他回合設定加入至負載測試](../test/how-to-add-additional-run-settings-to-a-load-test.md)
