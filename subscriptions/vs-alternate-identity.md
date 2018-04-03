---
title: Visual Studio 訂閱者身分識別
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 3/15/2018
Ms.topic: Get-Started-Article
Description: How to add an alternate identity for your Visual Studio subscription, to use for VSTS and Azure.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 70bfd305ec35b562fb722fb853016c3df4240ff8
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="identities-for-visual-studio-subscribers"></a>Visual Studio 訂閱者身分識別

當您啟用 Visual Studio 訂用帳戶時，我們會連結您在 Visual Studio 訂用帳戶啟用期間所使用的身分識別 (或登入)。 這樣我們可以在 [Visual Studio 訂閱者入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs)、VSTS 和 Azure 中辨識您。

在 VSTS 中，我們會在您每次登入時檢查您的 Visual Studio 訂用帳戶狀態，並自動授與您所屬每個帳戶的功能。 因為這些功能是隨附於訂閱者的權益，所以使用連結至 Visual Studio 訂用帳戶的身分識別時，它可以免費將您新增為任何 VSTS 帳戶的成員。

在 Azure 中，當您啟用您訂閱者權益的[每月 Azure 點數](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/)時，我們會檢查您的 Visual Studio 訂用帳戶狀態。

在 [Visual Studio 訂閱者入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs) 中，您可新增**其他身分識別** -- 除啟用期間所用的身分識別之外。 今天，如果您使用 Microsoft 帳戶啟用您的訂用帳戶，我們可讓您新增其他身分識別。 這樣您也可以新增工作或學校帳戶 (登入 Visual Studio、Office 365 或您公司或學校的網路時所用的帳戶)，讓您使用您個人的帳戶和您的工作或學校帳戶來存取 VSTS。

## <a name="how-to-add-an-alternate-identity-to-your-visual-studio-subscription"></a>如何在 Visual Studio 訂用帳戶中新增其他身分識別

1. 登入 [Visual Studio 訂閱者入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs)。

  > 如果系統要求您選擇「個人帳戶」或「公司或學校帳戶」，請選擇「個人帳戶」(您的 Microsoft 帳戶)。
  >
  > 有時候需要選擇，是因為您的 Microsoft 帳戶和您的工作或學校帳戶共用相同的電子郵件地址。 雖然這兩個身分識別使用相同的電子郵件地址，但它們仍是使用不同的設定檔、安全性設定和權限的不同身分識別。
  >
  > 自 2018 年 3 月 30 日開始，您就無法再使用所用網域受 Azure Active Directory 管理的電子郵件來建立 Microsoft 帳戶。 您仍然可以使用此電子郵件作為工作帳戶登入。

2. 前往 [訂用帳戶] 索引標籤。

  ![選擇 [訂用帳戶]](_img/vs-alternate-identity/choose-subscriptions-my-visual-studio-com-portal.png)

3. 前往 [相關連結] 下的 [新增其他帳戶]。

  ![前往 [相關連結] 下的 [新增其他帳戶]](_img/vs-alternate-identity/add-alternate-account-my-visual-studio-com-portal.png)

4. 輸入您的工作或學校帳戶，然後選擇 [新增]。

  ![輸入您的工作或學校帳戶](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. 使用您的工作或學校帳戶登入您的 VSTS 帳戶 (```https://{youraccount}.visualstudio.com```)。 資訊傳播可能略有延遲，請在 15 分鐘後再查看一次。 

## <a name="faq"></a>常見問題集

### <a name="q--why-doesnt-vsts-recognize-me-as-a-visual-studio-subscriber"></a>問： 為什麼 VSTS 無法辦識我是 Visual Studio 訂閱者？
答：當您使用主要或其他身分識別登入時，VSTS 應會自動識別您的訂用帳戶。 如果沒有，您可以嘗試以下幾點：

* 檢查您是否有有效的 Visual Studio 訂用帳戶，[包含 VSTS 權益](vs-vsts.md)。

* 確認您使用的登入/身分識別是 Visual Studio 訂用帳戶的主要或其他身分識別。

* 至少瀏覽一次 [Visual Studio 訂閱者入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs)再登入 VSTS。

如果 VSTS 仍無法辨識您的訂用帳戶，請[連絡支援服務](https://www.visualstudio.com/team-services/support/)

