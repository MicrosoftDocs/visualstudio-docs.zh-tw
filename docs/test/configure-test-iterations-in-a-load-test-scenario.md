---
title: 設定用於負載測試的測試反覆項目
description: 瞭解如何設定測試反復專案設定，以設定案例中的反復專案數目上限，以及它們之間暫停的時間長度。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, scenarios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5316b03220a094d3280aba3eb8c46f190a2874f
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442556"
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>在負載測試情節中設定測試反覆項目

若要進行測試反覆項目設定，請使用 [負載測試編輯器] 和 [屬性] 視窗以編輯負載測試情節。 根據預設，設定的負載測試情節中，不會指定測試反覆項目上限。 您可以選擇在情節中設定反覆項目數目的上限，以及反覆項目之間暫停的時間長度。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>針對情節指定測試反覆項目上限

您可以使用 [負載測試編輯器] 來變更 [屬性] 視窗中的 [測試反覆項目數目上限] 屬性，以指定要針對情節執行測試的次數上限。

[測試反覆項目數目上限] 屬性會控制要針對情節執行的測試反覆項目數目上限。 如同負載測試回合設定中的 [測試反覆項目] 屬性，這是用於所有代理程式上所有使用者的最大數目，而不是只針對每一個使用者設定。

> [!NOTE]
> 如需負載測試情節屬性及其描述的完整清單，請參閱 [負載測試情節屬性](../test/load-test-scenario-properties.md)。

對於循序測試混合，一個反覆項目就是經過混合中所有測試的項目。 對於所有其他測試混合，每一個測試執行都會計算為一個反覆項目。 如需詳細資訊，請參閱 [關於混合控制項](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)。

如果負載測試為持續期間負載測試，而持續期間會在反覆項目計數完成之前到期，則仍會停止測試。 如果測試為反覆項目型，而測試反覆項目在情節反覆項目之前就符合，則會停止測試。 您可以在與負載測試中的回合設定關聯的 [屬性] 視窗中，使用 [執行持續期間] 屬性來設定持續期間。

符合情節反覆項目計數時，情節會停止執行，但其他作用中情節會繼續執行。

> [!NOTE]
> 相關的屬性為 Web 測試資料來源上的 [唯一] 屬性，這個屬性會循序逐列移動資料，但每一筆記錄只移動一次。 如需詳細資訊，請參閱[將資料來源繫結至 Web 效能測試](../test/add-a-data-source-to-a-web-performance-test.md)。

[測試反覆項目數目上限 屬性可用於各種狀況。 有些負載測試人員偏好使用反覆項目測試，有些則偏好持續期間測試。

![在情節中指定測試反覆項目](../test/media/loadtest_prop.png)

### <a name="to-specify-the-maximum-test-iterations"></a>若要指定測試反覆項目上限

1. 開啟負載測試。

2. [負載測試編輯器] 隨即出現。 負載測試樹狀結構隨即顯示。

3. 在負載測試樹狀目錄的 [情節] 資料夾中，選擇您要對其指定測試反覆項目數上限的情節節點。

4. 在 [檢視] 功能表上，選取 [屬性視窗]。

     情節的分類和屬性會顯示在 [屬性] 視窗中。

5. 在 [測試反覆項目數目上限] 屬性的文字方塊中，鍵入值以指出執行負載測試時，要針對情節執行測試的次數上限。

    > [!NOTE]
    > 對 [測試反覆項目數目上限] 屬性使用值 0，表示沒有反覆項目上限。

6. 屬性變更完成之後，選擇 [檔案] 功能表上的 [儲存]。 然後，您就可以使用新的 [測試反覆項目數目上限] 值來執行負載測試。

## <a name="specify-think-times-between-test-iterations-for-a-scenario"></a>為情節指定測試反覆項目間的考慮時間

[測試反覆項目間的考慮時間] 屬性是在 [負載測試編輯器] 中編輯負載測試情節屬性時，使用 [屬性] 視窗設定的屬性。

[測試反覆項目間的考慮時間] 屬性是用來指定啟動測試反覆項目之前的等候秒數。

> [!NOTE]
> 如需負載測試情節屬性及其描述的完整清單，請參閱 [負載測試情節屬性](../test/load-test-scenario-properties.md)。

### <a name="to-specify-the-think-time-between-test-iterations"></a>指定測試反覆項目間的考慮時間

1. 開啟負載測試。

     [負載測試編輯器] 隨即出現。 負載測試樹狀結構隨即顯示。

2. 在負載測試樹狀目錄的 [情節] 資料夾中，選擇您要為其指定考慮時間的情節節點。

3. 在 [檢視] 功能表上，選取 [屬性視窗]。

     情節的分類和屬性會顯示在 [屬性] 視窗中。

4. 在 [測試反覆項目間的考慮時間] 屬性值中，輸入數字，代表啟動下一個測試反覆項目之前的等候秒數。

5. 屬性變更完成之後，選擇 [檔案] 功能表上的 [儲存]。 然後，您就可以使用新的 [測試反覆項目間的考慮時間] 值來執行負載測試。

## <a name="see-also"></a>另請參閱

- [編輯負載測試情節](../test/edit-load-test-scenarios.md)
- [設定用於負載測試的測試代理程式和測試控制器](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [負載測試情節屬性](../test/load-test-scenario-properties.md)
- [編輯考慮時間以模擬網站人類互動延遲](../test/edit-think-times-in-load-test-scenarios.md)
