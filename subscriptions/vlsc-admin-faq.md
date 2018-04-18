---
title: VLSC 管理移轉常見問題集 | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/13/2018
ms.topic: Get-Started-Article
description: 大量授權服務中心系統管理移轉常見問題集
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 014564880dcc7587a1f94e3815d6f36edb36cee3
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2018
---
# <a name="visual-studio-subscriptions-administration-migration"></a>Visual Studio 訂閱系統管理移轉

在接下來幾個月，對 Visual Studio 訂閱 (先前稱為 MSDN 訂閱) 的管理將會有所變更。 目前，您可以透過「大量授權」購買 Visual Studio 訂閱，而訂閱的管理會在「大量授權服務中心」入口網站 (VLSC) 中進行。 現在正在建立一個新版管理入口網站，未來將會在這個新版入口網站中管理 Visual Studio 訂閱。 除了 VLSC 所提供的現有作業之外，新版入口網站還將允許沒有限制的大量指派、追蹤和篩選訂閱，以及能夠利用 Azure Active Directory (Azure AD) 來管理存取。 新版「Visual Studio 系統管理入口網站」將位於：[https://manage.visualstudio.com](https://manage.visualstudio.com)。 

> [!Note] 
> 此移轉將不會影響 MPSA 客戶。 

## <a name="frequently-asked-questions"></a>常見問題集

### <a name="why-is-it-changing"></a>為何要進行變更？
新版入口網站將提供最佳的 Visual Studio 訂閱管理體驗，並且會建立單一的 Visual Studio 訂閱管理體驗，而不論其購買方式為何。 新版入口網站提供一個新平台，可啟用 Azure AD 並讓我們為未來做好準備。 此外，它也將有一個已更新的使用者介面，更易於瀏覽和使用，讓系統管理員工作更有效率。

### <a name="who-will-be-impacted"></a>誰會受到影響？ 
此變更將影響所有具有有效「大量授權」合約且已透過「大量授權」購買「Visual Studio 訂閱」的客戶。 

### <a name="when-is-it-changing"></a>何時要進行變更？
這是一個大規模的轉換，將會分階段完成，直到所有具備「Visual Studio 訂閱」有效「大量授權」合約的客戶都移轉至新版管理入口網站為止。 此移轉已從 2017 年第一季開始進行。 我們會在為「大量授權」客戶排定移轉的當週之前，事先通知他們。  

### <a name="does-my-organization-need-to-sign-up-for-azure-active-directory-azure-ad"></a>我的組織是否需要註冊 Azure Active Directory (Azure AD)？
組織不需要註冊 Azure AD，但您可以隨時註冊。 如果您選擇在 Azure AD 上線，就可以使用 Azure AD 的免費層，無須支付任何費用，即可達到此目的。 搭配 Azure Active Directory 時，您將可提升組織的安全性、控制及長期可靠性，來為組織提供安全防護。 不過，如果您尚未做好使用 Azure AD 的準備，則將能夠像目前一樣繼續使用「Microsoft 帳戶」(MSA)。 

### <a name="how-do-i-know-when-my-organization-will-be-migrated"></a>如何知道何時會移轉我的組織？
我們將會寄送電子郵件給「主要/通知連絡人」，邀請他們在組織移轉的一週前完成上線程序。 「訂閱管理員」也會收到電子郵件，告知他們我們已連絡「主要/通知連絡人」，並已提供有關如何協助確保上線成功的詳細資料。 了解如何[尋找組織的主要/通知連絡人](#How-do-I-find-out-who-my-Primary-or-Notices-Contact-is?)。 

### <a name="is-onboarding-different-from-migration"></a>上線與移轉是否不同？
是。  此程序包含兩個階段。 在移轉前將組織設定好 (或上線) 可確保您的系統管理員工作不會受到干擾。 在我們移轉組織的資訊之後，您就能夠在新版入口網站中管理 Visual Studio 訂閱。 如果「主要/通知連絡人」未在移轉前執行上線程序，「訂閱管理員」將會被系統封鎖而無法管理訂閱，直到您完成上線程序為止。 

### <a name="what-is-the-onboarding-process"></a>什麼是上線程序？
「主要/通知連絡人」將會收到邀請他們完成上線程序的電子郵件。 請參閱下面有關此程序的指示。 
1.  **尋找您的 PCN 並登入：**

    a.  在電子郵件中，會提供「主要/通知連絡人」一個唯一的連結及其「公開客戶編號」(PCN) 的末三碼。* 

    b.  為取得完整的 PCN，「主要連絡人」將需要登入 VLSC (可以在下面找到尋找 PCN 的指示)。 

    c.   取得 PCN 之後，他們需要選取提示他們登入的唯一連結。 他們將能夠使用工作/學校帳戶 (如果組織在 Azure AD 中) 或 Microsoft 帳戶 (MSA) (如果組織不在 Azure AD 中) 來登入。 

    d.  接著，系統會提示他們輸入 PCN。 

2.  **設定您的系統管理員：**

    輸入 PCN 之後，系統會將他們引導至可供他們新增超級管理員和系統管理員 (先前稱為「訂閱管理員」) 的頁面。 在理想的情況下，這應該在組織的移轉日期之前完成，如此才不會干擾您的訂閱管理工作。 

3.  **存取新版訂閱管理入口網站：**移轉組織之後，將會傳送電子郵件給超級管理員和系統管理員，邀請他們存取新版入口網站以開始管理訂閱。 

> [!NOTE] 
> 如果「主要連絡人」或「通知連絡人」收到多封電子郵件，即表示他們有多個 PCN。 他們將需要使用每封電子郵件中所參考的唯一 PCN 連結來完成程序。 

### <a name="what-is-the-difference-between-a-super-admin-and-an-administrator"></a>超級管理員與系統管理員之間有何差異？
當「主要/通知連絡人」第一次登入時，系統會自動將他們設定為超級管理員。超級管理員可以藉由新增/刪除其他超級管理員或系統管理員，來管理系統管理員對訂閱的存取，而且也可以管理訂閱。 超級管理員可以選擇除了自己之外，再指派其他超級管理員。

系統管理員 (先前稱為「訂閱管理員」) 只能管理訂閱，但無法控制誰對管理訂閱擁有存取權。 

### <a name="how-will-i-as-an-administrator-onboard-to-the-new-portal"></a>如果我是系統管理員，要如何在新版入口網站上線？
組織的「主要管理員」和「通知管理員」將會收到電子郵件，內含一個唯一的連結，會將他們引導至一個可供他們使用工作或學校帳戶 (由 Azure Active Directory (Azure AD) 或個人 MSA 支援) 登入的頁面。 登入之後，他們將需要輸入組織的「公開客戶編號」(PCN) 或「授權編號」以驗證合約。 接著，系統會將他們設定為超級管理員，使其能夠新增其他系統管理員 (例如您) 來管理 Visual Studio 訂閱。 

### <a name="where-do-i-manage-subscriptions-if-my-organization-has-been-onboarded-but-hasnt-been-migrated"></a>如果我的組織已經上線但尚未移轉，要在哪裡管理訂閱？ 
您將繼續透過 VLSC 管理訂閱，直到您收到來自「Visual Studio 訂閱」的電子郵件，通知您已移轉組織並已可在新版入口網站中進行管理為止。 

### <a name="where-can-i-locate-my-organizations-public-customer-number-pcn-or-authorization-number"></a>要到哪裡尋找我組織的「公開客戶編號」(PCN) 或「授權編號」？
請登入 [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx)，然後瀏覽下列路徑：[訂閱] > [Visual Studio 訂閱]。 PCN 會位在 [合約/公開客戶編號結果] 底下。 請參閱這篇[說明文章](/find-pcn/)，了解有關尋找 PCN 的逐步指引。 

### <a name="how-do-i-find-out-who-my-primary-or-notices-contact-is"></a>要如何找出誰是我的主要或通知連絡人？
請登入 [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx)，然後瀏覽下列路徑：[授權] > [關聯摘要]。選取您的 [授權識別碼] > [連絡人]。 請參閱這篇[說明文章](/find-primary-contact/)，了解有關尋找「主要連絡人」或「通知連絡人」的逐步指引。 

### <a name="what-if-my-primary-or-notices-contact-is-gone-no-longer-with-the-company-or-not-available-to-complete-onboarding"></a>如果我的主要或通知連絡人不見、已離職或無法完成上線工作時，該怎麼辦？
您將需要[連絡支援人員](https://www.visualstudio.com/subscriptions/support/#talktous)，並提供您在 VLSC 中用來管理訂閱的電子郵件。 驗證之後，支援人員將能夠協助您進行上線程序。 

### <a name="what-will-happen-with-renewing-customers"></a>正在更新的客戶會發生什麼情況？ 
正在更新的客戶應該如常繼續更新其訂閱，因為更新程序不受移轉影響。 

### <a name="should-my-organization-wait-to-set-up-a-new-agreement-in-the-new-system-rather-than-renew-an-existing-agreement"></a>我的組織是否應該等候在新系統中設定新合約，而不是更新現有的合約？ 
否。  移轉不會影響合約的建立或更新。 

### <a name="what-if-my-organizations-agreement-is-in-the-grace-period-during-the-transition-will-they-also-be-migrated"></a>如果我組織的合約在轉換期間處於寬限期，該怎麼辦？ 它們是否也會一併移轉？
是，如果合約仍然有效，將會移轉組織。 

### <a name="what-if-my-organization-has-over-claimed-in-the-current-system-will-we-still-be-migrated-to-the-new-system"></a>如果我組織在目前的系統中已經越權，該怎麼辦？ 是否仍會將我們移轉至新系統？ 
是，仍會將組織移轉至新系統。 越權能力 (適用於允許此情況的合約類型) 將存在於新系統中。 

### <a name="what-if-my-organization-has-more-than-one-subscription-assigned-to-a-single-useremail-address"></a>如果我的組織有多個訂閱指派給單一使用者/電子郵件地址，該怎麼辦？
仍會移轉組織。  不過，您將無法指派相同層級 (亦即：Enterprise、Professional 等) 的任何額外訂閱給該使用者/電子郵件地址。 任何具有相同電子郵件地址的相同層級訂閱在移轉時仍然可見，但系統管理員將需要變更電子郵件地址，使它們成為唯一的。 在新版入口網站中，您將無法指派多個相同層級的訂閱給單一使用者/電子郵件地址。

### <a name="where-can-i-find-the-most-up-to-date-information-about-the-migration"></a>我可以在哪裡找到有關移轉的最新資訊？ 
如需有關此移轉的最新資訊，請瀏覽我們的「Visual Studio 訂閱」系統管理員[網頁](https://aka.ms/vs-admin)。 如果您需要支援，請查看 Visual Studio 訂閱[支援頁面](http://www.visualstudio.com/subscriptions/support/#!collections/962-subscriptions)，其中包含自助資訊和支援連絡資訊。 在接下來的幾個月，我們將繼續提供有關系統管理員網頁的更新，並透過電子郵件協助輕鬆進行這項轉換。 

## <a name="resources-and-support-information"></a>資源和支援資訊
- [系統管理員網頁](https://www.visualstudio.com/subscriptions-administration/)

- Visual Studio 訂閱和管理[支援](https://www.visualstudio.com/subscriptions/support/) 

- [如何尋找我的 PCN](/find-pcn/)

- [如何尋找我的主要或通知連絡人](/find-primary-contact/) 

- 讓組織上線及管理系統管理員的[影片](https://www.youtube.com/watch?v=ZmnywYGSFMg&list=PLReL099Y5nRfDyvvwzNDBaZe7qTxmuM2T&index=1&t=0s) 
