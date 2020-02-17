---
title: 登入 Visual Studio 訂用帳戶可能會因為使用別名而失敗 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/14/2020
ms.topic: conceptual
description: 登入可能會因為使用別名或易記名稱而失敗
ms.openlocfilehash: dff48852e566522ad01ee07bd46cda72b8e1e249
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2020
ms.locfileid: "77276629"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>登入 Visual Studio 訂用帳戶可能會因為使用別名而失敗
視用於登入的帳戶類型而定，當登入 [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) 時，可用的訂用帳戶可能無法正確顯示。 其中一個可能的原因是使用「別名」或「易記名稱」，而非使用訂用帳戶指派目標的登入身分識別。 這稱為「別名處理」。

## <a name="what-is-aliasing"></a>別名處理是什麼？
「別名處理」一詞指的是使用不同身分識別來登入 Windows (或您的 Active Directory) 並存取電子郵件的使用者。

當公司使用 Microsoft Online Service 作為其目錄登入使用 (例如 olivia@contoso.com)，但使用者以別名或易記名稱存取其電子郵件帳戶 (例如 OliviaG@contoso.com) 時，就會發生別名處理。 請確定您的使用者使用「登入電子郵件地址」進行登入，如 Visual Studio 訂用帳戶管理入口網站中所列的 https://manage.visualstudio.com 存取其訂閱

## <a name="as-an-administrator-what-options-do-i-have"></a>身為系統管理員，我有哪些選項？

視訂閱者的帳戶類型而定，尋找下列適用的解決方案：

### <a name="work-or-school-account-upn-mismatch-issue"></a>工作或學校帳戶 UPN 不相符的問題

當公司具有使用中的 Diretory 設定，其中 UPN 與主要 SMTP 位址不相同時，就可能會發生使用者主體名稱（UPN）不符的情況。 

#### <a name="how-to-detect-if-a-users-sign-in-address-has-a-upn-mismatch"></a>如何偵測使用者的登入位址是否有 UPN 不符

讓使用者完成下列步驟：

1. 使用其訂用帳戶指派電子郵件中所述的登入位址，登入 https://my.visualstudio.com。  

    > [!NOTE]
    > 如果他們沒有訂用帳戶指派電子郵件，您可以從公司入口網站中將其重新傳送給他們。  

2. 按一下 [訂閱] 索引標籤。
3. 確認顯示在右上方的電子郵件地址指出「您的登入身分 ...」與其訂用帳戶指派電子郵件中的登入電子郵件地址相同。  如果沒有，則無法存取其訂閱權益。 

   > [!div class="mx-imgBorder"]
   > ![訂閱 頁面](_img/aliasing/aliasing-subscriptions-page.png)

#### <a name="how-to-correct-the-upn-mismatch"></a>如何修正 UPN 不相符的問題

1. 存取 Visual Studio 系統管理管理入口網站，網址為 https://manage.visualstudio.com 

2. 找出具有 UPN 不符問題的使用者。  如果您有許多訂用帳戶，[篩選](search-license.md)功能可以讓您更輕鬆。 

3. 將登入電子郵件地址變更為使用者的 UPN。

4. 儲存變更 

5. 要求使用者登出訂閱者入口網站，並使用 UPN 重新登入。   

### <a name="personal-account-aliasing-issue"></a>個人帳號別名問題

別名問題也會影響個人帳戶。 

#### <a name="how-to-detect-if-a-personal-account-has-an-aliasing-issue"></a>如何偵測個人帳戶是否有別名問題

1. 登入 https://my.visualstudio.com。

2. 按一下 [**訂閱**] 索引標籤，並檢查您已登入的位址。 

3. 如果登入的電子郵件地址與用來存取網站的電子郵件地址不同，則您的帳戶與別名之間會發生衝突。 

#### <a name="how-to-fix-a-personal-account-aliasing-issue"></a>如何修正個人帳號別名問題

Visual Studio 訂用帳戶平臺會將主要別名的優先順序設為 [顯示訂閱詳細資料]。  若要解決此問題，您必須使用不同的電子郵件別名做為登入的主要別名。 

1. 移至 [[管理您登入 Microsoft 的方式](https://go.microsoft.com/fwlink/p/?linkid=842796)]。
2. 若出現提示，請登入您的 Microsoft 帳戶。 
3. 在 [帳號別名] 底下，選取用來指派訂閱的電子郵件地址旁的 [**設為主要**]。 
4. 在 [帳號別名] 底下，選取用來指派訂閱的電子郵件地址旁的 [設為主要]。 
5. 登出 Visual Studio 訂閱者入口網站（ https://my.visualstudio.com) 
6. 使用新的主要別名再次存取入口網站。 

### <a name="ensure-a-successful-experience-for-your-users"></a>確保您的使用者體驗成功

身為系統管理員，有兩個選項可確保您的訂閱者在 https://my.visualstudio.com上具有成功的登入體驗。 

- 第一個選項（建議）是利用目錄帳戶作為 https://manage.visualstudio.com上的登入位址。
- 第二個選項較不安全，第二個選項（較不安全）是允許您的訂閱者使用不同的電子郵件地址來登入，而不是其目錄電子郵件地址。

在系統管理員入口網站中完成下列步驟，即可設定這兩個選項：

1. 登入 https://manage.visualstudio.com 

2. 如果您要改變單一使用者，請在資料表中選取該使用者，並以滑鼠右鍵按一下以編輯。 這會開啟一個面板，您可以在其中修改登入電子郵件地址。  

3. 在 [登入電子郵件地址] 欄位中進行必要的更新。 

4. 按一下 [儲存]，變更就會生效。  
如果您需要對大量的使用者進行這些變更，您可以利用大量編輯功能。 如需該程式的詳細資訊，請參閱我們的 [編輯訂閱]] （編輯-license.md）一文中的「**使用大量編輯來編輯多個訂閱者**」一節。  

## <a name="next-steps"></a>後續步驟
深入瞭解如何管理 Visual Studio 訂閱。
- [指派個別訂閱](assign-license.md)
- [指派多個訂用帳戶](assign-license-bulk.md)
- [編輯訂用帳戶](edit-license.md)
- [刪除訂用帳戶](delete-license.md)
- [判斷最大使用量](maximum-usage.md)

## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](/visualstudio/)
- [Azure DevOps 檔](/azure/devops/)
- [Azure 文件](/azure/)
- [Microsoft 365 檔](/microsoft-365/)
