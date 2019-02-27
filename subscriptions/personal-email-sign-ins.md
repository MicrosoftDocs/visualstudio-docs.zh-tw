---
title: 顯示於 VLSC 中的個人電子郵件
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/23/2018
ms.topic: conceptual
description: Visual Studio 訂閱 – 我為何會針對我的訂閱者看見 Hotmail 或 Gmail 地址？
searchscope: VS Subscription
ms.openlocfilehash: 0ba4029fcec0c8d35a58def14ab38afbb79e2fee
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843373"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Visual Studio 訂用帳戶 - 我為何會針對我的訂閱者看見 Hotmail 或 Gmail 地址？

隨著公司從大量授權服務中心 (VLSC) 移轉至新的 Visual Studio [訂閱管理入口網站](https://manage.visualstudio.com)，系統管理員可能會對於部分訂閱者的「登入電子郵件地址」是顯示為第三方電子郵件地址 (例如 Hotmail、Gmail 或 Yahoo) 感到訝異。  如需詳細資訊，請參閱[這段影片](https://www.youtube.com/watch?v=1op-i1zEMfY&t=0s&list=PLReL099Y5nRfDyvvwzNDBaZe7qTxmuM2T&index=6)。

## <a name="cause"></a>原因

此案例是因為與舊版 MSDN 訂閱者體驗相關聯的登入程序所造成。 使用者是從大量授權服務中心 (VLSC) 移轉到新的入口網站，而未經修改。 系統管理員可能未發覺使用者以個人帳戶來存取其訂用帳戶權益。 在於 2016 年完成的 Visual Studio 訂閱者移轉之前，若要成功使用 Visual Studio 訂閱，必須完成兩項動作：
1. 系統管理員使用個別訂閱者的公司或學校電子郵件地址，將訂閱「指派」給他們。
2. 該訂閱者「啟動」訂閱。

在訂閱者啟動程序期間：需要使用 Microsoft 帳戶 (MSA) 來登入。 若訂閱者沒有嘗試將其公司或學校帳戶 (例如 tasha@contoso.com) 轉換成 MSA，他們則可以建立新的 MSA 或使用現有的 MSA。 這導致其「登入電子郵件地址」和「指派電子郵件地址」有所不同。

> [!NOTE]
> [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) 上的新訂閱者體驗，同時支援公司/學校帳戶及 Microsoft 帳戶 (MAA) 身分識別類型。

最後，由於系統管理員移轉會使用來自 VLSC 有關訂閱者「登入電子郵件地址」的資料來填入新的訂閱者管理體驗，加上我們對新使用者介面所做出的變更會使這些個人帳戶變得更加容易看見，因此於近期完成移轉的系統管理員可能會看見這些先前沒有注意到的資訊。

## <a name="solution"></a>方案

若要更正此問題，您必須編輯訂閱者資訊以更新其登入電子郵件地址。  您可以對單一訂閱者進行編輯，或是大量做出編輯。 如需完整資訊，請造訪[編輯訂閱](edit-license.md)。

在您更新訂閱者的電子郵件地址之後，便應該通知他們其登入資訊已經變更。  他們也會收到一封包含更新資訊的電子郵件。