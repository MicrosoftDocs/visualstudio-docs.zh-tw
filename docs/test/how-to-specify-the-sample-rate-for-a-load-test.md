---
title: HOW TO：指定負載測試回合設定的採樣速率
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: b022b4648931bf0e403df589d37cb086fb2a9c2c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053045"
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>HOW TO：指定負載測試回合設定的採樣速率

使用 [新增負載測試精靈] 建立負載測試之後，您就可以使用 [負載測試編輯器]，將屬性變更為符合您的測試需求和目標。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

使用 [負載測試編輯器] 時，您可以在 [屬性] 視窗中編輯回合設定的 [採樣速率] 屬性值。 如需回合設定屬性及其描述的完整清單，請參閱[負載測試回合設定屬性](../test/load-test-run-settings-properties.md)。

請根據負載測試的長度，為負載測試回合設定選擇 [採樣速率] 屬性的適當值。 較小的取樣率 (例如五秒的預設值) 會在負載測試結果資料庫中佔用較多空間。 若為較長的負載測試，增加取樣率會降低您所收集的資料量。 如需詳細資訊，請參閱[＜How to：指定負載測試回合設定的採樣速率](../test/how-to-specify-the-sample-rate-for-a-load-test.md)。

下面是一些取樣率的方針：

|負載測試持續期間|建議取樣率|
|-|-----------------------------|
|\< 1 小時|5 秒|
|1 - 8 小時|15 秒|
|8 - 24 小時|30 秒|
|> 24 小時|60 秒|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>若要在回合設定中指定效能計數器取樣率

1.  開啟負載測試。

     [負載測試編輯器] 隨即出現。 負載測試樹狀隨即顯示。

2.  在負載測試樹狀目錄的 [回合設定] 資料夾中，選擇您要為其指定採樣速率的回合設定。

3.  在 [檢視] 功能表上，選取 [屬性視窗]。

     負載測試回合設定的分類和屬性會顯示在 [屬性] 視窗中。

4.  在 [採樣速率] 屬性中輸入時間值，表示負載測試將按此頻率收集效能計數器資料。

5.  屬性變更完成之後，選擇 [檔案] 功能表上的 [儲存]。 然後您就可以使用新的 [採樣速率] 值來執行負載測試。

## <a name="see-also"></a>另請參閱

- [設定負載測試回合設定](../test/configure-load-test-run-settings.md)
- [負載測試情節屬性](../test/load-test-scenario-properties.md)