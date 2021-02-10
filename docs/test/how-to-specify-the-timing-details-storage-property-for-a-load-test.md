---
title: '計時詳細資料儲存區屬性 (負載測試回合設定) '
description: 瞭解如何編輯回合設定的計時詳細資料儲存區屬性。 有效的值只是個別詳細資料、無和統計資料。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 867a9c21-0909-4963-bc02-d41e9393008c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: f208dd19674a257381db6feeaf47df5d3951ff9d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969291"
---
# <a name="how-to-specify-the-timing-details-storage-property-for-a-load-test-run-setting"></a>如何：指定負載測試回合設定的計時詳細資料儲存區屬性

使用 [新增負載測試精靈] 建立負載測試之後，您就可以使用 [負載測試編輯器] 來變更設定，以便符合您的測試需求和目標。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

您可以在 [屬性] 視窗中編輯回合設定的 [計時詳細資料儲存區] 屬性值。 [計時詳細資料儲存區] 屬性可以設為下列任何選項：

- **所有個別細節：** 針對測試期間發行的每個測試、異動和頁面，收集和儲存個別計時資料。

  > [!NOTE]
  > 必須選取 [所有個別細節] 選項，才能在負載測試結果中啟用虛擬使用者資料資訊。 如需詳細資訊，請參閱[在詳細資料檢視中分析虛擬使用者活動](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)。

- **無：** 不收集任何個別計時詳細資料。 但仍會收集平均值。

- **僅限統計資料：** 儲存個別計時資料，但只以百分位數資料形式儲存。 這樣可以節省空間資源。

  **計時詳細資料儲存區屬性的考量**

  如果啟用 [計時詳細資料儲存區] 屬性，則在負載測試期間每個個別測試、異動和頁面的執行時間會儲存在負載測試結果儲存機制中。 這可讓第90和第95個百分位數資料顯示在 [ **負載測試分析器** ] 的 [ **測試**]、[ **交易**] 和 [ **頁面** ] 資料表中。

  如果啟用 [計時詳細資料儲存區] 屬性，將其值設為 [僅限統計資料] 或 [所有個別細節]，則會測量所有個別測試、頁面和異動的時間，也會從個別計時資料計算出百分位數資料。 其差異在於，使用 [僅限統計資料] 選項時，在計算出百分位數資料之後，系統就會從儲存機制中刪除個別的計時資料。 這樣做會減少使用計時詳細資料時儲存機制所需的空間量。 不過，如果您想要使用 SQL 工具，以其他方式處理計時詳細資料，在此情況下應使用 [所有個別細節] 選項，以便將計時詳細資料用於該處理。 此外，如果您將屬性設定為 **AllIndividualDetails**，則在負載測試執行完成之後，您就可以在 [**負載測試分析器**] 中使用 [**虛擬使用者活動圖**] 來分析虛擬使用者活動。 如需詳細資訊，請參閱[在詳細資料檢視中分析虛擬使用者活動](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)。

  負載測試結果儲存機制用來儲存計時詳細資料所需的空間可能相當大，尤其是長時間執行的負載測試。 其次，在負載測試結束時，用來將這項資料儲存至負載測試結果儲存機制的時間會比較長，因為在負載測試執行完成之前，這項資料會先存放在負載測試代理程式上，當負載測試完成後，資料就會儲存至儲存機制中。 [計時詳細資料儲存區] 屬性預設處於啟用狀態。 如果這對您的測試環境來說會是個問題，您可能會希望將 [計時詳細資料儲存區] 設定為 [無]。

  測試回合期間計時詳細資料會儲存在 *LoadTestItemResults.dat* 檔案中，在負載測試完成後就會傳回至控制器。 如果是長時間執行的負載測試，此檔案會相當大。 如果代理程式電腦上磁碟空間不足，這會是個問題。

  如果您要升級舊版 Visual Studio 負載測試的專案，請使用下列程序啟用完整詳細資料收集。

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>若要設定負載測試中的計時詳細資料儲存區屬性

1. 在負載測試編輯器中開啟負載測試。

2. 展開負載測試中的 [回合設定] 節點。

3. 選擇您要設定的回合設定，例如 [回合設定1[作用中]]。

4. 開啟 [ **屬性** ] 視窗。 在 [檢視] 功能表上，選取 [屬性視窗]。

5. 在 [結果] 分類底下，選擇 [計時詳細資料儲存區] 屬性，並選取 [所有個別細節]。

     設定 [**計時詳細資料儲存區**] 屬性的 [**所有個別詳細資料**] 設定之後，您可以執行負載測試並查看 [**虛擬使用者活動圖**]。 如需詳細資訊，請參閱 [如何：分析虛擬使用者在負載測試期間執行的動作](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)。

## <a name="see-also"></a>另請參閱

- [在詳細資料檢視中分析虛擬使用者活動](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [逐步解說：使用虛擬使用者活動圖來隔離問題](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)
