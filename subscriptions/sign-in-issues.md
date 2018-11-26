---
title: 登入 Visual Studio 訂用帳戶的問題 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 11/07/2018
ms.topic: conceptual
description: 了解登入 Visual Studio 訂用帳戶時可能遇到的問題
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 0883e5228a44f0df80e9de912029e21545d5ec2a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51811218"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>登入 Visual Studio 訂用帳戶的問題
若要使用 Visual Studio 訂用帳戶，您必須先登入。  視您的訂用帳戶而定，您可能已使用 Microsoft 帳戶 (MSA) 或 Azure Active Directory (AAD) 身分識別加以設定。  本文將討論一些登入訂用帳戶時可能會遇到的問題。  

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>無法使用工作/學校電子郵件地址建立 Microsoft 帳戶 (MSA)

在 Azure AD 中設定電子郵件網域時，不再允許使用工作/學校電子郵件地址建立新個人 Microsoft 帳戶 (MSA) 的功能。 這代表什麼呢？ 如果您的組織使用 Office 365 或是 Microsoft 中依賴 Azure AD 的其他商務服務，而且您已在 Azure AD 租用戶中新增網域名稱，則使用者再也無法使用網域中的電子郵件地址建立新個人 Microsoft 帳戶。 

### <a name="why-was-this-change-made"></a>為什麼要進行這項變更？

擁有以工作地址作為使用者名稱的個人 Microsoft 帳戶，對終端使用者和 IT 部門來說都充滿了問題。 例如:  
- 使用者可能認為其個人 Microsoft 帳戶符合商務規範，而且當他們將商務文件儲存到其 OneDrive 時符合規範 
- 離開組織的使用者通常無法再存取其工作電子郵件地址。 當他們這麼做時，如果已忘記其密碼，可能無法回到其個人的 Microsoft 帳戶。 另一方面，其 IT 部門可以重設他們的密碼，並進入離職員工的個人帳戶。 
- IT 部門對於帳戶擁有權及安全性具有錯誤的認知。 但是，使用者只需要將程式碼往返其工作電子郵件地址一次，並且可以在未來隨時重新命名其帳戶。 

對於擁有兩個帳戶且這些帳戶使用相同電子郵件地址 (一個在 Azure AD，一個在 Microsoft 帳戶) 的使用者，此情況特別令人混淆。 

### <a name="what-does-this-experience-look-like"></a>這項體驗會產生什麼結果？

如果您嘗試使用工作或學校電子郵件地址註冊 Microsoft 消費者應用程式，您會看到下列訊息。 

   > [!div class="mx-imgBorder"]
   > ![無法使用工作電子郵件建立帳戶](_img/sign-in-issues/cannot-use-work-email.png)

不過，如果您嘗試註冊支援個人和工作/學校帳戶的 Microsoft 應用程式，則應該會看到此訊息：

   > [!div class="mx-imgBorder"]
   > ![支援的工作/學校帳戶](_img/sign-in-issues/existing-account.png)

### <a name="are-existing-accounts-affected"></a>現有的帳戶是否受到影響？
此處所述的註冊封鎖只會禁止建立新帳戶。 它對已擁有使用工作/學校電子郵件地址之 Microsoft 帳戶的使用者沒有任何影響。 如果您已處在這種情況下，我們可讓您更輕鬆地重新命名個人 Microsoft 帳戶。 本[技術支援文章](http://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account)提供簡單的逐步指引。 重新命名您的個人 Microsoft 帳戶表示變更使用者名稱，並不會影響您的工作電子郵件或登入 Office 365 等商務服務的方式。 它也不會影響您的個人資料，只會變更您的登入方式。 您可以使用其他 (個人) 電子郵件地址、從 Microsoft 取得新的 @outlook.com 電子郵件地址，或使用您的電話號碼作為新使用者名稱。 

> [!NOTE]
> 比方說，如果您的 IT 部門要求您使用工作/學校電子郵件來建立個人 Microsoft 帳戶以存取頂級支援等 Microsoft 商務服務，則請先洽詢管理員小組，再重新命名您的帳戶。 

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>刪除登入位址可能會禁止存取訂用帳戶

如果您刪除一或多個與訂用帳戶建立關聯的身分識別 (MSA 或 AAD)，則您包括使用者名稱和登入識別碼的訂閱者資訊可能會匿名呈現，導致您無法存取訂用帳戶。 

若要避免對訂用帳戶存取造成影響，請使用下列其中一種方法。  
- 部署單一身分識別管理系統 (MSA 或 AAD)，但不能同時部署。  
- 透過租用戶建立 AAD 與 MSA 身分識別的關聯。 


## <a name="next-steps"></a>後續步驟
- 了解如何在 AAD 內[連結 MSA 與 AAD 帳戶](/azure/active-directory/b2b/add-users-administrator)。
- 深入了解[匿名化](anonymization.md)。 
