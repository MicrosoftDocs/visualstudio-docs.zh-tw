---
title: 顯示於 VLSC 中的個人電子郵件
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 04/10/2020
ms.topic: conceptual
description: Visual Studio 訂閱 – 我為何會針對我的訂閱者看見 Hotmail 或 Gmail 地址？
ms.openlocfilehash: 44b18bd46d55349fae5a3ece03cee9fe93240148
ms.sourcegitcommit: 316dd2182dd56b0cbde49f0cd82e9f75baa2530f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2020
ms.locfileid: "81223680"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>可視化工作室訂閱 – 為什麼我會看到訂閱者的個人帳戶?
公司從批量許可服務中心 (VLSC) 遷移到新的可視化工作室[訂閱管理門戶](https://manage.visualstudio.com)後,管理員驚訝地發現,某些訂閱者的"登錄電子郵件地址"顯示個人電子郵寄地址,如 Hotmail 或 Outlook。  

## <a name="cause"></a>原因
此案例是因為與舊版 MSDN 訂閱者體驗相關聯的登入程序所造成。 使用者是從大量授權服務中心 (VLSC) 移轉到 Visual Studio 訂閱系統管理入口網站，而未經修改。 系統管理員可能未發覺使用者以個人帳戶來存取其訂用帳戶權益。 在於 2016 年完成的 Visual Studio 訂閱者移轉之前，若要成功使用 Visual Studio 訂閱，必須完成兩項動作：
1. 系統管理員使用個別訂閱者的公司或學校電子郵件地址，將訂閱「指派」給他們。
2. 該訂閱者「啟動」訂閱。

訂閱者啟用程序期間：需要 Microsoft 帳戶 (MSA) 才能登入。 若訂閱者沒有嘗試將其公司或學校帳戶 (例如 tasha@contoso.com) 轉換成 MSA，他們則可以建立新的 MSA 或使用現有的 MSA。 這導致其「登入電子郵件地址」和「指派電子郵件地址」有所不同。

> [!NOTE]
> 上[https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)的現代訂戶體驗支援工作/學校和Microsoft帳戶 (MSA) 標識類型。

## <a name="solution"></a>解決方法

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

要更正此問題,只需選擇 **「連接電子郵件」** 按鈕,系統將嘗試根據匹配名字和姓氏,將帳戶與 MSA 與組織的 Azure 活動目錄 (Azure AD) 中的現有使用者匹配。 如果出現錯誤,可以通過單擊匹配右側的**X**來刪除任何匹配項。  

> [!div class="mx-imgBorder"]
> ![連線電子郵件按鈕](_img/connect-emails/connect-emails-button.png)

您還可以使用**搜尋目錄**來更正錯誤或填寫 Azure AD 中缺少的資訊。 如果所有匹配項看起來正確,您可以選擇"選擇所有匹配的訂閱者",而不是一次選擇一個。  

> [!div class="mx-imgBorder"]
> ![連線電子郵件飛出](_img/connect-emails/connect-emails-flyout.png)

接下來點擊"繼續",這將帶您到一個螢幕概述要發生的更改。 如果您同意,請按下"保存",然後進行更改。 您的訂閱者還將收到一條消息,通知他們下次登錄訂閱時更改。   

> [!div class="mx-imgBorder"]
> ![連線電子郵件確認](_img/connect-emails/connect-emails-confirm.png) 

> [!NOTE]
> 當您編輯登入電子郵件地址時,這只會更新訂閱者用於登入其訂閱的https://my.visualstudio.com電子郵件 。 如果訂閱者已經使用其他電子郵件地址啟動了 Azure 或複數等權益,則需要繼續使用這些電子郵寄地址來訪問它們。 對於他們訪問的任何新權益,他們應該使用新的電子郵寄地址。 

## <a name="see-also"></a>另請參閱
- [視覺化工作室文件](https://docs.microsoft.com/visualstudio/)
- [Azure 開發人員文件](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [微軟 365 文件](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>後續步驟
- 如果您已經更新訂閱者的電子郵件地址，便應該通知他們其登入資訊已經變更。  他們也會收到一封包含更新資訊的電子郵件。
- [篩選組織中的訂閱者清單](search-license.md)可能有助於找出任何可能需要變更的登入電子郵件地址。  
