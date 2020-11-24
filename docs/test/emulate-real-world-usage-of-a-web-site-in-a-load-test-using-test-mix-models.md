---
title: 模擬網站的實際使用情形以進行負載測試
description: 使用負載模型選項，更精確地預測您要進行負載測試之網站或應用程式的預期實際使用方式。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load model, specifying
- load test load model, specifying
ms.assetid: b7fae849-0538-40d1-ab35-2bb3a0fe4393
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ba5bba0b90acdfab932196ceda7dd8ad971efde1
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441257"
---
# <a name="test-mix-models-overview"></a>測試混合模型概觀

使用負載模型選項，可以讓您對正在進行負載測試的網站或應用程式，更為準確地預測其預期的真實使用情況。 這相當重要，因為若負載測試不是奠基於準確的負載模型，便可能會產生誤導的結果。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-enhancements"></a>測試混合模型的加強功能

使用 [負載測試編輯器] 或測試混合模型精靈，可以讓您為負載測試情節指定下列類型的測試混合。 如需詳細資訊，請參閱[變更情節中的測試混合模型](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)。

您可以針對負載測試情節指定下列其中一個測試混合模型選項：

- **按總測試數：** 判斷當虛擬使用者啟動測試反覆項目時所執行的 Web 效能或單元測試。 在負載測試結束時，特定測試回合的次數會與指派的測試分佈相符。 當您的測試混合是以 IIS 記錄或實際執行資料中的交易百分比為基礎時，請使用此測試混合模型。 如需詳細資訊，請參閱以 [啟動的測試為依據的百分比](#BasedOnTestsStarted)。

- **按虛擬使用者人數：** 判斷將執行特定 Web 效能或單元測試之虛擬使用者的百分比。 在負載測試的任一時間點，執行特定測試的使用者人數會與指定的測試分佈相符。 當您的測試混合是以執行特定測試的使用者百分比為基礎時，請使用此測試混合模型。 如需詳細資訊，請參閱[按虛擬使用者的百分比](#PercentageBasedonVirtualUsers)。

- **按使用者步調：** 在負載測試進行期間，每個 Web 效能測試或單元測試會在每小時內針對每位使用者執行指定的次數。 當您想要讓虛擬使用者在整個負載測試中以特定步調執行測試時，請使用此測試混合模型。 如需詳細資訊，請參閱[步調測試混合](#PacingTestMix)。

    > [!TIP]
    > 選擇 **百分比測試混合** 和 **按虛擬使用者的百分比** 的時機為何？ 當測試混合中某些測試的持續期間比其他測試長很多時，這兩個選擇間的差異就很重要。 在這種情況下，您可能應該選擇 **按虛擬使用者的百分比**。 當太多使用者會執行長時間測試的可能性增高時，這個選擇有助於避免這類的測試回合。 然而，當測試都具有差不多的持續期間時，選擇 **百分比測試混合** 就可以較為放心。

- **依據循序順序：** 每位虛擬使用者都會按照情節中定義測試的順序來執行 Web 效能或單元測試。 虛擬使用者會繼續按照此順序進行測試循環，直到負載測試完成為止。 如需詳細資訊，請參閱 [順序](#SequentialOrder)。

### <a name="percentage-based-on-tests-started"></a><a name="BasedOnTestsStarted"></a> 以啟動的測試為依據的百分比

對於混合中的每個測試，您可以指定百分比以決定測試被選為下一個執行測試的頻率。 舉例來說，您可以指派下列百分比值給三個測試：

- TestA (50%)

- TestB (35%)

- TestC (15%)

如果使用這些設定，下一個要啟動的測試會依據指派的百分比而決定。 執行這項操作時，不需考慮目前執行每個測試的虛擬使用者人數。

### <a name="percentage-based-on-virtual-users"></a><a name="PercentageBasedonVirtualUsers"></a> 以虛擬使用者為基礎的百分比
這個測試混合模型決定將執行特定測試的虛擬使用者的百分比。 如果使用這個測試混合模型，下一個要啟動的測試，不僅會依據指派的百分比，也會依據目前執行特定測試的虛擬使用者百分比而決定。 在負載測試的任何點中，執行特定測試的使用者人數，會盡可能符合指派的持續期間。

### <a name="pacing-test-mix"></a><a name="PacingTestMix"></a> 步調測試混合

如果指定步調測試混合，是針對測試混合中每個測試每個虛擬使用者，設定測試執行的比率。 對於每個測試，這個比率表示每個虛擬使用者每小時的測試回合。 舉例來說，您可以指派下列步調測試混合給下列測試：

- TestA：每個使用者每小時 4 個測試

- TestB：每個使用者每小時 2 個測試

- TestC：每個使用者每小時 0.125 個測試

如果使用步調測試混合模型，負載測試執行階段引擎會保證啟動測試的實際比率會小於或等於指定比率。 當測試執行太久而無法完成指派數目時，就會傳回錯誤。

使用步調測試混合時，[測試反覆項目間的考慮時間] 設定並不適用。

#### <a name="apply-distribution-to-pacing-delay"></a>將分佈套用到步調延遲
負載測試情節中的 [將分佈套用到步調延遲] 屬性值可以設定為 true 或 false：

- **True**：案例會套用 [**編輯測試混合**] 對話方塊中 [**按每使用者每小時測試**] 欄位的值所指定的一般統計散發延遲。 如需詳細資訊，請參閱[編輯測試混合模型以指定虛擬使用者執行測試的可能性](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)。

   例如，假設您在 [**編輯測試混合**] 對話方塊中將測試的 [每個 **使用者每小時測試**] 值設定為每小時2位使用者。 如果 [將分佈套用到步調延遲] 屬性設定為 [True]，則一般統計散發延遲會套用至測試之間的等待時間。 測試仍然會每小時執行 2 項測試，但是 2 項測試之間不一定會有 30 分鐘間隔。 第一項測試可能在 4 分鐘後執行，而第二項測試在 45 分鐘後執行。

- **False**：測試將依照您在 [**編輯測試混合**] 對話方塊中 [按每 **使用者每小時測試**] 資料行的值所指定的特定步調執行。 如需詳細資訊，請參閱[編輯測試混合模型以指定虛擬使用者執行測試的可能性](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)。

   例如，假設您在 [**編輯測試混合**] 對話方塊中將測試的 [每個 **使用者每小時測試**] 值設定為每小時2位使用者。 如果 [將分佈套用到步調延遲] 屬性設定為 [False]，則測試執行時基本上不會有任何延遲。 測試將會每 30 分鐘執行。 這樣可確保每小時執行 2 項測試。

  如需詳細資訊，請參閱 [如何：在使用使用者步調測試混合模型時，將分佈套用到步調延遲](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)。

### <a name="sequential-order"></a><a name="SequentialOrder"></a> 順序
選取 [依據循序測試順序] 選項，可讓每個虛擬使用者按測試的定義順序，執行情節中的所有測試。

## <a name="test-iterations-property"></a>測試反覆項目屬性
在 [回合設定] 屬性中，您可以指定 [測試反覆項目] 屬性的值。 這個值是在負載測試中測試反覆項目要執行的次數。 啟動指定次數的測試反覆項目後，不論載入設定檔是如何設定的，都不會啟動額外的測試反覆項目。 完成指定次數的測試反覆項目後，負載測試就會結束。 如需詳細資訊，請參閱 [如何：在回合設定中指定測試](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)反復專案的數目。

## <a name="initialize-and-terminate-tests"></a>初始化和結束測試
您可以選取在每個虛擬使用者負載測試工作階段的開始和結束時要執行的測試。 如需詳細資訊，請參閱[編輯測試混合模型以指定虛擬使用者執行測試的可能性](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)。

- **初始化測試**： 這個測試是在測試混合中任何測試執行前，由每個虛擬使用者所執行的。

- **結束測試**： 這個測試是在特定虛擬使用者的所有測試執行後才執行的。

  請注意下列有關初始化測試和結束測試的事項：

- 您可以依據時間而不是反覆計數，指定負載測試持續期間。 在這種情況下，當負載測試回合持續期間完成時，不會執行結束測試。

- 如果初始化測試是單元測試或 Web 效能測試，在完成初始化測試後便會儲存 TestContext 或 WebTestContext 物件的狀態。 這會接著用來做為測試混合中測試反覆項目的起始內容。

- 情節屬性 [新使用者的百分比] 中定義的新使用者，一定要執行初始化測試、測試混合中的一個測試反覆項目，以及結束測試。

## <a name="see-also"></a>另請參閱

- [編輯測試混合模型以指定虛擬使用者執行測試的可能性](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [編輯負載模式以模型化虛擬使用者活動](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [編輯測試混合以指定要包含在負載測試情節中的測試](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [設定負載測試回合設定](../test/configure-load-test-run-settings.md)
- [負載測試情節屬性](../test/load-test-scenario-properties.md)
- [變更情節中的測試混合模型](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
