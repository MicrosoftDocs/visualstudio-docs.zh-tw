---
title: 負載測試情節
description: 瞭解如何編輯負載測試情節，讓您能夠設定測試來模擬複雜、實際的工作負載。
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, user activities
- load tests, modeling scenarios
ms.assetid: fec04f2e-bf38-4d44-b2ec-fa50f58fd0d9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 01129ae017dd51a6bc36d966a495eb7fd1afd2f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926894"
---
# <a name="edit-load-test-scenarios"></a>編輯負載測試情節

負載測試「情節」可指定負載模式、測試混合、瀏覽器混合和網路混合。 這些情節很重要，因為它們可讓您設定測試來模擬複雜且真實的工作負載。

例如，您可能針對數以百計的客戶同時透過許多連接速度，並且使用不同瀏覽器連接至具有網際網路前端之電子商務網站進行測試。 相同的網站也可能具有系統管理功能，內部員工會利用這些系統管理功能更新產品資訊和檢視統計資料。 這些內部使用者通常會使用相同的瀏覽器和高速的 LAN 連線存取網站。 您可以將這兩個不同使用者群組的屬性封裝成不同的情節。 每個情節都包含虛擬使用者類型。 在這種情況下，您可以使用一個負載測試情節來代表虛擬客戶，並使用另一個情節來代表網站的虛擬內部使用者。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="scenario-components"></a>情節元件

在建立負載測試時所指定的任何初始組態選項及設定，都可以稍後於 [負載測試編輯器] 中修改。 您也可以在負載測試中新增情節、回合設定和計數器集合。

![負載測試情節](../test/media/loadtesteditinscenarios.png)

情節包含下列元件：

|詞彙|定義|
|-|-|
|瀏覽器混合|模擬虛擬使用者透過各種網頁瀏覽器存取網站。|
|負載模式|指定可在負載測試期間使用的虛擬使用者數目，以及啟動新使用者的比例。 例如，逐步執行、常數和以目標為依據。|
|測試混合模型|指定虛擬使用者在負載測試情節中執行指定之測試的可能性。 例如：20% 的機會執行 TestA，以及 80% 的機會執行 TestB。 測試混合模型必須反映特定情節之測試的目標。|
|測試混合|測試混合是構成情節之 Web 效能和單元測試的選擇，而且是那些測試在情節中的分佈方式。|
|網路混合|模擬虛擬使用者透過各種網路連線存取網站。 網路混合提供了 LAN、纜線數據機和其他選項。|

情節有幾個其他屬性，您可以使用 [負載測試編輯器] 加以編輯。 如需詳細資訊，請參閱[負載測試情節屬性](../test/load-test-scenario-properties.md)。

## <a name="tasks"></a>工作

|工作|相關主題|
|-|-----------------------|
|**在情節中新增人工互動暫停：** 考慮時間是用來模擬造成人們在與網站互動時必須等待的人類行為。 考慮時間會發生在 Web 效能測試的各個要求之間，以及負載情節中各個測試反覆項目之間。 在負載測試中使用考慮時間，有助於建立更精確的負載模擬。|-   [編輯考慮時間以模擬網站人類互動延遲](../test/edit-think-times-in-load-test-scenarios.md)|
|**為情節指定虛擬使用者數目：** 您可以設定負載模式屬性，以指定在負載測試期間調整模擬使用者負載的方式。 您可取得三種內建的負載模式：常數、逐步執行和以目標為依據。 請根據您的負載測試目標，選擇負載模式並將屬性調整為適當的層級。|-   [編輯負載模式以模型化虛擬使用者活動](../test/edit-load-patterns-to-model-virtual-user-activities.md)|
|**設定虛擬使用者在情節中執行測試的可能性：** 您可以使用測試混合，以指定虛擬使用者在負載測試情節中執行指定測試的可能性。 這可讓您更寫實地模擬負載。 您能夠擁有數個工作流程 (而不是整個應用程式中只有一個工作流程)，這可以更貼切地呈現使用者與應用程式互動的方式。|-   [編輯測試混合模型](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)|
|**在負載測試情節中新增或移除 Web 效能或單元測試：** 您可以從情節的負載測試中新增或移除 Web 效能或單元測試。 負載測試包含一個或多個「情節」(Scenario)，其中每個情節都包含一個或多個 Web 效能或單元測試。|-   [編輯測試混合](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**為情節設定想要的網路混合：** 在負載測試情節中使用網路混合，可讓您模擬更真實的網路負載。 負載是以網路類型的異質混合，而非使用單一網路類型所產生。 您會更貼切地呈現使用者與應用程式的互動方式。 網路混合模型應該反映出該情節的目標。|-   [指定虛擬網路類型](../test/specify-virtual-network-types-in-a-load-test-scenario.md)|
|**為情節選取適當的網頁瀏覽器混合：** 在負載測試情節中使用瀏覽器混合，可讓您模擬更真實的 Web 負載。 負載會由瀏覽器的異質性混合，而非只是以單一的瀏覽器來產生。 您會建立將於應用程式中使用之瀏覽器的極為近似混合。|-   [指定網頁瀏覽器類型](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**設定情節的測試反覆項目設定：** 您可以使用 [負載測試編輯器] 和 [屬性] 視窗編輯負載測試情節，以設定測試反覆項目的設定。 根據預設，設定的情節中，沒有測試反覆項目上限。 您可以選擇性地在情節中設定反覆項目數目的上限，以及反覆項目之間暫停的時間長度。|-   [設定情節的測試反覆項目](../test/configure-test-iterations-in-a-load-test-scenario.md)|
|**設定情節的延遲設定：** 使用 [負載測試編輯器] 和 [屬性] 視窗，您可以在負載測試中指定啟動情節前的延遲。 如果需要某個情節開始產生另一個情節會使用的項目，則這是可能想要使用 [延遲開始時間] 屬性時的其中一個範例。 您可以延遲使用項目的情節，讓產生項目的情節可以填入一些資料。|-   [設定情節開始延遲](../test/configure-scenario-start-delays.md)|
|**指定負載測試情節中所要使用的遠端電腦：** 建立負載測試之後，您可以編輯負載測試情節的屬性，以指出要包含的測試代理程式。 如需詳細資訊，請參閱 [測試控制器和測試代理](configure-test-agents-and-controllers-for-load-tests.md)程式。|-   [如何：指定要使用的測試代理程式](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)|

## <a name="see-also"></a>另請參閱

- [編輯負載測試](../test/edit-load-tests.md)
- [負載測試情節屬性](../test/load-test-scenario-properties.md)
