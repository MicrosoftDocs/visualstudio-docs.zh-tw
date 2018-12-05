---
title: 在 Visual Studio 中指定要用於負載測試情節的測試代理程式
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test agents, load tests
- load tests, scenarios
- load tests, specifying for load tests
- tests agents, load tests, specifying
- load tests, test agents
ms.assetid: e86806dd-5897-4e4c-bfd4-8d687fb72a6e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 1d153e3ab237e87764b8805c91f4e4c4e5512c60
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895180"
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>如何：指定要用於負載測試情節的測試代理程式

使用 [新增負載測試精靈] 建立負載測試之後，您就可以使用 [負載測試編輯器] 來變更情節屬性，以便符合您的測試需求和目標。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> 如需負載測試情節屬性及其描述的完整清單，請參閱[負載測試情節屬性](../test/load-test-scenario-properties.md)。

指定代理程式的方式，是在 [負載測試編輯器] 中變更 [屬性] 視窗中的 [要使用的代理程式] 屬性。

如果您是要從遠端使用控制器和代理程式執行負載測試，可以指定想要情節使用的代理程式。 例如，您可以指定特定一組代理程式，以便在分析效能趨勢時維持一致性。 另外，代理程式也可以分散在不同的地理位置，讓代理程式執行的指令碼更親近於代理程式所在地。

> [!TIP]
> 另一個可用的選項是使用網路模擬來模擬慢速網路，而不是實際將代理程式放在遠端網站。 如需詳細資訊，請參閱[指定虛擬網路類型](../test/specify-virtual-network-types-in-a-load-test-scenario.md)。

如需詳細資訊，請參閱[測試控制器和測試代理程式](configure-test-agents-and-controllers-for-load-tests.md)。

另一個原因是部分 (但非全部) 代理程式中可能已安裝特定情節所需的軟體。

您可以在測試設定中使用角色，控制針對指定的測試回合選取的代理程式。 如需詳細資訊，請參閱[使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)。

如果測試代理程式電腦的 CPU 使用率超過 75% 或可用的實體記憶體低於 10%，請將更多代理程式加入至您的負載測試，確保代理程式電腦不會成為負載測試的瓶頸。

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>若要指定要用於情節的代理程式

1.  開啟負載測試。

     [負載測試編輯器] 隨即出現。 負載測試樹狀隨即顯示。

2.  在負載測試樹狀目錄的 [情節] 資料夾中，選擇您要為其指定要使用之代理程式的情節節點。

3.  在 [檢視] 功能表上，選取 [屬性視窗]。

     情節的分類和屬性會顯示在 [屬性] 視窗中。

4.  在 [要使用的代理程式] 屬性的文字方塊中，輸入可在其上執行情節之代理程式的清單。

     多個代理程式必須以逗號分隔，例如 "**Agent1, Agent2, Agent3**"。 將這個屬性保留空白，即指定情節應該使用所有可用的代理程式。

    > [!NOTE]
    > 本機回合會忽略 [要使用的代理程式] 屬性。 對遠端回合來說，如果 [要使用的代理程式] 中沒有指定任何代理程式，情節中的測試將不會執行。

5.  變更屬性之後，請選擇 [檔案] 功能表上的 [儲存]。 然後，您就可以使用新的 [要使用的代理程式] 值來執行負載測試。

## <a name="see-also"></a>另請參閱

- [編輯負載測試情節](../test/edit-load-test-scenarios.md)
- [逐步解說：建立和執行負載測試](../test/walkthrough-create-and-run-a-load-test.md)
- [測試控制器和測試代理程式](configure-test-agents-and-controllers-for-load-tests.md)
- [負載測試情節屬性](../test/load-test-scenario-properties.md)