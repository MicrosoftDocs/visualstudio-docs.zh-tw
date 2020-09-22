---
title: 如何使用連線的 Microsoft 帳戶和 Azure Active Directory 的身分識別 |Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: 50ce0445-ef1a-4e92-b9d0-aebb2155a111
ms.date: 03/11/2020
ms.topic: conceptual
robots: noindex, nofollow
description: 瞭解如何使用已連接的 Microsoft 帳戶和 Azure Active Directory 身分識別
ms.openlocfilehash: 6d67576ab715f3ff8a49287155423a3dd6c20867
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005234"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>如何在 Visual Studio 訂用帳戶中使用連線的身分識別
如果您透過公司或學校收到 Visual Studio 的訂用帳戶，並使用您的 Microsoft 帳戶 (MSA) 登入，則您的訂用帳戶管理員可以將您的 MSA 連線到組織的 Azure Active Directory (Azure AD) 中的身分識別。  這將會變更您的訂用帳戶中所包含的一些優點。 

## <a name="overview-of-connected-ids"></a>已連線的識別碼總覽
組織逐漸移至以 Azure AD 為基礎的身分識別，以提供更佳的安全性和支援來管理訂閱的自動化。  如果您的訂用帳戶使用諸如 @outlook.com 或其他個人電子郵件地址等 MSA，則您的系統管理員可能會將您的登入電子郵件變更為您的 Azure AD 身分識別。  這將會變更如何登入訂閱者入口網站， https://my.visualstudio.com 但可能不會變更您存取擁有權益的方式。  

如果您的系統管理員連接您的 MSA 和 Azure AD 身分識別，您將會收到一封電子郵件，讓您知道如何使用 Azure AD 身分識別（而不是 MSA）來存取您的 Visual Studio 訂用帳戶。 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>如何使用 Azure AD 身分識別來存取權益
當系統管理員將您的 MSA 連接到您的 Azure AD 身分識別之後，您必須使用 Azure AD 身分識別登入訂閱者入口網站， https://my.visualstudio.com 以存取依賴 Azure AD 的權益。  其中包括：
- Visual Studio IDE
- Azure DevOps
- Azure DevTest 個人點數

## <a name="how-to-access-benefits-using-your-msa"></a>如何使用 MSA 存取權益
針對 Visual Studio 訂用帳戶（例如 Pluralsight、LinkedIn、CloudPilot 等等）所提供的許多優點，您實際上是在合作夥伴的網站上建立使用者帳戶。  針對這些帳戶，您應該繼續使用您在建立帳戶時所使用的身分識別。  例如，如果您使用 MSA 啟用了 Pluralsight 權益，不論您用來登入訂閱者入口網站的身分識別為何，都應該繼續使用您的 MSA 來進行 Pluralsight 訓練。  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>使用替代身分識別來存取您的訂用帳戶
將替代帳戶新增至 Visual Studio 訂用帳戶，可讓您使用與獲指派訂用帳戶不同的身分識別來存取訂用帳戶權益 (例如 Azure DevOps 和 Azure)。 過去，只有在將 Visual Studio (VS) 訂用帳戶指派給 Microsoft 帳戶 (MSA) 時，才能使用這項功能。 我們已擴充 Azure Active Directory (Azure AD) 中公司或學校帳戶的這個功能。  如需使用其他帳戶的詳細資訊，請參閱我們的 [替代](vs-alternate-identity.md) 身分識別文章。 

## <a name="frequently-asked-questions"></a>常見問題集
### <a name="q-how-can-i-contact-my-admin-about-this"></a>問：我要如何與我的系統管理員聯絡這種情況？
答：如需聯繫系統管理員的相關資訊，請參閱我們的 [訂閱系統管理員](contact-my-admin.md) 文章。  

### <a name="q-im-an-admin--how-do-i-use-this"></a>問：我是系統管理員。 如何? 使用此功能？
答：執行連接的身分識別很簡單。  如需詳細資訊，請查看[這篇文章](personal-email-sign-ins.md)。 

## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](/visualstudio/)
- [Azure DevOps 檔](/azure/devops/)
- [Azure 檔](/azure/)
- [Microsoft 365 檔](/microsoft-365/)

## <a name="next-steps"></a>下一步
當您的系統管理員連接您的 Azure AD 與 MSA 帳戶之後，建議您確認是否可以成功登入訂用帳戶 [入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs) ，並存取 Azure DevOps、Visual Studio 和 Azure DevTest 個別點數等權益。