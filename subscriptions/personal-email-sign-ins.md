---
title: 顯示於 VLSC 中的個人電子郵件
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 09/17/2020
ms.topic: conceptual
description: Visual Studio 訂閱 – 我為何會針對我的訂閱者看見 Hotmail 或 Gmail 地址？
ms.openlocfilehash: 95f5d849a1f661ab6a65a34890faf8f812c7007d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810493"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Visual Studio 訂用帳戶–為什麼我會看到訂閱者的個人帳戶？
從大量授權服務中心遷移 (VLSC) 至新的 Visual Studio 訂用帳戶 [管理入口網站](https://manage.visualstudio.com)之後，系統管理員很驚訝地發現某些訂閱者的「登入電子郵件地址」會顯示個人電子郵件地址，例如 Hotmail 或 Outlook。  

## <a name="cause"></a>原因
此案例是因為與舊版 MSDN 訂閱者體驗相關聯的登入程序所造成。 使用者是從大量授權服務中心 (VLSC) 移轉到 Visual Studio 訂閱系統管理入口網站，而未經修改。 系統管理員可能未發覺使用者以個人帳戶來存取其訂用帳戶權益。 在於 2016 年完成的 Visual Studio 訂閱者移轉之前，若要成功使用 Visual Studio 訂閱，必須完成兩項動作：
1. 系統管理員使用個別訂閱者的公司或學校電子郵件地址，將訂閱「指派」給他們。
2. 該訂閱者「啟動」訂閱。

訂閱者啟用程序期間：需要 Microsoft 帳戶 (MSA) 才能登入。 若訂閱者沒有嘗試將其公司或學校帳戶 (例如 tasha@contoso.com) 轉換成 MSA，他們則可以建立新的 MSA 或使用現有的 MSA。 這導致其「登入電子郵件地址」和「指派電子郵件地址」有所不同。

> [!NOTE]
> 的新式訂閱者體驗 [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) 支援公司/學校和 Microsoft 帳戶 (MSA) 身分識別類型。

## <a name="solution"></a>解決方法

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

若要修正這個問題，只要選取 [ **連接電子郵件]** 按鈕，系統就會嘗試將 msa 的帳戶與組織 Azure Active Directory 中的現有使用者 (Azure AD) 根據相符的姓氏和姓氏。 如果發生錯誤，您可以按一下相符項右邊的 **X** 來移除任何相符的結果。  

> [!div class="mx-imgBorder"]
> ![連接電子郵件按鈕](_img/connect-emails/connect-emails-button.png "按一下 [連接電子郵件]，將您的使用者與 Microsoft 帳戶對應到您的 Azure Active Directory")

您也可以使用 **搜尋目錄** 來修正錯誤，或從您的 Azure AD 填入遺漏的資訊。 如果所有相符專案都正確無誤，您可以選擇 [選取所有相符的訂閱者]，而不是一次選取一個相符的訂閱者。  

> [!div class="mx-imgBorder"]
> ![連接電子郵件飛出](_img/connect-emails/connect-emails-flyout.png "選取您要與 Azure AD 身分識別相符的訂閱者，然後按一下 [繼續]。")

接下來請按一下 [繼續]，這會帶您前往要進行的變更清單。 如果您同意，請按一下 [儲存]，將會進行變更。 您的訂閱者也會收到訊息，通知他們下一次登入其訂用帳戶時的變更。   

> [!div class="mx-imgBorder"]
> ![連接電子郵件確認](_img/connect-emails/connect-emails-confirm.png "按一下 [繼續] 以執行建議的變更，然後按一下 [儲存]。") 

> [!NOTE]
> 當您編輯登入電子郵件地址時，這只會更新訂閱者用來登入其訂用帳戶的電子郵件 https://my.visualstudio.com 。 如果「訂閱者」已使用其他電子郵件地址來啟用 Azure 或 Pluralsight 等權益，他們將需要繼續使用這些電子郵件地址來存取它們。 針對他們存取的任何新權益，他們應該使用新的電子郵件地址。 

## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 檔](https://docs.microsoft.com/azure/devops/)
- [Azure 檔](https://docs.microsoft.com/azure/)
- [Microsoft 365 檔](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>後續步驟
- 如果您已經更新訂閱者的電子郵件地址，便應該通知他們其登入資訊已經變更。  他們也會收到一封包含更新資訊的電子郵件。
- [篩選組織中的訂閱者清單](search-license.md)可能有助於找出任何可能需要變更的登入電子郵件地址。  
