---
title: 處理過度分派的授權 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: 了解系統管理員如何解決過度分派訂閱的問題
ms.openlocfilehash: 924f6fb2c513d70aefd28c1d4ff18d1af62178c2
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605515"
---
# <a name="overallocated-subscriptions"></a>超額配置的訂用帳戶
有時，在新增訂閱者之後訂單也有所變更，而可能導致已指派的訂閱數超過公司所擁有的授權數。 這稱為「過度分派」。  發生這種情況時，[訂閱者] 索引標籤會顯示警示，並提供有關已過度分派多少訂閱的進一步資訊。

> [!NOTE]
> Open License 方案不允許過度分派。  此外，其他程式在入口網站中可能會以不同的方式顯示此資訊。
>
> [!div class="mx-imgBorder"]
> ![過度領取的訂閱通知](_img/over-claimed/over-claimed-alert.png)

## <a name="resolve-overallocated-subscriptions"></a>解決過度分派的訂閱
有幾個方式可以解決過度分派：
- 聯絡您的轉銷商以購買額外的訂閱。
- 等到您的年度校正期間，然後在該時間點針對過度分派的訂閱支付費用。 
- 刪除部分訂閱指派。  (這無法排除每年校正時的付款需求，因為校正是以一年中在任何時間指派的最大訂閱數為依據。)

## <a name="billing-and-true-up"></a>計費與校正
如果您的組織有 Enterprise 合約 (EA)，系統管理員不必購買訂用帳戶即可加以指派，並在稍後透過稱為「校正」的對帳流程支付其費用。  當您超額配置時，您的組織會需要在「校正」期間，為指派給使用者的訂用帳戶最大數目付費。  即使您在校正進行的當下已不再指派訂用帳戶的最大數目，也是如此。  若要深入了解如何監視您的最大使用量，請瀏覽[最大使用量](maximum-usage.md)主題。

> [!Important]
> 如果含 GitHub Enterprise 的 Visual Studio 訂用帳戶由 Visual Studio 訂用帳戶系統管理員指派，而且過去未曾購買過這些訂用帳戶，就不會在組織中向 GitHub Enterprise 系統管理員顯示。 若要確保 GitHub Enterprise 訂用帳戶確實顯示，就必須在初次指派訂用帳戶時，購買**至少一個**含 GitHub Enterprise 的 Visual Studio Professional 或含 GitHub Enterprise 的 Visual Studio Enterprise。
>
> 客戶必須負責確保指派的每個 GitHub 訂用帳戶都對應一個含 GitHub 的 Visual Studio 訂用帳戶 (在管理入口網站中指派)，以保持符合這個訂用帳戶的授權需求。

## <a name="next-steps"></a>後續步驟
- 深入了解如何管理[含 GitHub Enterprise 的 Visual Studio 訂用帳戶](assign-github.md)。
- 如需 Visual Studio 訂用帳戶有關銷售、訂閱、帳戶與計費的協助，請聯繫 Visual Studio [訂用帳戶支援](https://visualstudio.microsoft.com/subscriptions/support/)。
