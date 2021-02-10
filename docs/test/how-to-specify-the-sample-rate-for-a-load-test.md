---
title: 指定負載測試回合設定的取樣率
description: 瞭解如何使用負載測試編輯器在屬性視窗中編輯回合設定值的取樣率。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 7d591ad7cc97543f9167b698b0a5f0664e59b5c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962648"
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>如何：指定負載測試回合設定的採樣速率

使用 [新增負載測試精靈] 建立負載測試之後，您就可以使用 [負載測試編輯器]，將屬性變更為符合您的測試需求和目標。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

使用 [負載測試編輯器] 時，您可以在 [屬性] 視窗中編輯回合設定的 [採樣速率] 屬性值。 如需回合設定屬性及其描述的完整清單，請參閱[負載測試回合設定屬性](../test/load-test-run-settings-properties.md)。

請根據負載測試的長度，為負載測試回合設定選擇 [採樣速率] 屬性的適當值。 較小的取樣率 (例如五秒的預設值) 會在負載測試結果資料庫中佔用較多空間。 若為較長的負載測試，增加取樣率會降低您所收集的資料量。 如需詳細資訊，請參閱 [如何：指定負載測試回合設定的取樣率](../test/how-to-specify-the-sample-rate-for-a-load-test.md)。

下面是一些取樣率的方針：

|負載測試持續期間|建議取樣率|
|-|-----------------------------|
|\< 1 小時|5 秒|
|1 - 8 小時|15 秒|
|8 - 24 小時|30 秒|
|> 24 小時|60 秒|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>若要在回合設定中指定效能計數器取樣率

1. 開啟負載測試。

     [負載測試編輯器] 隨即出現。 負載測試樹狀結構隨即顯示。

2. 在負載測試樹狀目錄的 [回合設定] 資料夾中，選擇您要為其指定採樣速率的回合設定。

3. 在 [檢視] 功能表上，選取 [屬性視窗]。

     負載測試回合設定的分類和屬性會顯示在 [屬性] 視窗中。

4. 在 [採樣速率] 屬性中輸入時間值，表示負載測試將按此頻率收集效能計數器資料。

5. 屬性變更完成之後，選擇 [檔案] 功能表上的 [儲存]。 然後您就可以使用新的 [採樣速率] 值來執行負載測試。

## <a name="see-also"></a>另請參閱

- [設定負載測試回合設定](../test/configure-load-test-run-settings.md)
- [負載測試情節屬性](../test/load-test-scenario-properties.md)
