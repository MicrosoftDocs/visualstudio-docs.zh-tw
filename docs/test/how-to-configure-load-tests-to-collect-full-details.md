---
title: 在 Visual Studio 中收集虛擬使用者的完整詳細資料以進行負載測試 | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart, configuring
- virtual user activity chart, configuring
ms.assetid: cb22e43b-af4d-4e09-9389-3c3fa00786f7
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: d18a93fad0d113369f48e21ae74a08484b99485c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-load-tests-to-collect-full-details-to-enable-virtual-user-activity-in-test-results"></a>如何：設定負載測試來收集完整詳細資料，以便在測試結果中啟用虛擬使用者活動

若要對負載測試使用虛擬使用者活動，您必須設定負載測試以收集完整詳細資料。 若要設定負載測試進行這項作業，請選取與負載測試建立關聯之 [計時詳細資料儲存區] 屬性的 [所有個別細節] 設定。 在這個模式中，負載測試將會收集每個測試、頁面和異動的詳細資訊。

 如果您要升級舊版 Visual Studio 負載測試的專案，請使用下列程序的步驟啟用完整詳細資料收集。

 [計時詳細資料儲存區] 屬性的 [所有個別細節] 設定可以設為下列任何選項：

-   **所有個別細節：**針對測試期間發行的每個測試、異動和頁面，收集和儲存個別計時資料。

    > [!NOTE]
    > 必須選取 [所有個別細節] 選項，才能在負載測試結果中啟用虛擬使用者資料資訊。

-   **無：**不收集任何個別計時詳細資料。 但仍會收集平均值。

-   **僅限統計資料：**儲存個別計時資料，但只以百分位數資料形式儲存。 這樣可以節省空間資源。

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>若要設定負載測試中的計時詳細資料儲存區屬性

1.  在負載測試編輯器中開啟負載測試。

2.  展開負載測試中的 [回合設定] 節點。

3.  選擇您要設定的回合設定，例如 [回合設定1[作用中]]。

4.  開啟屬性視窗。 在 [檢視] 功能表上，選取 [屬性視窗]。

5.  在 [結果] 分類底下，選擇 [計時詳細資料儲存區] 屬性，並選取 [所有個別細節]。

     設定 [計時詳細資料儲存區] 屬性的 [所有個別細節] 設定之後，您可以執行負載測試並檢視虛擬使用者活動圖。 如需詳細資訊，請參閱[如何：分析虛擬使用者在負載測試期間的行為](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)。

## <a name="see-also"></a>另請參閱

- [在詳細資料檢視中分析虛擬使用者活動](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [逐步解說：使用虛擬使用者活動圖表來隔離問題](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)