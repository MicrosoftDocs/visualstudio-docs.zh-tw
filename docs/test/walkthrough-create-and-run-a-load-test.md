---
title: 建立和執行負載測試
description: 瞭解如何建立包含單元測試的負載測試。 您可以使用 Visual Studio Enterprise 來建立和執行負載測試。
ms.custom: SEO-VS-2020
ms.date: 10/01/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, in load tests
- unit tests, load test walkthrough
- load tests, walkthrough
ms.assetid: bbf075a5-96d5-48ed-a03c-330f0fc04748
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 888bf1f699027ab883a01ba74d8efc5703c91c9a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968966"
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>逐步解說：建立和執行包含單元測試的負載測試

在這個逐步解說中，您會建立包含單元測試的負載測試。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

本逐步解說會引導您使用 Visual Studio Enterprise 建立及執行負載測試。 負載測試是 Web 效能測試和單元測試的容器。 負載測試是利用 [新增負載測試精靈] 所建立。

負載測試也會公開 (Expose) 許多執行階段屬性，您可以修改這些屬性，以產生需要的負載模擬。 在這個逐步解說中，您會使用 [新增負載測試精靈] 將單元測試加入至負載測試。

在這個逐步解說中，您將完成下列工作：

- 建立使用單元測試的負載測試。

- 變更部分負載測試設定。

- 執行負載測試。

- 執行 [逐步解說：針對 managed 程式碼建立和執行單元測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) 中的步驟，以建立簡單的 c # 類別庫，其中包含有一些單元測試的 web 效能和負載測試專案。

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>使用新增負載測試精靈建立包含單元測試的負載測試

### <a name="to-start-the-new-load-test-wizard"></a>若要啟動新增負載測試精靈

1. 請確定您已安裝 [[建立負載測試專案](../test/quickstart-create-a-load-test-project.md)] 中所述的 [ **Web 效能和負載測試工具**] 元件。

1. 開啟您在 [逐步解說：針對 managed 程式碼建立和執行單元測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)中建立的 Bank 方案。

1. 在 [方案總管]，開啟 Bank 方案節點的捷徑功能表，選擇 [新增]，然後選擇 [新增專案]。

     [加入新的專案] 對話方塊隨即顯示。

1. 在 [ **加入新專案** ] 對話方塊中，展開 [ **Visual c #** ]，然後選擇 [ **測試**]。 在範本清單中，選擇 [Web 效能和負載測試專案]，然後在 [名稱] 欄位中，鍵入 `BankLoadTest`。 選擇 [確定]。

     BankLoadTest Web 效能和負載測試專案會加入至方案。

1. 開啟新的 BankLoadTest Web 效能和負載測試專案的捷徑功能表，選擇 [新增]，然後選擇 [負載測試]。

1. [新增負載測試精靈] 隨即啟動。

1. [新增負載測試精靈] 的 [歡迎使用] 頁面是第一個出現的頁面。

1. 選擇 [下一步]。

### <a name="to-edit-settings-for-load-test-scenario"></a>若要編輯負載測試情節的設定

1. 在 [輸入負載測試情節的名稱] 文字方塊中，鍵入 **ScenarioSample**。

     「情節」是一個群組機制。 它是由一組測試和在負載之下執行這些測試的屬性所構成。

2. 將 [時間特性考慮] 設為 [`Use normal distribution centered on recorded think times`]。 考慮時間代表使用者從網頁移到下一頁之前的暫停時間。

1. 完成時，請選擇 [下一步]。

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>若要編輯測試情節的負載模式設定

1. 選擇 [逐步執行負載]。

    > [!NOTE]
    > 您可以選擇兩種負載模式類型：常數負載和逐步執行負載。 每一種類型在負載測試中都有其功能，但是在此逐步解說中，請選擇 [逐步執行負載]。

2. 將 [啟動使用者計數] 設為 10 個使用者。

3. 將 [逐步執行持續期間] 設為 10 秒。

4. 將 [逐步執行使用者計數] 設為 10 位使用者/逐步執行。

5. 將 [最大使用者計數] 設為 100 位使用者。

6. 選擇 [下一步]。

### <a name="to-select-test-mix-model-for-the-scenario"></a>若要選取情節的測試混合模型

1. 在 **[如何將測試混合模型** 化] 底下，選取 [ **根據測試總數**]。

2. 選擇 [下一步]。

### <a name="to-add-unit-tests-to-the-scenario"></a>若要將單元測試加入至情節

1. 下一個步驟是 [將測試新增至負載測試情節，並且編輯測試混合]。

2. 選擇 [新增] 選取測試。

3. 選擇 [**可用的測試**] 窗格中所列的 **CreditTest** 單元測試，其中會列出 web 效能和負載測試專案中的所有 web 效能測試和單元測試。

4. 選擇箭號，將 **CreditTest** 單元測試新增至 [ **選取的測試** ] 窗格。

5. 針對 **DebitTest** 和 **FreezeAccountTest** 單元測試重複步驟 3 和 4。

6. 在加完這三個單元測試後，選擇 [確定]。

     就可以看到測試混合。

7. 將 **CreditTest** 的 [分佈] 下方的滑桿略往右移，以調整測試分佈。 留意到其餘滑桿會自動往左移，而分佈會維持在 100%。

8. 選擇 [下一步]。

### <a name="to-select-network-mix-for-test-scenario"></a>若要選取測試情節的網路混合

1. 選取要加入網路頻寬混合的 LAN 連線類型。

     您還可以新增其他網路類型。 使用滑桿來調整測試散發和加權。

2. 選擇 [下一步]。

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>若要指定要在負載測試執行期間以計數器集合監視的電腦

1. 選擇 [下一步]。

     如需計數器集合的詳細資訊，請參閱[在負載測試中指定電腦的計數器集合和臨界值規則](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)。

### <a name="to-edit-run-setting-for-load-test"></a>若要編輯負載測試的回合設定

1. 選取 [負載測試持續期間]，然後將 [執行持續期間] 設為 2 分鐘，以便替負載測試進行「煙霧測試」(Smoke Test)。

     建置負載測試時，先執行簡短的輕量負載測試，驗證所有項目均已正確設定並如預期般執行，會是很好的習慣。 這個程序稱為「煙霧測試」(Smoke Testing)。

2. 選擇 [完成]。 您的負載測試會在 [負載測試編輯器] 中開啟。

## <a name="run-the-load-test"></a>執行負載測試
 建立好負載測試之後，請執行此測試，以檢視銀行應用程式對負載模擬的反應。 負載測試執行時，您會看到 [負載測試分析器] 視窗。

### <a name="to-run-the-load-test"></a>若要執行負載測試

1. 在 [負載測試編輯器] 中開啟負載測試後，選擇工具列上綠色的 [執行測試] 按鈕。 您的負載測試便會開始執行。

2. 如果您的測試模擬超出任何臨界值，樹狀控制項節點便會出現圖示，指出發生臨界值違規。 錯誤上面會有紅色圈圈，警告則是黃色的三角形。 您會看到超過臨界值的計數器，且若將圖示拖曳到圖形中，即可繪製圖形。 您可以在測試執行時執行此動作。

## <a name="see-also"></a>另請參閱

- [編輯測試混合以指定要包含在負載測試情節中的測試](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [指定虛擬網路類型](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [編輯負載測試情節](../test/edit-load-test-scenarios.md)
- [編輯負載模式以模型化虛擬使用者活動](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [編輯測試混合模型以指定虛擬使用者執行測試的可能性](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
