---
title: 將回合設定新增至負載測試
description: 瞭解如何使用負載測試的其他設定，包括測試的持續時間、結果集合詳細資料層級，以及所收集的計數器集合。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, adding
- load tests, run settings
ms.assetid: 257d2a24-d582-4cfe-8b2b-51f51ba9cc84
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 5a7077442b3b823423edc09284c59979cc98a6d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908636"
---
# <a name="how-to-add-additional-run-settings-to-a-load-test"></a>如何：將其他回合設定新增至負載測試

負載測試的回合設定會決定各種其他設定。 這些設定包括測試的持續期間、結果收集詳細層級，以及在測試執行時所收集的計數器集合。 您可以針對每個負載測試建立和儲存多個回合設定，然後在執行測試時選取一個特定的設定。 當您使用 [新增負載測試精靈] 來建立負載測試時，就會將初始回合設定加入至負載測試。

您可以使用不同的屬性設定，將其他回合設定加入至負載測試，以便在不同的狀況下執行負載測試。 例如，您可以加入新的測試設定並且使用不同的取樣率，或指定較長的執行持續期間。 您一次只能使用一個回合設定，而且必須指定要使用的回合設定 (將它標記為使用中)。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-another-run-setting"></a>若要加入其他回合設定

1. 開啟負載測試。

2. (選擇性) 展開 [回合設定] 資料夾。

3. 以滑鼠右鍵按一下 [回合設定] 資料夾，然後選取 [新增回合設定]。

     新的回合設定即會新增至 [回合設定] 資料夾。

4. 在 [檢視] 功能表上選擇 [屬性視窗]。

     [屬性視窗] 隨即顯示，並顯示選取之回合設定的屬性。

5. 在 [屬性] 視窗中，使用 [名稱] 屬性的文字方塊來提供新回合設定的名稱，此名稱描述回合設定的目的 (例如，**回合設定：執行五分鐘**)。

6. 使用 [ **屬性** ] 視窗來變更回合設定。 例如，將執行持續期間變更為 [00:05:00] 以執行測試五分鐘。

    > [!NOTE]
    > 如需回合設定屬性及其描述的完整清單，請參閱[負載測試回合設定屬性](../test/load-test-run-settings-properties.md)。

     您現在可以指定想要使用加入的回合設定 (將它設定為使用中)。 如需詳細資訊，請參閱[如何：選取負載測試的使用中回合設定](../test/how-to-select-the-active-run-setting-for-a-load-test.md)。

## <a name="see-also"></a>另請參閱

- [設定負載測試回合設定](../test/configure-load-test-run-settings.md)
- [在負載測試中指定電腦的計數器集合和臨界值規則](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
