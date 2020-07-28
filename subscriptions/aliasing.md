---
title: 登入 Visual Studio 訂用帳戶可能會因為使用別名而失敗 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97bf7474-c6c2-49b3-b2c9-f1b2808eed1a
ms.date: 03/02/2020
ms.topic: conceptual
description: 登入可能會因為使用別名或易記名稱而失敗
ms.openlocfilehash: 1b6c465bc3e850d8582abde200ac9e5bd995e431
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234636"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>使用別名時，登入 Visual Studio 訂用帳戶可能會失敗
視用來登入的帳戶類型而定，登入時可能無法正確顯示可用的訂閱 [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) 。 其中一個可能的原因是使用「別名」或「易記名稱」，而非使用訂用帳戶指派目標的登入身分識別。 這稱為「別名處理」。

## <a name="what-is-aliasing"></a>別名處理是什麼？
「別名處理」一詞指的是使用不同身分識別來登入 Windows (或您的 Active Directory) 並存取電子郵件的使用者。

當公司使用 Microsoft Online Service 作為其目錄登入使用 (例如 JohnD@contoso.com)，但使用者以別名或易記名稱存取其電子郵件帳戶 (例如 John.Doe@contoso.com) 時，就會發生別名處理。 請確定您的使用者使用的是系統管理員入口網站中所列的「登入電子郵件地址」 https://manage.visualstudio.com ，才能存取其訂用帳戶。 

## <a name="what-are-the-potential-issues"></a>可能的問題有哪些？

視訂閱者的帳戶類型而定，他們可能會遇到兩個問題的其中一個。 

### <a name="work-or-school-account-upn-mismatch-issue"></a>工作或學校帳戶 UPN 不相符的問題 
當公司具有 Active Directory 設定，而 UserPrincipalName （UPN）與主要 SMTP 位址不相同時，就可能會發生 UPN 不符的情況。 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>如何偵測您的登入位址是否受到 UPN 不相符的影響 

1. https://my.visualstudio.com/subscriptions使用您的訂用帳戶指派電子郵件中所述的登入位址來登入。

2. 確認列在頁面右上方的登入電子郵件地址符合您用來登入的位址。  如果不相符，則您的 UPN 不相符，而且您將無法看到您的訂用帳戶。 

> [!div class="mx-imgBorder"]
> ![登入電子郵件地址](_img//aliasing/sign-in-email.png "請確定顯示在右上方的電子郵件地址符合您用來登入的網址。")

#### <a name="how-to-fix-a-upn-mismatch"></a>如何修正 UPN 不相符的問題

1. 存取 Visual Studio 管理管理入口網站[https://manage.visualstudio.com](https://manage.visualstudio.com) 

2. 找出具有 UPN 不符問題的訂閱者。 （[篩選](search-license.md)功能可讓您輕鬆地尋找訂閱者）。

3. 將登入郵寄地址變更為訂閱者的 UPN 

0. 儲存變更 

0. 通知訂閱者登出訂閱者入口網站，並使用 UPN 再次存取 

### <a name="personal-account-aliasing-issue"></a>個人帳號別名問題

如果用來登入 Visual Studio 訂閱入口網站的電子郵件地址與訂用帳戶相關聯的電子郵件地址不相符，個人訂用帳戶也可能會遇到問題。 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>如何偵測您的個人訂用帳戶是否受到別名問題影響

1. 登入[https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions)

0. 確認列在頁面右上方的登入電子郵件地址符合您用來登入的位址。  如果登入的電子郵件地址與用來存取網站的電子郵件地址不同，則您的帳戶與別名之間會發生衝突。

#### <a name="how-to-fix-an-alias-issue"></a>如何修正別名問題

Visual Studio 平臺會排定主要別名的優先順序，以顯示訂用帳戶詳細資料。 

1. 移至 [**管理您登入 Microsoft 的方式**]。 若出現提示，請登入您的 Microsoft 帳戶。 

2. 在 [帳號別名] 底下，選取用來指派訂閱的電子郵件地址旁的 [**設為主要**]。 

> [!div class="mx-imgBorder"]
> ![設定主要電子郵件地址](_img//aliasing/account-aliases.png "使用 [設為主要] 連結來選擇訂用帳戶的主要別名。")

3. 登出 Visual Studio 訂用帳戶入口網站（https://my.visualstudio.com) 

4. 使用用來指派訂閱的帳戶重新登入，其現在應設定為主要別名。 

## <a name="preventing-aliasing-issues"></a>防止別名問題

身為系統管理員，有兩個選項可確保您的訂閱者成功登入體驗 [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) 。
- 第一個選項（建議使用）是利用目錄帳戶作為 Visual Studio 訂用帳戶入口網站（位於）的登入 https://my.visualstudio.com 。  
- 第二個選項（較不安全）是允許您的訂閱者使用不同于其目錄電子郵件地址的電子郵件地址進行登入。

在系統管理員入口網站中，這兩個選項都是藉由完成下列步驟來設定：  
1. 登入[https://manage.visualstudio.com](https://manage.visualstudio.com) 

0. 如果您要改變單一使用者，請在資料表中選取該使用者，並以滑鼠右鍵按一下以編輯。 這會開啟一個面板，您可以在其中修改登入電子郵件地址。 在 [登入電子郵件地址] 欄位中進行必要的更新。 按一下 [儲存]，變更就會生效。  

0. 如果您需要對大量的使用者進行這些變更，您可以利用大量編輯功能。 如需詳細資訊，請參閱[使用大量編輯來編輯多個訂閱者](https://docs.microsoft.com/visualstudio/subscriptions/edit-license#edit-multiple-subscribers-using-bulk-edit)一文。

> [!NOTE]
> 針對個別和大量變更，訂閱者會收到一封電子郵件，指示他們的登入電子郵件地址已變更，而他們需要使用更新的電子郵件地址來登入。 也請務必注意，如果訂閱者先前已啟用其他登入位址的權益，他們將需要繼續使用其他登入位址來存取它們。  

## <a name="see-also"></a>另請參閱
- [Visual Studio 文件](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [Microsoft 365 檔](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>後續步驟
深入瞭解如何管理 Visual Studio 訂閱。
- [指派個別訂閱](assign-license.md)
- [指派多個訂用帳戶](assign-license-bulk.md)
- [編輯訂用帳戶](edit-license.md)
- [判斷最大使用量](maximum-usage.md)


