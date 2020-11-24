---
title: 用於負載測試情節的測試混合
description: 瞭解如何編輯案例的測試混合，其結合了 web 效能和單元測試的選取範圍，以及這些測試的分佈。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, adding tests
- test mix
- load tests, test mix
- load tests, removing tests
ms.assetid: 303e1d70-5d98-424a-b51e-e0898e16d3f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d6681b8aead05a180df04b1c3953002aa832a281
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441374"
---
# <a name="edit-the-test-mix-to-specify-which-web-performance-unit-and-coded-ui-tests-to-include-in-a-load-test-scenario"></a>編輯測試混合以指定要包含在負載測試情節中的 Web 效能測試、單元測試和自動程式化 UI 測試

情節的「測試混合」結合了情節所包含之 Web 效能和單元測試的選取範圍，以及這些測試在情節中的分佈方式。 分佈就是您可以針對虛擬使用者在負載測試回合期間選取特定測試之可能性指定的設定。

將一組測試新增至負載測試之後，「測試混合」便會像其他混合選項般運作。 虛擬使用者會根據您在混合中指定的可能性，隨機地選取測試。 例如，如果您有兩個測試，各佔混合的 50%，則新虛擬使用者大約有一半的時間會選擇執行第一個測試。 在 50/50 混合中，如果某個測試較長，而另一個測試較短，則較長的測試便會造成較多負載。

將測試加入至混合之後，您就可以移除測試。 此外，您也可以使用混合控制項，變更測試混合的分佈。 混合控制可讓您輕鬆地調整測試在情節中的分佈方式。

> [!NOTE]
> 分佈是用來度量虛擬使用者在執行負載測試期間選取特定測試的可能性。 而且會以百分比表示分佈程度。 因此，情節中所有測試的分佈數目總和是 100。 例如，如果情節僅包含一個測試，則該測試的分佈程度為 100%。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-tests-to-a-test-mix-in-an-existing-scenario"></a>將新的測試新增至現有情節中的測試混合

當您使用 [新增負載測試精靈] 來建立新的情節時，可以指定要加入至新情節之測試混合的 Web 效能和單元測試。

您可以使用 [負載測試編輯器] 將其他 Web 效能和單元測試加入至情節的測試混合。

![將測試加入至現有的負載測試](../test/media/ltest_addingtests.png)

### <a name="to-add-more-tests-to-an-existing-scenario"></a>若要將其他測試加入至現有的情節

1. 開啟負載測試。

2. 在 [負載測試編輯器] 中，以滑鼠右鍵按一下現有的情節，然後選擇 [加入測試]。

     [新增測試] 對話方塊隨即出現。 方案中所有原本不存在於情節的 Web 效能、單元和自動程式化 UI 測試都可以加入至情節。

3. 在 [可用的測試] 窗格中，選取您想要新增的 Web 效能、單元和自動程式化 UI 測試。 選擇向右箭號，將測試新增至 [選取的測試] 窗格。

4. 完成新增測試之後，選擇 [確定]。

     測試便會加入至測試混合。 新的散發會自動指派至測試混合中的測試。

5. (選擇性) 調整混合控制項以指定測試分佈。 如需詳細資訊，請參閱 [關於混合控制項](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)。

## <a name="remove-tests-from-a-scenario"></a>從情節移除測試
![從現有的負載測試中移除測試](../test/media/ltest_removetest.png)

### <a name="to-remove-tests-from-a-scenario"></a>從情節移除測試

1. 開啟負載測試。

2. 在 [負載測試編輯器] 的負載測試樹狀目錄中，以滑鼠右鍵按一下您想要從中移除測試的情節，然後選取 [編輯測試混合]。 [編輯測試混合] 對話方塊隨即出現。

3. 在方格中選取 Web 效能、單元或自動程式化 UI 測試，然後選擇 [移除]。

    > [!NOTE]
    > 移除測試後，請將測試混合調整為您慣用的散發。

4. 完成移除測試之後，選擇 [確定]。

## <a name="about-the-mix-control"></a><a name="EditingTestMixAboutMixControl"></a> 關於混合控制項
混合控制可讓您在負載測試情節中，調整分佈在測試、瀏覽器類型或網路類型中的負載百分比。 您可以藉由移動滑桿調整百分比值。 調整混合測試可指定在負載測試情節中，一位虛擬使用者執行特定測試的可能性。

當您移動滑桿時，所有可用項目的百分比值就會變更。 如果您有兩個以上的項目，您所新增或移除的數量會在其他項目間平均分佈。 您無法覆寫這個行為。 如果您針對特定項目選取鎖定資料行中的核取方塊，就會鎖定該項目所指定的百分比值。 之後，當您移動滑桿時，您所新增或移除的數量僅會套用到其餘未鎖定的所有項目。

[均分] 按鈕用於平均配置所有項目間的百分比。 例如，如果您有三個項目，選擇 [均分] 會將百分比值設定為 34、33 與 33。

> [!WARNING]
> [均分] 按鈕會覆寫所有已鎖定的項目。

您也可以直接在資料行中輸入百分比值， **%** 而不是使用滑杆。 如果您直接輸入百分比值，其他項目就不會自動調整。

> [!NOTE]
> 當總計未新增至100%，或輸入資料行的百分比值為十進位時，滑杆會停用 **%** 。

當您手動輸入百分比值時，應確認所有項目的總和為 100%。 當您儲存混合時，如果總和不是 100%，系統會提示您接受該百分比值，或返回予以調整。 如果您選擇接受此設定，則會按比例分配至 100%。  例如，如果您有兩個項目，而且手動設定為 80% 和 40%。第一個項目會被設定為 66.67% (80 除以 120)，而第二個項目則會被設定為 33.33% (40 除以 120)。

## <a name="see-also"></a>另請參閱

- [編輯負載測試情節](../test/edit-load-test-scenarios.md)
