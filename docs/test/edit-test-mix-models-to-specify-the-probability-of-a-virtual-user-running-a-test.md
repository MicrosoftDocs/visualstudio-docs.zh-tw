---
title: 編輯測試混合模型
description: 瞭解測試混合模型如何讓您擁有數個工作流程，這些工作流程會更接近終端使用者與您的應用程式互動的方式。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios
- load tests, virtual users
ms.assetid: e3b7d952-9012-400a-8131-3444390a6066
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 2ef6844c76638b46e43556eb9294cce04a7d1fcf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926777"
---
# <a name="edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test"></a>編輯測試混合模型以指定虛擬使用者執行測試的可能性

「測試混合模型」會指定在負載測試情節中，執行指定測試的虛擬使用者的可能性。 這可讓您更寫實地模擬負載。 您能夠擁有數個工作流程 (而不是整個應用程式中只有一個工作流程)，這可以更貼切地呈現使用者與應用程式互動的方式。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-options"></a>測試混合模型選項

您可以針對負載測試情節指定下列其中一個測試混合模型選項：

- **按總測試數：** 判斷當虛擬使用者啟動測試反覆項目時所執行的 Web 效能或單元測試。 在負載測試結束時，特定測試的執行次數會與指定的測試分佈相符。 當您的測試混合是以 IIS 記錄或實際執行資料中的交易百分比為基礎時，請使用此測試混合模型。

- **按虛擬使用者人數：** 判斷將執行特定 Web 效能或單元測試之虛擬使用者的百分比。 在負載測試的任一時間點，執行特定測試的使用者人數會與指定的測試分佈相符。 當您的測試混合是以執行特定測試的使用者百分比為基礎時，請使用此測試混合模型。

- **按使用者步調：** 在負載測試進行期間，每個 Web 效能測試或單元測試會在每小時內針對每位使用者執行指定的次數。 當您想要讓虛擬使用者在整個負載測試中以特定步調執行測試時，請使用此測試混合模型。

- **依據循序順序：** 每位虛擬使用者都會按照情節中定義測試的順序來執行 Web 效能或單元測試。 虛擬使用者會繼續按照此順序進行測試循環，直到負載測試完成為止。

## <a name="tasks"></a>工作

|工作|相關主題|
|-|-----------------------|
|**指定負載測試的測試混合：** 建立負載測試時，您可以在 [新增負載測試精靈] 中指定負載測試的設定。 在 [新增負載測試精靈] 中，您可以選擇要加入至初始情節的現有 Web 和單元測試。 當您將測試加入至情節之後，就可以指定情節的測試混合。<br /><br /> 使用負載模型選項，可以讓您對進行負載測試中的網站或應用程式，更為準確地預測其預期真實使用情況。 這是相當重要的，因為不是奠基於準確負載模型的負載測試，可能會產生誤導的結果。|-   [模擬網站或應用程式的預期實際使用情況](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)|
|**編輯測試混合模型：** 您可以使用 **負載測試編輯器**，將負載測試情節變更為使用其中一種測試混合模型。||
|**為按使用者步調的測試混合模型設定步調延遲：** 如果您的負載測試情節已設定為使用 [按使用者步調的測試混合模型]，您可以指定設定分佈步調延遲的方式。|-   [如何：在使用使用者步調測試混合模型時，將分佈套用到步調延遲](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|

## <a name="change-the-test-mix-model-in-a-scenario"></a>變更情節中的測試混合模型

使用 **新的負載測試精靈** 建立負載測試之後，您可以使用 **負載測試編輯器** 來變更情節屬性，以符合您的測試需求和目標。

> [!NOTE]
> 如需載入設定屬性及其描述的完整清單，請參閱 [負載測試情節屬性](../test/load-test-scenario-properties.md)。

使用 **負載測試編輯器**，您可以在 [**屬性**] 視窗中編輯 [**測試混合類型**] 屬性，以變更負載測試情節中的測試混合模型。

### <a name="to-change-the-test-mix-model"></a>若要變更測試混合模型

1. 開啟負載測試。

     [負載測試編輯器] 隨即出現。 負載測試樹狀結構隨即顯示。

2. 在負載測試樹狀目錄的 [情節] 資料夾中，選擇您要為其指定測試反覆項目數上限的情節節點。

3. 在 [檢視] 功能表上，選取 [屬性視窗]。

     情節的分類和屬性隨即出現。

4. 在 [測試混合類型] 屬性中選擇省略符號按鈕 (**…**)。

     [編輯測試混合] 對話方塊隨即出現。

5. 選擇 [測試混合模型] 底下的下拉式清單，並選取情節所要使用的測試混合類型。

6. (選擇性) 使用 [新增]、[移除] 和 [均分] 按鈕與分佈滑桿，修改測試混合。 如需詳細資訊，請參閱[編輯測試混合以指定要包含在負載測試情節中的測試](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)。

7. (選擇性) 使用核取方塊並選取所要的測試，指定要初始化或結束的 Web 效能與單元測試。 如需詳細資訊，請參閱[模擬網站或應用程式的預期實際使用情況](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)。

8. 選擇 [確定]。

     [屬性] 視窗隨即為 [測試混合類型] 屬性顯示新的測試混合模型。

9. 變更屬性之後，請選擇 [檔案] 功能表上的 [儲存]。 然後，您就可以使用新的 [測試混合類型] 值來執行負載測試。

## <a name="see-also"></a>另請參閱

- [編輯負載測試情節](../test/edit-load-test-scenarios.md)
- [負載測試情節屬性](../test/load-test-scenario-properties.md)
