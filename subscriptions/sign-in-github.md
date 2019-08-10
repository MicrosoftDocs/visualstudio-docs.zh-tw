---
title: 使用 GitHub 帳戶登入 Visual Studio 訂用帳戶 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/11/2019
ms.topic: conceptual
description: 了解如何使用 GitHub 帳戶登入 Visual Studio 訂用帳戶。
ms.openlocfilehash: 6279c9399a42bc07579f48c887987b4b662da9da
ms.sourcegitcommit: 57866dd72fd0e15ce61128df70729b427a2d02eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2019
ms.locfileid: "68315369"
---
# <a name="signing-in-to-visual-studio-subscriptions-with-your-github-account"></a>使用 GitHub 帳戶登入 Visual Studio 訂用帳戶 

登入您 Visual Studio 訂用帳戶的步驟取決於您使用的帳戶類型。 例如，您可能使用 Microsoft 帳戶 (MSA) 或您的雇主或學校提供的電子郵件地址。 2019 年 1 月起，您現在也可以使用您的 GitHub 帳戶來登入某些訂用帳戶。 

本文將提供使用 GitHub 帳戶登入的步驟。

## <a name="signing-in-with-your-github-account"></a>使用您的 GitHub 帳戶登入

GitHub 身分識別支援可讓您使用現有 GitHub 帳戶，作為新或現有 Microsoft 帳戶的認證，將您的 GitHub 帳戶與 Microsoft 帳戶連結。 

當您登入 GitHub 時，Microsoft 會檢查與您 GitHub 帳戶建立關聯的任何電子郵件地址，是否與現有的個人或企業 Microsoft 帳戶相符。 如果電子郵件地址符合您的企業帳戶，系統會提示您改為登入該帳戶。 如果電子郵件地址符合個人帳戶，我們會將您 GitHub 帳戶新增為登入該個人帳戶的方法。

連結您的 GitHub 和 Microsoft 帳戶認證之後，您可以從任何可使用個人 Microsoft 帳戶的位置 (例如 Azure 網站、Office 應用程式和 Xbox) 使用該單一登入。 這些帳戶也可以用於讓 Azure Active Directory 來賓登入為 Microsoft 帳戶 (假設電子郵件地址符合邀請中的其中一個)。

> [!NOTE]
> 將 GitHub 身分識別連結到 Microsoft 帳戶，不會提供 Microsoft 任何程式碼存取權。 當應用程式 (例如 Azure DevOps 與 Visual Studio) 需要存取您的程式碼存放庫時，系統會提示您授與此存取權的特定同意。 

### <a name="frequently-asked-questions"></a>常見問題集
針對您使用 GitHub 帳戶認證登入 Visual Studio 訂用帳戶時可能會遇到的問題，下列常見問題集可協助您解決。

#### <a name="q-i-forgot-my-github-password--how-can-i-access-my-account-now"></a>問：我忘記我的 GitHub 密碼。  我現在應如何存取我的帳戶？
答：您可以前往 [Reset your password](https://github.com/password_reset) (重設密碼) 來復原您的 GitHub 帳戶。 或者，您可以在[復原您的帳戶](https://account.live.com/password/reset)上輸入您的 GitHub 帳戶電子郵件地址，來復原您與 GitHub 連結的 Microsoft 帳戶。

#### <a name="q-i-deleted-my-github-account--how-can-i-access-my-microsoft-account-msa-now"></a>問：我刪除了我的 GitHub 帳戶。  我現在應如何存取我的 Microsoft 帳戶 (MSA)？
答：如果您的 MSA 沒有任何其他認證 (例如密碼、驗證器應用程式或安全性金鑰)，您可以使用與您 Microsoft 帳戶連結之電子郵件地址來復原您的 Microsoft 帳戶。 若要開始使用，請前往[復原您的帳戶](https://account.live.com/password/reset)。 您必須將密碼新增至您的帳戶，讓我們知道稍後如何將您登入。 

#### <a name="q-theres-no-sign-in-with-github-option-on-the-sign-in-page--how-can-i-use-my-github-credentials-to-sign-in"></a>問：登入頁面上沒有「使用 GitHub 登入」選項。  我應如何使用我的 GitHub 認證登入？
答：鍵入您在建立與您 GitHub 連結的 Microsoft 帳戶時，所選擇的 GitHub 電子郵件地址。 我們將尋找您的資訊，並將您轉至 GitHub 進行登入。 或者，如果登入頁面中有登入選項連結，請按一下該連結，並使用顯示的 [使用 GitHub 登入]  按鈕。 

#### <a name="q-i-cant-sign-in-to-some-of-my-apps-and-products-with-github--why"></a>問：我無法使用 GitHub 登入我的某些應用程式與產品。  原因為何？
答：並非所有的 Microsoft 產品都可從其登入頁面存取 GitHub.com，例如 Xbox 主控台。 當您鍵入從 GitHub 帳戶連結的電子郵件地址時，我們會傳送驗證碼到該地址，以便確認這是您本人。 您仍會登入到相同的帳戶，只是登入方法不同。 

#### <a name="q--ive-added-a-password-to-the-microsoft-account-i-have-linked-to-my-github-account--will-that-cause-a-problem"></a>問：我已將密碼新增至已連結到我 GitHub 帳戶的 Microsoft 帳戶。  這會造成問題嗎？
答：完全不用。 這不會變更您的 GitHub 密碼，只是您多了另一種方式來登入您的 Microsoft 帳戶。 每當您使用您的電子郵件地址登入時，我們會讓您選擇使用您的 Microsoft 帳戶密碼登入或轉至 GitHub 登入。 如果您需要新增密碼，我們強烈建議您使用與您 GitHub 帳戶不同的密碼。

#### <a name="q-i-want-to-add-the-authenticator-app-to-the-account-i-created-using-github--can-i-do-that"></a>問：我想要將驗證器應用程式新增至我使用 GitHub 建立的帳戶。  可以這麼做嗎？
答：沒問題，您只需要下載該應用程式並使用您的電子郵件地址登入。 當您使用您的電子郵件地址登入時，系統將會提示您選擇[驗證器應用程式](https://go.microsoft.com/fwlink/?linkid=2090219)或 GitHub 作為您的認證。

#### <a name="q-ive-enabled-two-factor-authentication-on-both-my-github-and-microsoft-accounts-msa-but-when-i-sign-in-to-my-msa-im-still-asked-to-authenticate-twice--why"></a>問：我已在我的 GitHub 和 Microsoft 帳戶 (MSA) 啟用雙重要素驗證，但是當我登入 MSA 時，系統仍要求我驗證兩次。  原因為何？
答：由於安全性限制，Microsoft 會將使用 GitHub 登入視為單一要素驗證，即使您已啟用雙步驟驗證也一樣。 因此，您必須重新驗證您的 Microsoft 帳戶。 

#### <a name="q--how-can-i-tell-if-my-microsoft-account-and-github-accounts-are-linked"></a>問：如何確認我的 Microsoft 帳戶和 GitHub 帳戶是否已連結？
答：每當您使用您的帳戶別名 (電子郵件地址、電話號碼、Skype 名稱) 登入時，我們將會顯示您帳戶的所有登入方法。 如果您沒有看到 GitHub，則表示您還沒有設定 GitHub。

#### <a name="q--how-can-i-unlink-my-microsoft-and-github-accounts"></a>問：如何將我的 Microsoft 與 GitHub 帳戶取消連結？ 
答：前往 account.microsoft.com 的[安全性](https://account.microsoft.com/security)索引標籤，然後按一下 [其他安全性選項]  來取消您 GitHub 帳戶的連結。 取消您 GitHub 帳戶的連結會將其從登入方法移除，並移除 Visual Studio 中任何 GitHub 存放庫的存取權。 其他 Microsoft 產品可能會個別要求存取您的 GitHub 帳戶，因此移除該存取權不會在所有產品中移除存取權。 前往 GitHub 設定檔的[應用程式權限](https://github.com/settings/applications)頁面，並從在該處列出的應用程式中撤銷同意。

#### <a name="q--i-try-to-use-my-github-account-to-sign-in-but-im-prompted-that-i-already-have-a-microsoft-identity-that-i-should-use-instead--whats-happening"></a>問：我嘗試使用 GitHub 帳戶來登入，但系統提示我已擁有 Microsoft 身分識別，且應該改為使用該身分識別。  這是為什麼？
答：如果您在您的 GitHub 帳戶上擁有 Azure Active Directory 電子郵件地址，這表示您已經擁有可以使用您 GitHub 程式碼存取 Azure 並執行 CI 管線的 Microsoft 身分識別。 使用該帳戶可確保您的 Azure 資源和組建管線保留在您組織範圍內。 不過，如果您要進行個人工作，我們建議在您的 GitHub 帳戶上設定個人電子郵件地址，讓您隨時都能存取。 完成此操作後，請再次嘗試登入，並在系統提示您登入您的公司或學校帳戶時，選擇 [使用不同的電子郵件地址]  。 這會讓您使用該個人電子郵件地址來建立新的 Microsoft 帳戶。

## <a name="next-steps"></a>後續步驟
當您成功登入訂用帳戶入口網站時，建議您前往 https://my.visualstudio.com/benefits 上的 [優點] 頁面，並探索提供給您的絕佳工具、服務及供應項目。  