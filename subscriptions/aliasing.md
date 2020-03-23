---
title: 登入 Visual Studio 訂用帳戶可能會因為使用別名而失敗 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97bf7474-c6c2-49b3-b2c9-f1b2808eed1a
ms.date: 03/02/2020
ms.topic: conceptual
description: 登入可能會因為使用別名或易記名稱而失敗
ms.openlocfilehash: 0f5ed4fe67dbd863a7ba4c22f10946cbeb1c36b0
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "79509053"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>使用別名時，登錄到視覺化工作室訂閱可能會失敗
根據用於登錄的帳戶類型，在登錄到 時可能無法正確顯示可用訂閱[https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)。 其中一個可能的原因是使用「別名」或「易記名稱」，而非使用訂用帳戶指派目標的登入身分識別。 這稱為「別名處理」。

## <a name="what-is-aliasing"></a>別名處理是什麼？
「別名處理」一詞指的是使用不同身分識別來登入 Windows (或您的 Active Directory) 並存取電子郵件的使用者。

當公司使用 Microsoft Online Service 作為其目錄登入使用 (例如 JohnD@contoso.com)，但使用者以別名或易記名稱存取其電子郵件帳戶 (例如 John.Doe@contoso.com) 時，就會發生別名處理。 確保使用者使用 "登錄電子郵件地址"（如在）https://manage.visualstudio.com中的管理員門戶中列出來訪問其訂閱。 

## <a name="what-are-the-potential-issues"></a>潛在的問題是什麼？

根據訂閱者的帳戶類型，他們可能會遇到兩個問題之一。 

### <a name="work-or-school-account-upn-mismatch-issue"></a>工作或學校帳戶 UPN 不匹配問題 
當公司設置了活動目錄，其中使用者主名稱 （UPN） 與主 SMTP 位址不同時，可能會遇到 UPN 不匹配。 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>如何檢測您的登錄位址是否受到 UPN 不匹配的影響 

1. 使用訂閱https://my.visualstudio.com/subscriptions分配電子郵件中提及的登錄位址登錄。

2. 驗證頁面右上角列出的登錄電子郵件地址是否與您用於登錄的位址匹配。  如果沒有，您的 UPN 不匹配，您將無法查看您的訂閱。 

> [!div class="mx-imgBorder"]
> ![登錄電子郵件地址](_img//aliasing/sign-in-email.png)

#### <a name="how-to-fix-a-upn-mismatch"></a>如何修復 UPN 不匹配

1. 訪問視覺化工作室監管中心[https://manage.visualstudio.com](https://manage.visualstudio.com) 

2. 找到具有 UPN 不匹配問題的訂閱者。 （[篩選器](search-license.md)功能可以方便地查找訂閱者。

3. 將登錄郵寄地址更改為訂閱者的 UPN 

0. 保存更改 

0. 通知訂閱者登出訂閱者門戶，並使用 UPN 再次訪問 

### <a name="personal-account-aliasing-issue"></a>個人帳號別名問題

如果用於登錄到 Visual Studio 訂閱門戶的電子郵件地址與與訂閱關聯的電子郵件地址不匹配，則個人訂閱帳戶也可能會遇到問題。 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>如何檢測您的個人訂閱帳戶是否受到別名問題的影響

1. 登錄[https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions)

0. 驗證頁面右上角列出的登錄電子郵件地址是否與您用於登錄的位址匹配。  如果登錄電子郵件地址與用於訪問網站的電子郵件地址不同，則您的帳戶和別名之間存在衝突。

#### <a name="how-to-fix-an-alias-issue"></a>如何修復別名問題

Visual Studio 平臺確定主別名的優先順序以顯示訂閱詳細資訊。 

1. 轉到**管理登錄到 Microsoft 的方式**。 如果出現提示，請登錄您的 Microsoft 帳戶。 

2. 在"帳號別名"下，選擇在用於分配訂閱的電子郵件地址旁邊**選擇"主**"。 

> [!div class="mx-imgBorder"]
> ![設置主電子郵件地址](_img//aliasing/account-aliases.png)

3. 登出視覺化工作室訂閱門戶 （https://my.visualstudio.com) 

4. 使用用於分配訂閱的帳戶重新登錄，該帳戶現在應該配置為主別名。 

## <a name="preventing-aliasing-issues"></a>防止鋸齒化問題

作為管理員，有兩個選項可確保您的訂閱者在 上[https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)具有成功的登錄體驗。
- 第一個選項（建議）是利用目錄帳戶作為 Visual Studio 訂閱門戶的https://my.visualstudio.com登錄。  
- 第二個選項（安全性較低）是允許訂閱者使用與其目錄電子郵件地址不同的電子郵件地址登錄。

通過完成以下步驟，在監管中心中配置了這兩個選項：  
1. 登錄[https://manage.visualstudio.com](https://manage.visualstudio.com) 

0. 如果要更改單個使用者，請在表中選擇該使用者，然後按右鍵以進行編輯。 這將打開一個面板，您可以在其中修改登錄電子郵件地址。 在登錄電子郵件地址欄位中進行必要的更新。 按一下"保存"，更改將生效。  

0. 如果需要對大量使用者進行這些更改，可以使用大量編輯功能。 有關詳細資訊，[請使用大量編輯文章閱讀編輯多個訂閱者](https://docs.microsoft.com/visualstudio/subscriptions/edit-license#edit-multiple-subscribers-using-bulk-edit)。

> [!NOTE]
> 對於個人和批量更改，訂閱者將收到一封電子郵件，其中包含其登錄電子郵件地址已更改且需要使用更新的電子郵件地址登錄的電子郵件。 還必須注意，如果訂閱者以前在其他登錄位址下啟動了權益，則需要繼續使用其他登錄位址來訪問它們。  

## <a name="see-also"></a>另請參閱
- [視覺化工作室文檔](https://docs.microsoft.com/visualstudio/)
- [Azure 開發人員文檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [微軟 365 文檔](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>後續步驟
詳細瞭解如何管理視覺化工作室訂閱。
- [分配單個訂閱](assign-license.md)
- [分配多個訂閱](assign-license-bulk.md)
- [編輯訂閱](edit-license.md)
- [確定最大使用量](maximum-usage.md)


