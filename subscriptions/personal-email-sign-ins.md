---
title: 顯示於 VLSC 中的個人電子郵件
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Visual Studio 訂閱 – 我為何會針對我的訂閱者看見 Hotmail 或 Gmail 地址？
ms.openlocfilehash: c4a3202bfb14246fa8057309de90bdc7c32db5df
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410211"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Visual Studio 訂用帳戶 - 我為何會針對我的訂閱者看見 Hotmail 或 Gmail 地址？
在公司從大量授權服務中心 (VLSC) 移轉至新的 Visual Studio [訂閱管理入口網站](https://manage.visualstudio.com)之後，系統管理員會對於部分訂閱者的「登入電子郵件地址」是顯示為第三方電子郵件地址 (例如 Hotmail、Gmail 或 Yahoo) 感到訝異。  如需詳細資訊，請參閱[這段影片](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6)。

## <a name="cause"></a>原因
此案例是因為與舊版 MSDN 訂閱者體驗相關聯的登入程序所造成。 使用者是從大量授權服務中心 (VLSC) 移轉到 Visual Studio 訂閱系統管理入口網站，而未經修改。 系統管理員可能未發覺使用者以個人帳戶來存取其訂用帳戶權益。 在於 2016 年完成的 Visual Studio 訂閱者移轉之前，若要成功使用 Visual Studio 訂閱，必須完成兩項動作：
1. 系統管理員使用個別訂閱者的公司或學校電子郵件地址，將訂閱「指派」給他們。
2. 該訂閱者「啟動」訂閱。

訂閱者啟用程序期間：需要 Microsoft 帳戶 (MSA) 才能登入。 若訂閱者沒有嘗試將其公司或學校帳戶 (例如 tasha@contoso.com) 轉換成 MSA，他們則可以建立新的 MSA 或使用現有的 MSA。 這導致其「登入電子郵件地址」和「指派電子郵件地址」有所不同。

> [!NOTE]
> [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) 上的新訂閱者體驗，同時支援公司/學校帳戶及 Microsoft 帳戶 (MAA) 身分識別類型。

## <a name="solution"></a>解決方法
若要修正此問題，只需選取 [連線**電子郵件]** 按鈕，系統就會根據符合的名字和姓氏，嘗試將具有 msa 的帳戶與組織的 Azure Active Directory （Azure AD）中的現有使用者進行比對。 如果發生錯誤，您可以按一下相符的右邊的**X**來移除任何相符的。  

> [!div class="mx-imgBorder"]
> ![連接電子郵件 按鈕](_img/connect-emails/connect-emails-button.png)

您也可以使用**搜尋目錄**來更正錯誤，或在 Azure AD 中填入遺漏的資訊。 如果所有相符專案看起來都正確，您可以選擇 [選取所有相符的訂閱者]，而不是一次選取一個。  

> [!div class="mx-imgBorder"]
> ![將電子郵件即時連線](_img/connect-emails/connect-emails-flyout.png)

接下來，按一下 [continue （繼續）]，這會將您帶到概述要進行之變更的畫面。 如果您同意，請按一下 [儲存]，將會進行變更。 您的訂閱者也會收到一則訊息，通知他們下一次登入其訂用帳戶時所進行的變更。   

> [!div class="mx-imgBorder"]
> ![連接電子郵件確認](_img/connect-emails/connect-emails-confirm.png) 

> [!NOTE]
> 當您編輯登入電子郵件地址時，這只會更新在 https://my.visualstudio.com上用來登入其訂用帳戶的電子郵件。 如果訂閱者已使用其他電子郵件地址來啟用 Azure 或 Pluralsight 之類的權益，他們就必須繼續使用這些電子郵件地址來存取它們。 針對他們所存取的任何新權益，他們應該使用新的電子郵件地址。 

## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [Microsoft 365 檔](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>後續步驟
- 如果您已經更新訂閱者的電子郵件地址，便應該通知他們其登入資訊已經變更。  他們也會收到一封包含更新資訊的電子郵件。
- [篩選組織中的訂閱者清單](search-license.md)可能有助於找出任何可能需要變更的登入電子郵件地址。  
