---
title: 在移轉後，上架至 Visual Studio 訂用帳戶管理入口網站
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 07/12/2018
ms.topic: conceptual
description: 了解如何在移轉至管理入口網站後，成功將組織上架於 Visual Studio 訂用帳戶。
searchscope: VS Subscription
ms.openlocfilehash: 3916fd762e9a2feaaa4892e4233d08a345db44a1
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954224"
---
# <a name="onboard-to-the-visual-studio-subscriptions-administration-portal-after-your-organization-is-migrated"></a>在您的組織移轉之後，上架至 Visual Studio 訂用帳戶系統管理入口網站

若您在 Microsoft 大量授權服務中心 (VLSC) 管理 Visual Studio 訂用帳戶，且最近曾經使用該網站來管理訂用帳戶，您將會注意到 VLSC 已不再提供訂用帳戶管理功能。 您管理訂用帳戶的程序看起來會像這樣：
> [!div class="mx-imgBorder"]
> ![Microsoft VLSC 的螢幕擷取畫面，其中 [訂用帳戶] 索引標籤已反白顯示](_img/post-migration-onboarding/vlsc-subscriptions.png)

不過，您現在必須透過稱為「Visual Studio 訂用帳戶系統管理入口網站」的新入口網站來管理訂用帳戶。 組織大量授權合約的主要連絡人或通知連絡人通常會完成此程序。 如果沒有，下列資訊可協助您取得管理訂用帳戶的存取權。

您可能會遇到其中一種情節：

1. [主要連絡人未完成上線程序。](#Onboarding-not-completed-by-Primary-Contact)<sup>1</sup> 
2. [主要連絡人已完成上線程序，但未將您加入為系統管理員。您的認證已列在 VLSC 中。](#Primary-Contact-did-not-provide-you-administrator-access) 
3. [主要連絡人已完成上線程序，但未將您加入為系統管理員。您的認證未列在 VLSC 中。](#Your-credentials-were-not-listed-in-VLSC-prior-to-migration)  

<sup>1</sup> 若您是主要或通知連絡人且未完成上線程序，您將必須依照情節一中的步驟完成設定組織的作業。

下列各節提供有關這些情節的詳細資料。

## <a name="onboarding-not-completed-by-primary-contact"></a>主要連絡人未完成上線程序

若主要連絡人未完成上線程序，您會看到以下畫面。 若您可以存取[大量授權服務中心 (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx)，您就能完成此程序並取得管理訂用帳戶的存取權。 您需要組織的[公開客戶號碼 (PCN)](find-pcn.md) (可以在 VLSC 中找到)。

在 [PCN] 欄位中，輸入 [PCN](find-pcn.md)，然後選取 [傳送邀請電子郵件]。
> [!div class="mx-imgBorder"]
> ![Visual Studio 訂用帳戶系統管理入口網站的螢幕擷取畫面](_img/post-migration-onboarding/send-invitation.png)

您會收到一封電子郵件，內含完成上線程序的唯一連結。 按一下該電子郵件中的連結、使用您的電子郵件地址登入，然後再次輸入 PCN。 該電子郵件中的唯一連結可讓您啟用對 Visual Studio 訂用帳戶系統管理入口網站的存取權。 您就可以存取和管理訂用帳戶。
> [!div class="mx-imgBorder"]
> ![成功通知的螢幕擷取畫面](_img/post-migration-onboarding/email-success.png)

## <a name="primary-contact-did-not-provide-you-administrator-access"></a>主要連絡人未提供系統管理員存取權給您

若您的主要連絡人已完成上線程序，且您的認證之前曾列於 VLSC 中，但主要連絡人未提供存取權給您，您會看到下列通知。 若要成為系統管理員，請連絡通知上所列的其中一個貴組織的超級系統管理員。
> [!div class="mx-imgBorder"]
> ![Visual Studio 訂用帳戶系統管理入口網站列出超級系統管理員的螢幕擷取畫面](_img/post-migration-onboarding/admin-list.png)

## <a name="your-credentials-were-not-listed-in-vlsc-prior-to-migration"></a>您的認證在移轉前未曾列在 VLSC 中

若您的主要連絡人已完成上線程序，但未將您加入為使用者，且您的認證先前未曾列在 VLSC 中，您會看到下列通知。 請連絡您的[主要連絡人](find-primary-contact.md)以取得入口網站存取權。
> [!div class="mx-imgBorder"]
> ![Visual Studio 訂用帳戶系統管理入口網站包含「找不到您」通知的螢幕擷取畫面](_img/post-migration-onboarding/cant-find-you.png)