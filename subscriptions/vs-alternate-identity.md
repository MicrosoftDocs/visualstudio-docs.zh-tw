---
title: Visual Studio 訂閱者身分識別
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 86f2856c-8adf-4085-9962-f4136679e5ed
ms.date: 02/02/2021
ms.topic: conceptual
description: 如何新增 Visual Studio 訂用帳戶的替代身分識別，以用於 Azure DevOps 和 Azure
ms.openlocfilehash: 200f299ba4e487e40572e54f1066ed6ac079e7d1
ms.sourcegitcommit: b0ecf9bb0d887bc0a900578089bf41ab8dddbb78
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2021
ms.locfileid: "99488661"
---
# <a name="identities-for-visual-studio-subscribers"></a>Visual Studio 訂閱者身分識別
當您啟用 Visual Studio 訂用帳戶時，我們會連結您在 Visual Studio 訂用帳戶啟用期間所使用的身分識別 (或登入)。 這樣，我們就可以在 [Visual Studio 訂閱者入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs)、Azure DevOps 與 Azure 中辨識您。

在 Azure DevOps 中，我們會在您每次登入時檢查您的 Visual Studio 訂用帳戶狀態，並自動授與您所屬每個組織的功能。
因為這些功能是隨附於訂閱者的權益，所以使用連結至 Visual Studio 訂用帳戶的身分識別時，可以免費將您新增為任何 Azure DevOps 組織的成員。

在 Azure 中，當您啟用訂閱者權益的 [每月 Azure DevTest 個別點數](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) 時，我們會檢查您的 Visual Studio 訂用帳戶狀態。

在 [Visual Studio 訂閱者入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs)中，您可以新增 **替代身分識別** -- 除了啟用期間所使用的身分識別之外。 如果您使用 Microsoft 帳戶來啟用您的訂用帳戶，我們可讓您新增替代身分識別。 如此一來，您也可以新增工作或學校帳戶 (您登入 Visual Studio、Microsoft 365 或公司或學校網路) 時所使用的帳戶，可讓您使用個人帳戶和公司或學校帳戶來存取 Azure DevOps。

## <a name="add-an-alternate-account-to-your-subscription"></a>將替代帳戶新增至您的訂用帳戶
將替代帳戶新增至您的 Visual Studio 訂用帳戶可讓您存取特定訂用帳戶權益（例如 Azure DevOps 和 Azure），或使用與指派訂用帳戶不同的身分識別來登入 Visual Studio 的 IDE。 過去，只有在將 Visual Studio (VS) 訂用帳戶指派給 Microsoft 帳戶 (MSA) 時，才能使用這項功能。 我們已擴充 Azure Active Directory (Azure AD) 中公司或學校帳戶的這個功能。

> [!NOTE]
> 替代識別碼只允許您使用第二個識別碼來啟用 Azure 點數和 Azure DevOps，以及登入 Visual Studio IDE。  它無法用來登入訂用帳戶入口網站 <https://my.visualstudio.com> 。  您仍然需要使用指派給訂用帳戶的識別碼來登入入口網站。 

針對所有訂用帳戶，您可以新增「公司或學校帳戶」，讓您可以搭配使用該帳戶與您需要登入的權益 (VS IDE、Azure DevOps 與 Azure)。

### <a name="add-the-alternate-account"></a>新增替代帳戶
1. 使用 Microsoft 帳戶登入 Visual Studio 訂閱者入口網站 (https://my.visualstudio.com)。
2. 選取 **[訂閱]** 索引標籤。
3. 選擇 [ **新增其他帳戶**]。
4. 新增公司或學校帳戶。
    > [!div class="mx-imgBorder"]
    > ![新增公司或學校帳戶](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png "在您的訂用帳戶上新增工作或學校帳戶作為其他帳戶。")

5. 使用公司或學校帳戶登入 Azure DevOps (https://{您的帳戶}.visualstudio.com)。

您的替代帳戶會新增至 Visual Studio 訂用帳戶，讓兩個身分識別都利用需要您使用替代帳戶 (IDE、Azure DevOps 與 Azure) 登入的訂閱權益。

## <a name="faq"></a>常見問題集

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>問：為什麼 Azure DevOps 無法辦識我是 Visual Studio 訂閱者？

答：當您使用主要或其他身分識別登入時，Azure DevOps 應會自動識別您的訂用帳戶。 如果沒有，您可以嘗試以下幾點：

* 檢查您是否有有效的 Visual Studio 訂用帳戶，其中包含 [Azure DevOps](vs-azure-devops.md#eligibility) 作為權益。

* 確認您使用的登入/身分識別是 Visual Studio 訂用帳戶的主要或其他身分識別。

* 登入 Azure DevOps 之前，請至少造訪 [Visual Studio 訂閱者入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs) 一次。

如果 Azure DevOps 仍無法辨識您的訂用帳戶，請連絡 [Azure DevOps 支援](https://azure.microsoft.com/support/devops/)。

## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](/visualstudio/)
- [Azure DevOps 文件](/azure/devops/) \(英文\)
- [Azure 檔](/azure/)
- [Microsoft 365 檔](/microsoft-365/)

## <a name="next-steps"></a>下一步 
如需有關使用 Azure、Azure DevOps 或 Visual Studio IDE 的詳細資訊，請參閱下列資源：
- [Azure](vs-azure.md)
- [Azure DevOps](vs-azure-devops.md)
- [Visual Studio](vs-ide-benefit.md)