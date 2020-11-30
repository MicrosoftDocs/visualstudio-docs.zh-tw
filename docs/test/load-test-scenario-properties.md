---
title: 負載測試情節屬性
description: 瞭解如何將 Visual Studio 中的負載測試情節屬性設定變更為本文中的其中一個不同的負載測試情節屬性。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 263a3a1f928fe42d1f5b910f82d0d4a6ea24412e
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328804"
---
# <a name="load-test-scenario-properties"></a>負載測試情節屬性

在 Visual Studio 中變更您的負載測試情節屬性設定，以符合測試需求。 本文會依分類列出各種不同的負載測試情節屬性。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="general"></a>一般

|屬性|定義|
|-|----------------|
|**名稱**|情節的名稱。|

## <a name="mix"></a>混合

|屬性|定義|
|-|----------------|
|**瀏覽器混合**|為負載測試指定網頁瀏覽器混合。 您可以指定不同的網頁瀏覽器類型及其負載分佈。<br /><br />選擇省略符號 **(…)** 按鈕開啟 [編輯瀏覽器混合] 對話方塊，並使用 [新增] 和 [移除] 選取負載測試中的網頁瀏覽器類型。<br /><br />如需詳細資訊，請參閱[指定網頁瀏覽器類型](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)。|
|**網路混合**|為負載測試指定網路混合。 您可以指定要包含哪些網路類型及其負載分佈。<br /><br />選擇省略符號 **(…)** 按鈕開啟 [編輯網路混合] 對話方塊，並使用 [新增] 和 [移除] 選取負載測試中的網路類型。<br /><br />如需詳細資訊，請參閱[指定虛擬網路類型](../test/specify-virtual-network-types-in-a-load-test-scenario.md)。|
|**測試混合**|為負載測試指定 Web 效能和單元測試混合。 您可以指定要包含哪些測試及其負載分佈。<br /><br />選擇省略符號 **(…)** 按鈕開啟 [編輯測試混合] 對話方塊，並使用 [新增] 和 [移除] 選取負載測試中的測試。<br /><br />如需詳細資訊，請參閱[編輯負載測試情節的測試混合](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)。|
|**測試混合類型**|指定負載測試的測試混合模型。<br /><br />選擇省略符號 **(…)** 按鈕開啟 [編輯測試混合] 對話方塊，並使用 [測試混合模型] 底下的下拉式清單選取要用於負載測試的測試混合模型。<br /><br />如需詳細資訊，請參閱[編輯測試混合模型](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)。|

## <a name="options"></a>選項

|屬性|定義|
|-|----------------|
|**要使用的代理程式**|如果要從遠端執行負載測試，請指定情節要使用的代理程式。 例如，您可以指定特定一組代理程式，以便在分析效能趨勢時維持一致性。 另外，代理程式也可以分散在不同的地理位置，讓代理程式執行的指令碼更親近於代理程式所在地。<br /><br />多個代理程式必須以逗號分隔，例如 "**Agent1, Agent2, Agent3**"。 將這個屬性保留空白，即指定情節應該使用所有可用的代理程式。<br /><br />如需詳細資訊，請參閱[如何：指定要使用的測試代理程式](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)。|
|**將分佈套用到步調延遲**|布林值，用來指定是否要在使用者步調測試混合模型中套用一般分佈延遲。 這個屬性只有在 [測試混合類型] 屬性設定為 [按使用者步調] 時才適用。<br /><br />如需詳細資訊，請參閱[如何：將分佈套用到步調延遲](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|
|**IP 切換**|布林值，用來指定是否要使用 IP 切換。<br /><br />IP 切換可讓測試代理程式利用某個不同 IP 位址的範圍，將要求傳送至伺服器。 這會模擬來自不同用戶端電腦的呼叫。 當您對負載平衡 Web 伺服陣列進行測試時，IP 切換很重要。 大多數的負載平衡器會使用用戶端的 IP 位址，將用戶端導引到特定的 Web 伺服器。 如果所有的要求似乎都來自單一用戶端，負載平衡器將不會平衡負載。 若要在 Web 伺服陣列中獲得較佳的負載平衡，讓要求都來自某一範圍的 IP 位址非常重要。<br /><br />IP 切換僅適用於測試代理程式。|
|**測試反覆項目數目上限**|數值，用來指定情節中要執行的測試數目上限。 0 值指定沒有上限。<br /><br />如需詳細資訊，請參閱[設定情節的測試反覆項目](../test/configure-test-iterations-in-a-load-test-scenario.md)。|
|**新使用者的百分比**|數值，指定情節中新使用者或初次造訪者的百分比。<br /><br />如需詳細資訊，請參閱[如何：指定使用 Web 快取資料之虛擬使用者的百分比](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)。|
|**考慮分析**|指定情節是否會使用 [常態分佈]，或考慮特性是 [開啟] 或 [關閉]。<br /><br />如需詳細資訊，請參閱[編輯考慮時間以模擬網站人類互動延遲](../test/edit-think-times-in-load-test-scenarios.md)。|

## <a name="timing"></a>計時

|屬性|定義|
|-|----------------|
|**延遲開始時間**|時間值，表示在負載測試啟動之後，情節啟動時延遲的小時、分鐘和秒數。 如果 [熱身期間停用] 屬性設定為 [True]，則等候時間量會在熱身期間後套用。<br /><br />如需詳細資訊，請參閱[設定情節開始延遲](../test/configure-scenario-start-delays.md)。|
|**熱身期間停用**|布林值，用來指定在負載測試回合設定中所指定的 [準備持續期間] 屬性時間值期間，情節是否應該執行。<br /><br />如需負載測試回合設定屬性的詳細資訊，請參閱[負載測試回合設定屬性](../test/load-test-run-settings-properties.md)。<br /><br />如需詳細資訊，請參閱[設定情節開始延遲](../test/configure-scenario-start-delays.md)。|
|**測試反覆項目間的考慮時間**|數值，用來指定測試反覆項目間的等候時間 (以秒為單位)。<br /><br />如需詳細資訊，請參閱[編輯考慮時間以模擬網站人類互動延遲](../test/edit-think-times-in-load-test-scenarios.md)。|

## <a name="see-also"></a>另請參閱

- [編輯負載測試情節](../test/edit-load-test-scenarios.md)
