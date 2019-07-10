---
title: 處理過度領取的授權 | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 02/13/2018
ms.topic: conceptual
description: 了解系統管理員如何解決過度領取訂閱的問題
searchscope: VS Subscription
ms.openlocfilehash: 06da8c460e9660857b0f03062bde5bd983bd176d
ms.sourcegitcommit: 32144a09ed46e7223ef7dcab647a9f73afa2dd55
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2019
ms.locfileid: "67586995"
---
# <a name="overallocated-subscriptions"></a>超額配置的訂用帳戶

有時，在新增訂閱者之後訂單也有所變更，而可能導致已指派的訂閱數超過公司所擁有的授權數。 發生這種情況時，[訂閱者] 索引標籤會顯示警示，並提供進一步資訊。

> [!NOTE]
> Open License 方案不允許過度領取的情況。  此外，其他程式在入口網站中可能會以不同的方式顯示此資訊。
>
> [!div class="mx-imgBorder"]
> ![過度領取的訂閱通知](_img/over-claimed/over-claimed-alert.png)

## <a name="resolving-overallocated-subscriptions"></a>解決超額配置訂用帳戶的問題

若要解決超額配置授權的問題：

1. 按一下警示文字。 隨即顯示一份篩選清單，其中顯示已指派訂閱層級的訂閱者，以及過度領取的到期日。 

2. 視需要移除訂閱者，以更正過度領取授權的情況。 

3. 頁面左側的概觀即會更新並顯示您目前又回到合規狀態，所有過度領取的通知都會消失。 

## <a name="billing-and-true-up"></a>計費與校正

如果您的組織有 Enterprise 合約 (EA)，系統管理員不必購買訂用帳戶即可加以指派，並在稍後透過稱為「校正」的對帳流程支付其費用。  當您超額配置時，您的組織會需要在「校正」期間，為指派給使用者的訂用帳戶最大數目付費。  即使您在校正進行的當下已不再指派訂用帳戶的最大數目，也是如此。  若要深入了解如何監視您的最大使用量，請瀏覽[最大使用量](maximum-usage.md)主題。

> [!Important]
> 如果含 GitHub Enterprise 的 Visual Studio 訂用帳戶由 Visual Studio 訂用帳戶系統管理員指派，而且過去未曾購買過這些訂用帳戶，就不會在組織中向 GitHub Enterprise 系統管理員顯示。 若要確保 GitHub Enterprise 訂用帳戶確實顯示，就必須在初次指派訂用帳戶時，購買**至少一個**含 GitHub Enterprise 的 Visual Studio Professional 或含 GitHub Enterprise 的 Visual Studio Enterprise。  
>
> 客戶必須負責確保指派的每個 GitHub 訂用帳戶都對應一個含 GitHub 的 Visual Studio 訂用帳戶 (在管理入口網站中指派)，以保持符合這個訂用帳戶的授權需求。

深入了解如何管理[含 GitHub Enterprise 的 Visual Studio 訂用帳戶](assign-github.md)。

## <a name="support-resources"></a>支援資源

- 如需 Visual Studio 訂用帳戶有關銷售、訂閱、帳戶與計費的協助，請聯繫 Visual Studio [訂用帳戶支援](https://visualstudio.microsoft.com/subscriptions/support/)。
