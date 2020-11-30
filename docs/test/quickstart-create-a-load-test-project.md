---
title: 建立 Web 效能和負載測試專案
description: 在本快速入門中，瞭解如何在 Visual Studio 中建立及執行 web 效能和負載測試專案。
ms.custom: SEO-VS-2020
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3833542dc00f347014dabf96f836fbd4fa810862
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329129"
---
# <a name="quickstart-create-a-load-test-project"></a>快速入門：建立負載測試專案

在此 10 分鐘的快速入門中，您將了解如何在 Visual Studio 中建立及執行 Web 效能和負載測試專案。 負載測試可執行 Web 效能或單元測試，以模擬同時存取某部伺服器的多位使用者。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="software-requirements"></a>軟體需求

只有 Visual Studio 的 **Enterprise 版本** 可以使用 Web 效能和負載測試專案。

## <a name="install-the-load-testing-component"></a>安裝負載測試元件

如果您尚未安裝 Web 效能與負載測試工具元件，您需要透過 Visual Studio 安裝程式來安裝它。

1. 從 Windows 的 [**開始**] 功能表開啟 **Visual Studio 安裝程式**。 您也可以從 [新增專案] 對話方塊，或從功能表列選擇 [**工具**  >  **取得工具和功能**]，在 Visual Studio 中存取它。

1. 在 [Visual Studio 安裝程式] 中，選擇 [個別元件] 索引標籤，然後向下捲動至 [偵錯和測試] 區段。 選取 [Web 效能與負載測試工具]。

   ![Web 效能與負載測試工具元件](media/web-perf-load-testing-tools-component.png)

1. 選擇 [修改] 按鈕。

   Web 效能與負載測試工具元件隨即安裝。

## <a name="create-a-load-test-project"></a>建立負載測試專案

在本節中，我們將建立 C# 負載測試專案。 如果您想要的話，您也可以建立 Visual Basic 負載測試專案。

::: moniker range="vs-2017"

1. 開啟 Visual Studio。

2. 從功能表列中選擇 [檔案]**[新增]** > **[專案]** > 。

   此時會開啟 [新增專案] 對話方塊。

3. 在 [新增專案] 對話方塊中，依序展開 [已安裝的] 和 [Visual C#]，然後選取 [測試] 分類。 選擇 [Web 效能和負載測試專案] 範本。

   ![Web 效能和負載測試專案範本](media/web-perf-load-test-project-template.png)

4. 如果您不想要使用預設名稱，請輸入專案的名稱，然後選擇 [確定]。

::: moniker-end

::: moniker range=">=vs-2019"

1. 開啟 Visual Studio。

2. 在 [開始] 視窗中，選擇 [ **建立新專案**]。

3. 在 [建立新專案] 頁面，於搜尋方塊內鍵入 **web test**，然後選取 C# 的 [Web 效能和負載測試專案] \[已淘汰] 範本。 選擇 [下一步]。

4. 如果您不想要使用預設名稱，請輸入專案的名稱，然後選擇 [建立]。

::: moniker-end

   Visual Studio 會建立專案，並在 **方案總管** 中顯示檔案。 專案一開始會包含一個名為 *webtest1.webtest webtest* 的 web 測試檔案。

## <a name="add-a-load-test-to-the-project"></a>將負載測試新增至專案

1. 從 [方案總管] 之專案節點的右鍵功能表或操作功能表，選擇 [新增] > [負載測試]。

   [新增負載測試精靈] 隨即開啟。

1. 選取 [內部部署負載測試] 選項，然後選擇 [下一步]。 您可以在[這裡](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts&preserve-view=true)深入了解雲端式負載測試。

   ![新增負載測試精靈 - 第一頁](media/load-test-wizard-page-1.png)

1. 選擇 [下一步] 逐步執行精靈，直到您到達 [將測試新增至負載測試情節，並且編輯測試混合] 頁面。 選擇 [新增] 按鈕。

   [新增測試] 對話方塊隨即開啟。

1. 在 [可用的測試] 底下選取 **WebTest1**，然後選擇向右箭號，將它移至 [選取的測試] 方塊。 選擇 [確定]  按鈕。

   ![[新增測試] 對話方塊](media/add-tests-dialog-box.png)

1. 回到 [新增負載測試精靈]，選擇 [完成] 按鈕。

   這會將負載測試新增至專案，並在編輯器視窗中開啟負載測試檔案。

## <a name="run-the-load-test"></a>執行負載測試

我們已建立負載測試，雖然功能不多，但讓我們繼續執行。

從編輯器中開啟之負載測試的右鍵功能表或操作功能表，選擇 [執行負載測試]。

![[執行負載測試] 功能表](media/run-load-test.png)

負載測試開始執行。 [測試結果] 視窗會顯示測試正在進行，並在編輯器視窗中顯示負載測試分析器。 測試完成之後 (如果您接受預設值則應為 5 分鐘之後)，摘要會顯示在編輯器中。 您可以選擇 [圖形]、[資料表] 或 [詳細資料]，來取得有關負載測試結果的不同資訊。

![負載測試分析器視窗](media/load-test-analyzer.png)

## <a name="next-steps"></a>後續步驟

現在您已建立簡單的負載測試專案，下一個步驟是設定情節、計數器集合與回合設定。

> [!div class="nextstepaction"]
> [編輯測試設定](edit-load-tests.md)
