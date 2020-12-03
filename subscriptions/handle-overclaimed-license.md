---
title: 在 Visual Studio 訂用帳戶中處理過度配置的授權 |Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: a747100c-6f08-41a4-aaad-05099741742b
ms.date: 12/02/2020
ms.topic: conceptual
description: 瞭解系統管理員如何解決過度配置的訂閱
ms.openlocfilehash: c2876223d2aa4f8da5f267595a193a2fecc3ace2
ms.sourcegitcommit: 29099741fcf94a5aef2655ee16605728b8b9a0ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96537743"
---
# <a name="over-allocated-subscriptions"></a>過度配置的訂用帳戶
有時，在新增訂閱者之後訂單也有所變更，而可能導致已指派的訂閱數超過公司所擁有的授權數。 這稱為「過度配置」。  

若要查看您的訂用帳戶配置，請按一下左側的上方圖示，以開啟 [配置] 窗格。  

> [!NOTE]
> Open License 程式中不允許過度配置。  此外，其他程式在入口網站中可能會以不同的方式顯示此資訊。
>
> [!div class="mx-imgBorder"]
> ![過度領取的訂閱通知](_img/over-claimed/over-claimed-alert.png "配置中會列出過度配置的數目，並以每個訂用帳戶類型的圖形上的雜湊清單示。")

請注意，顯示會使用雜湊的橫條來指出過度配置的訂用帳戶。  所有訂用帳戶類型的過度配置數目都包含在頂端的 [總覽] 區段中，而且每個訂用帳戶層級也會顯示自己的配置狀態。  

## <a name="resolve-over-allocated-subscriptions"></a>解析過度配置的訂閱
有數種方式可解決過度配置：
- 聯絡您的轉銷商以購買額外的訂閱。
- 等到您的年度待處理期完成，並在該時間點支付過度配置的訂用帳戶。 
- 刪除部分訂閱指派。  (這無法排除每年校正時的付款需求，因為校正是以一年中在任何時間指派的最大訂閱數為依據。)

## <a name="billing-and-true-up"></a>計費與校正
如果您的組織有 Enterprise 合約 (EA)，系統管理員不必購買訂用帳戶即可加以指派，並在稍後透過稱為「校正」的對帳流程支付其費用。  當您過度配置時，您的組織將會以「true」期間指派給使用者的訂用帳戶數目上限為計費。  即使您在校正進行的當下已不再指派訂用帳戶的最大數目，也是如此。  若要深入了解如何監視您的最大使用量，請瀏覽[最大使用量](maximum-usage.md)主題。


## <a name="see-also"></a>請參閱
- [Visual Studio 檔](/visualstudio/)
- [Azure DevOps 文件](/azure/devops/) \(英文\)
- [Azure 檔](/azure/)
- [Microsoft 365 檔](/microsoft-365/)

## <a name="next-steps"></a>後續步驟
- 深入瞭解如何 [使用 GitHub Enterprise 管理 Visual Studio 訂閱](assign-github.md)。
- 如需有關 Visual Studio 訂閱的銷售、訂用帳戶、帳戶和計費的協助，請聯絡 Visual Studio [訂閱支援](https://visualstudio.microsoft.com/subscriptions/support/)。