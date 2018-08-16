---
title: 在您的組織移轉之後開始使用 Visual Studio 訂用帳戶系統管理入口網站
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 07/12/2018
Ms.topic: Get-Started-Article
Description: Learn how to successfully onboard your organization for Visual Studio subscriptions after migrating to the administration portal.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 4052d04669327ab0383aba91de05e4d8b95db4c5
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637451"
---
# <a name="onboarding-to-the-visual-studio-subscriptions-administration-portal-after-your-organization-was-migrated"></a>在您的組織移轉之後開始使用 Visual Studio 訂用帳戶系統管理入口網站 

若您在大量授權服務中心 (VLSC) 管理 Visual Studio 訂用帳戶，且最近曾經使用該網站來管理訂用帳戶，您將會注意到 VLSC 已不再提供訂用帳戶管理功能。 您管理訂用帳戶的程序看起來會像這樣：
> [!div class="mx-imgBorder"]
> ![VLSC 訂閱](_img/post-migration-onboarding/vlsc-subscriptions.png)

到達定帳戶頁面之後，您會按一下下面的連結。 
> [!div class="mx-imgBorder"]
> ![關聯性摘要連結](_img/post-migration-onboarding/relationship-summary-link.png)

這以前會將您帶到可以管理訂用帳戶的頁面。   不過，您現在必須透過稱為「Visual Studio 訂用帳戶系統管理入口網站」的新入口網站來管理訂用帳戶。  有數個步驟必須由您組織大量授權合約的主要連絡人或通知連絡人執行。 若主要或通知連絡人未完成此程序或已無法使用，則可能會發生一些情況。 下面會帶領您完成取得訂用帳戶管理存取權的步驟。 

您可能會遇到一或數種情況：
1.  [主要連絡人未完成上線程序](#Onboarding-not-completed-by-Primary-Contact)<sup>1</sup> 
2.  [主要連絡人已完成上線程序，但未將您加入為系統管理員。您的認證已列在 VLSC 中。](#Primary-Contact-did-not-provide-you-administrator-access) 
3.  [主要連絡人已完成上線程序，但未將您加入為系統管理員，且您的認證未列在 VLSC 中](#Your-credentials-were-not-listed-in-VLSC-prior-to-migration)  

<sup>1</sup> 若您是主要或通知連絡人且未完成上線程序，您將必須依照情節一中的步驟完成設定組織的作業。 

下面是您將會看到的每個情節的的畫面範例與您可以採取的步驟。 

## <a name="onboarding-not-completed-by-primary-contact"></a>主要連絡人未完成上線程序

若主要連絡人未完成上線程序，您應該會看到如下畫面。 若您可以存 [大量授權服務中心 (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx)，則您將能完成此程序並取得訂用帳戶管理存取權。 您需要組織的[公開客戶號碼 (PCN)](find-pcn.md) (可在 VLSC 中找到)。 

若主要連絡人未完成上線程序，只要在欄位中輸入 [PCN](find-pcn.md) 並選取 [送出邀請函]。 
> [!div class="mx-imgBorder"]
> ![傳送邀請電子郵件](_img/post-migration-onboarding/send-invitation.png)

一旦按一下該按鈕以傳送邀請函，您將會收到電子郵件，其中包含完成上線程序的唯一連結。 您將需要按一下該電子郵件中的連結、使用您的電子郵件地址登入，然後再次輸入 PCN。 該電子郵件中的唯一連結可讓您啟用對 Visual Studio 訂用帳戶系統管理入口網站的存取權。 接著，您將能存取及管理訂用帳戶。 
> [!div class="mx-imgBorder"]
> ![電子郵件成功](_img/post-migration-onboarding/email-success.png)


## <a name="primary-contact-did-not-provide-you-administrator-access"></a>主要連絡人未提供系統管理員存取權給您

若您的主要連絡人已完成上線程序，且您的認證之前曾列於 VLSC 中，但主要連絡人未提供存取權給您，當您登入 [Visual Studio 訂用帳戶系統管理入口網站](https://manage.visualstudio.com/)時將會看到下列通知。  若要成為系統管理員，您將需要連絡畫面上所列的其中一個貴組織的超級系統管理員。
> [!div class="mx-imgBorder"]
> ![系統管理員清單](_img/post-migration-onboarding/admin-list.png)

## <a name="your-credentials-were-not-listed-in-vlsc-prior-to-migration"></a>您的認證在移轉前未曾列在 VLSC 中

若您的主要連絡人已完成上線程序，但未將您加入為使用者，且您的認證先前未曾列在 VLSC 中，當您嘗試存取 [Visual Studio 訂用帳戶系統管理入口網站](https://manage.visualstudio.com/)時將會看到下列通知。 您將需要連絡您的[主要連絡人](find-primary-contact.md)以取得入口網站存取權。 
> [!div class="mx-imgBorder"]
> ![找不到您](_img/post-migration-onboarding/cant-find-you.png)