---
title: 如何使用連接的 Microsoft 帳戶和 Azure 活動目錄標識 |微軟文檔
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/11/2020
ms.topic: conceptual
robots: noindex, nofollow
description: 瞭解如何使用連接的 Microsoft 帳戶和 Azure 活動目錄標識
ms.openlocfilehash: 3dcb41a26f27e5135962edf7ff933de40ccefe5e
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "79508975"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>如何在視覺化工作室訂閱中使用連接的標識
如果您通過工作或學校收到 Visual Studio 訂閱，並且使用 Microsoft 帳戶 （MSA） 登錄，則訂閱管理員可能會將 MSA 連接到組織的 Azure 活動目錄 （Azure AD） 中的身份。  這將更改您訪問訂閱中包含的某些權益的方式。 

## <a name="overview-of-connected-ids"></a>連接的 I 的概述
組織越來越多地遷移到基於 Azure AD 的標識，以改進訂閱的自動化管理安全性和支援。  如果您的訂閱使用 MSA（如或其他@outlook.com個人電子郵件地址），則管理員可能會將登錄電子郵件更改為 Azure AD 標識。  這將更改登錄訂閱者門戶的方式，https://my.visualstudio.com但可能不會更改您訪問擁有權益的方式。  

如果管理員連接您的 MSA 和 Azure AD 標識，您將收到一封電子郵件，通知您可以使用 Azure AD 標識而不是 MSA 開始訪問 Visual Studio 訂閱。 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>如何使用 Azure AD 標識訪問權益
管理員將 MSA 連接到 Azure AD 標識後，需要使用 Azure AD 標識登錄到訂閱https://my.visualstudio.com伺服器門戶，以訪問依賴于 Azure AD 的優勢。  其中包括：
- Visual Studio IDE
- Azure DevOps
- Azure DevTest 個人點數

## <a name="how-to-access-benefits-using-your-msa"></a>如何使用 MSA 訪問權益
對於 Visual Studio 訂閱中提供的許多好處（如複數、LinkedIn、CloudPilot 等），您實際上在合作夥伴的網站上創建使用者帳戶。  對於這些帳戶，應繼續使用創建帳戶時使用的標識。  例如，如果您使用 MSA 啟動了複數權益，則在進行複數訪問培訓時應繼續使用 MSA，而不管使用何種身份登錄到訂閱者門戶。  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>使用備用標識訪問訂閱
將替代帳戶新增至 Visual Studio 訂用帳戶，可讓您使用與獲指派訂用帳戶不同的身分識別來存取訂用帳戶權益 (例如 Azure DevOps 和 Azure)。 過去，只有在將 Visual Studio (VS) 訂用帳戶指派給 Microsoft 帳戶 (MSA) 時，才能使用這項功能。 我們已擴充 Azure Active Directory (Azure AD) 中公司或學校帳戶的這個功能。  有關使用備用帳戶的詳細資訊，請查看我們的[備用標識](vs-alternate-identity.md)文章。 

## <a name="frequently-asked-questions"></a>常見問題集
### <a name="q-how-can-i-contact-my-admin-about-this"></a>問：如何聯繫我的管理員？
答：有關聯繫管理員的資訊，請參閱我們的["聯繫您的訂閱管理員"](contact-my-admin.md)文章。  

## <a name="see-also"></a>另請參閱
- [視覺化工作室文檔](https://docs.microsoft.com/visualstudio/)
- [Azure 開發人員文檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [微軟 365 文檔](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>後續步驟
管理員連接 Azure AD 和 MSA 帳戶後，我們建議驗證是否可以成功登錄到[訂閱門戶](https://my.visualstudio.com?wt.mc_id=o~msft~docs)並訪問 Azure DevOps、Visual Studio 和 Azure DevTest 個人積分等權益。 