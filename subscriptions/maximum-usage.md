---
title: 使用管理入口網站中的 [使用量上限] 功能
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/24/2019
ms.topic: conceptual
description: 了解如何在管理入口網站中檢視已指派的訂用帳戶數目上限
searchscope: VS Subscription
ms.openlocfilehash: c263c610b140d3662cb17ba9f2c3d3f1a1907ab7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965393"
---
# <a name="using-the-maximum-usage-feature-to-track-the-number-of-assigned-subscriptions"></a>使用 [使用量上限] 功能來追蹤已指派的訂用帳戶數目

Visual Studio 訂用帳戶系統管理入口網站中新功能會協助您追蹤曾購買和指派的訂用帳戶數量，並識別過去一年和整個合約持續時間內，每個層級曾指派的訂用帳戶尖峰數目。 

## <a name="viewing-maximum-usage"></a>檢視使用量上限

查看任何合約和訂用帳戶層級指派的訂用帳戶尖峰數目：

1. 在入口網站左上方下拉式清單中選取您想要檢視的合約。 (如果您只有一份合約，它會是已選取狀態。)

2. 按一下 [使用量上限] 索引標籤。  
    > [!div class="mx-imgBorder"]
    > ![[使用量上限] 功能表](_img/maximum-usage/maximum-usage-menu.png)

3. 「使用量上限摘要」隨即出現，且會顯示每個層級過去一年內已指派的訂用帳戶最大數目，以及達到該尖峰的日期。  如果達到該尖峰的次數超過一次，則會顯示第一次達到的尖峰。 
    > [!div class="mx-imgBorder"]
    > ![[使用量上限] 摘要](_img/maximum-usage/maximum-usage-summary.png)

4. 若要查看合約存留期間內已指派的訂用帳戶最大數目，請按一下 [Full-Term] \(全程執行期間\) 索引標籤。

## <a name="viewing-assignment-history"></a>檢視指派記錄

按一下 [Export full report] \(匯出完整報告\) 按鈕，除可看到每個訂用帳戶層級的尖峰指派，您還可以看到合約的活動執行帳戶，包括購買和指派。  

> [!div class="mx-imgBorder"]
> ![[使用量上限] 完整報告](_img/maximum-usage/maximum-usage-full-report.png)

針對每個訂用帳戶層級，此報告會顯示日期您達到新指派上限層級的日期，和您自該日期起已購買的訂用帳戶數目，讓您輕鬆查看任何出現過度分派的日期。  

例如，在上表中可以看到，合約在 2018 年 12 月 13 日時有 123 個 Visual Studio Enterprise 訂用帳戶，且已指派 120 個。  2019 年 1 月 8 日，多指派了一個訂用帳戶，使得總數達到 121 個。  隔天，又指派六個訂用帳戶，並在合約中新增四個訂用帳戶，以平衡新的指派數量。  

## <a name="frequently-asked-questions"></a>常見問題集
### <a name="q-how-is-the-information-in-the-maximum-usage-different-from-the-assignment-information-available-in-the-overview-section-on-the-left-side-of-the-portal"></a>問：[使用量上限] 的資訊和入口網站左側 [概觀] 區段提供的指派資訊有何不同？

答：[概觀] 中的資訊顯示每個訂用帳戶層級目前指派和可用的訂用帳戶。  這和合約在任何時點的已指派訂用帳戶數目上限會有極大差異。  [使用量上限] 功能可讓您查看何時達到指派層級上限以及哪個層級。  這是重要的區別，因為訂用帳戶的計費校正期間是以任何時點已指派訂用帳戶數目上限為基礎。 

## <a name="next-steps"></a>後續步驟
如果您有任何關於訂用帳戶指派或系統管理入口網站其他方面的問題，請連絡 https://visualstudio.microsoft.com/subscriptions/support/ 以尋求協助。 