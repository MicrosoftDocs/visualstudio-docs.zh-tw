---
title: 如何使用已連線的 Microsoft 帳戶和 Azure Active Directory 身分識別 |Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 09/27/2019
ms.topic: conceptual
robots: noindex, nofollow
description: 瞭解如何使用已連線的 Microsoft 帳戶和 Azure Active Directory 身分識別
ms.openlocfilehash: d0d30092f34a3cb17b41455612cd336af3e58d30
ms.sourcegitcommit: 13decf878b33fc0c5d665a88067170c2861b261b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71682155"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>如何在 Visual Studio 訂用帳戶中使用已連線的身分識別
如果您透過公司或學校收到 Visual Studio 訂用帳戶，並使用您的 Microsoft 帳戶（MSA）登入，則您的訂閱管理員可以將您的 MSA 連線到貴組織 Azure Active Directory （Azure AD）中的身分識別。  這會變更您的訂用帳戶中所含權益的存取方式。 

## <a name="overview-of-connected-ids"></a>已連線識別碼的總覽
組織逐漸轉移到 Azure AD 的身分識別，以提供更佳的安全性和支援來管理訂用帳戶的自動化。  如果您的訂用帳戶使用 MSA，例如 @outlook.com 或其他個人電子郵件地址，您的系統管理員可能會將您的登入電子郵件變更為您的 Azure AD 身分識別。  這會變更在 https://my.visualstudio.com 登入訂閱者入口網站的方式，但可能不會變更您存取擁有權益的方式。  

如果您的系統管理員連接到您的 MSA 和 Azure AD 身分識別，您會收到一封電子郵件，告訴您要使用 Azure AD 身分識別開始存取您的 Visual Studio 訂用帳戶，而不是您的 MSA。 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>如何使用 Azure AD 身分識別存取權益
當您的系統管理員將 MSA 連線到您的 Azure AD 身分識別之後，您必須使用您的 Azure AD 身分識別登入位於 https://my.visualstudio.com 的訂閱者入口網站，以存取依賴 Azure AD 的權益。  它們包括：
- Visual Studio IDE
- Azure DevOps
- Azure 點數

## <a name="how-to-access-benefits-using-your-msa"></a>如何使用您的 MSA 存取權益
如需 Visual Studio 訂用帳戶（例如 Pluralsight、LinkedIn、CloudPilot 等）中所提供的許多優點，您實際上是在合作夥伴的網站上建立使用者帳戶。  針對這些帳戶，您應該繼續使用您在建立帳戶時所使用的身分識別。  例如，如果您使用 MSA 啟用您的 Pluralsight 權益，不論您用來登入訂閱者入口網站的身分識別為何，都應該在採取 Pluralsight 訓練時繼續使用您的 MSA。  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>使用替代的身分識別來存取您的訂用帳戶
將替代帳戶新增至 Visual Studio 訂用帳戶，可讓您使用與獲指派訂用帳戶不同的身分識別來存取訂用帳戶權益 (例如 Azure DevOps 和 Azure)。 過去，只有在將 Visual Studio (VS) 訂用帳戶指派給 Microsoft 帳戶 (MSA) 時，才能使用這項功能。 我們已擴充 Azure Active Directory (Azure AD) 中公司或學校帳戶的這個功能。  如需使用其他帳戶的詳細資訊，請參閱我們的[替代](vs-alternate-identity.md)身分識別一文。 

## <a name="frequently-asked-questions"></a>常見問題集
### <a name="q-how-can-i-contact-my-admin-about-this"></a>問：我要如何與我的系統管理員聯絡這種情況？
答：如需與系統管理員聯繫的相關資訊，請參閱我們的[訂閱管理員](contact-my-admin.md)文章。  

## <a name="next-steps"></a>後續步驟
當您的系統管理員連接到您的 Azure AD 和 MSA 帳戶之後，建議您確認可以成功登入訂用帳戶[入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs)，並存取 Azure DevOps、Visual Studio 和您的 Azure 信用額度等權益。 