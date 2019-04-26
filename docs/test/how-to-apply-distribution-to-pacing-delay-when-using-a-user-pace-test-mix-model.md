---
title: 將分佈套用到步調延遲以進行負載測試
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d3ef8ecfefd1d614570b4d73808d3e5736d77230
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979335"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>HOW TO：將分佈套用到步調延遲以進行使用者步調測試混合模型

使用 [新增負載測試精靈] 來建立負載測試之後，就可以使用 [負載測試編輯器] 來變更情節屬性，以符合您的測試需求和目標。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

[將分佈套用到步調延遲] 屬性是使用 [屬性] 視窗來設定的。 負載測試情節的屬性是使用 [負載測試編輯器] 修改。

> [!NOTE]
> 只有在依據使用者步調設定「負載測試混合」時，才適用 [將分佈套用到步調延遲] 屬性。 如需詳細資訊，請參閱[編輯測試混合模型以指定虛擬使用者執行測試的可能性](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)。

[將分佈套用到步調延遲] 的值可以設定為 true 或 false：

- **True**：情節會套用 [編輯測試混合] 對話方塊中 [按每使用者每小時測試] 欄位值指定的常態統計分佈延遲。 如需詳細資訊，請參閱[編輯測試混合模型以指定虛擬使用者執行測試的可能性](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)。

     例如，假設您在 [編輯測試混合] 對話方塊中將測試的 [按每使用者每小時測試] 值設定為每小時兩位使用者。 如果 [將分佈套用到步調延遲] 屬性設定為 [True]，則正常統計散發會套用至測試之間的等待時間。 測試仍然會每小時執行兩項測試，但是兩項測試之間不一定會有 30 分鐘延遲。 第一項測試可能在四分鐘後執行，而第二項測試在 45 分鐘後執行。

- **False**：測試會依照您為 [編輯測試混合] 對話方塊中 [按每使用者每小時測試] 欄位值指定的步調來執行。 如需詳細資訊，請參閱[編輯測試混合模型以指定虛擬使用者執行測試的可能性](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)。

     例如，假設您在 [編輯測試混合] 對話方塊中將測試的 [按每使用者每小時測試] 值設定為每小時兩位使用者。 如果 [將分佈套用到步調延遲] 屬性設定為 [False]，則測試執行時不會有任何延遲。 測試將會每 30 分鐘執行。 這樣可確保每小時執行兩項測試。

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>若要針對情節指定將分佈套用到步調延遲屬性設定

1. 開啟負載測試。

   [負載測試編輯器] 隨即出現。 負載測試樹狀結構隨即顯示。

2. 在負載測試樹狀目錄的 [情節] 資料夾中，選取您要為其套用步調分佈的情節節點。

3. 在 [檢視] 功能表上，選取 [屬性視窗]。

   情節的分類和屬性會顯示在 [屬性] 視窗中。

4. 在 [將分佈套用到步調延遲] 的屬性值中，選取 [True] 或 [False]。

5. 選取 [檔案] > [儲存]。 現在，您已可以使用新的 [將分佈套用到步調延遲] 值來執行負載測試。

## <a name="see-also"></a>另請參閱

- [編輯負載測試情節](../test/edit-load-test-scenarios.md)
- [逐步解說：建立和執行負載測試](../test/walkthrough-create-and-run-a-load-test.md)
- [測試控制器和測試代理程式](configure-test-agents-and-controllers-for-load-tests.md)
- [負載測試情節屬性](../test/load-test-scenario-properties.md)