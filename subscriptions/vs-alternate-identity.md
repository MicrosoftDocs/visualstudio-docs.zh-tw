---
title: Visual Studio 訂閱者身分識別
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 04/10/2018
ms.topic: conceptual
description: 如何新增 Visual Studio 訂用帳戶的替代身分識別，以用於 Azure DevOps Services 和 Azure
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: vs subscription
ms.openlocfilehash: 15b364cc8375d4e0e64b20ad7e8a6b19ba4140f5
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283557"
---
# <a name="identities-for-visual-studio-subscribers"></a>Visual Studio 訂閱者身分識別

當您啟用 Visual Studio 訂用帳戶時，我們會連結您在 Visual Studio 訂用帳戶啟用期間所使用的身分識別 (或登入)。 這樣我們可以在 [Visual Studio 訂閱者入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs)、Azure DevOps Services 和 Azure 中辨識您。

在 Azure DevOps Services 中，我們會在您每次登入時檢查您的 Visual Studio 訂用帳戶狀態，並自動授與您所屬每個帳戶的功能。
因為這些功能是隨附於訂閱者的權益，所以使用連結至 Visual Studio 訂用帳戶的身分識別時，可以免費將您新增為任何 Azure DevOps Services 帳戶的成員。

在 Azure 中，當您啟用您訂閱者權益的[每月 Azure 點數](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/)時，我們會檢查您的 Visual Studio 訂用帳戶狀態。

在 [Visual Studio 訂閱者入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs)中，您可以新增**替代身分識別** -- 除了啟用期間所使用的身分識別之外。 現在，如果您使用 Microsoft 帳戶啟用您的訂用帳戶，我們可讓您新增替代身分識別。 這樣您也可以新增公司或學校帳戶 (登入 Visual Studio、Office 365 或您公司或學校網路時所用的帳戶)，讓您使用個人帳戶和公司或學校帳戶來存取 Azure DevOps Services。

## <a name="add-an-alternate-account-to-your-visual-studio-subscription"></a>將替代帳戶新增至 Visual Studio 訂用帳戶

將替代帳戶新增至 Visual Studio 訂用帳戶，可讓您使用與獲指派訂用帳戶不同的身分識別來存取訂用帳戶權益 (例如 Azure DevOps Services 和 Azure)。 過去，只有在將 Visual Studio (VS) 訂用帳戶指派給 Microsoft 帳戶 (MSA) 時，才能使用這項功能。 我們已擴充 Azure Active Directory (Azure AD) 中公司或學校帳戶的這個功能。

這不會將一份訂用帳戶提供給其他帳戶；它只會提供使用替代帳戶存取兩個權益的能力。

針對所有訂用帳戶，您可以新增「公司或學校帳戶」，讓您可以搭配使用該帳戶與您需要登入的權益 (VS IDE、Azure DevOps Services 和 Azure)。


### <a name="add-the-alternate-account"></a>新增替代帳戶


1. 使用 Microsoft 帳戶登入 Visual Studio 訂閱者入口網站 (https://my.visualstudio.com)。

2. 前往 [訂用帳戶]。

    > [!div class="mx-imgBorder"]
    > ![新增替代帳戶 - 前往 VS 中的訂用帳戶](_img/vs-alternate-identity/my-vs-subscriptions.png)

3. 選擇 [Add alternate account (新增其他帳戶)]。
    > [!div class="mx-imgBorder"]
    > ![選擇 [Add alternate account] \(新增其他帳戶\)](_img/vs-alternate-identity/choose-add-alternate-account.png)

4. 新增公司或學校帳戶。
    > [!div class="mx-imgBorder"]
    > ![新增公司或學校帳戶](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. 使用公司或學校帳戶登入 Azure DevOps Services (https://{您的帳戶}.visualstudio.com)。
    > [!div class="mx-imgBorder"]
    > ![使用公司或學校帳戶](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

您的替代帳戶會新增至 Visual Studio 訂用帳戶，讓兩個身分識別都利用需要您使用替代帳戶 (IDE、Azure DevOps Services 和 Azure) 登入的訂閱權益。

## <a name="faq"></a>常見問題集

### <a name="q--why-doesnt-azure-devops-services-recognize-me-as-a-visual-studio-subscriber"></a>問：為什麼 Azure DevOps Services 無法辦識我是 Visual Studio 訂閱者？

答：當您使用主要或其他身分識別登入時，Azure DevOps Services 應會自動識別您的訂用帳戶。 如果沒有，您可以嘗試以下幾點：

* 檢查您是否有有效的 Visual Studio 訂用帳戶，[包含 Azure DevOps Services 權益](vs-azure-devops.md)。

* 確認您使用的登入/身分識別是 Visual Studio 訂用帳戶的主要或其他身分識別。

* 至少瀏覽一次 [Visual Studio 訂閱者入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs)再登入 Azure DevOps Services。

如果 Azure DevOps Services 仍無法辨識您的訂用帳戶，請[連絡支援服務](https://visualstudio.microsoft.com/team-services/support/)
