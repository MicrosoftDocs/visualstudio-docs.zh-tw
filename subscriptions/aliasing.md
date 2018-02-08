---
title: "登入 Visual Studio 訂用帳戶可能會因為別名而失敗 | Microsoft Docs"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/2/2018
Ms.topic: Get-Started-Article
Description: Sign-in may fail if aliases or friendly names are used.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 8c07bc8d3cf674d86c2152ff80f20e4fac003fc3
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-with-aliases"></a>登入 Visual Studio 訂用帳戶可能會因為別名而失敗

視用於登入的帳戶類型而定，當登入 [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) 時，可用的訂用帳戶可能無法正確顯示。其中一個可能的原因是使用「別名」或「易記名稱」，而非使用訂用帳戶指派目標的登入身分識別。 這稱為「別名處理」。 

## <a name="what-is-aliasing"></a>別名處理是什麼？

「別名處理」一詞指的是使用不同身分識別來登入 Windows (或您的 Active Directory) 並存取電子郵件的使用者。

當公司使用 Microsoft Online Service 做為其目錄登入使用 (例如 JohnD@contoso.com)，但使用者使用別名或易記名稱存取其電子郵件帳戶 (例如 John.Doe@contoso.com) 時，就會發生別名處理。針對透過大量授權服務中心 (VLSC) 管理其訂用帳戶的客戶，這會導致不成功的登入體驗，因為提供的電子郵件地址 (John.Doe@contoso.com) 不符合成功透過 [公司或學校帳戶] 選項驗證所需的目錄地址 (JohnD@contoso.com)。

## <a name="as-an-administrator-what-options-do-i-have"></a>身為系統管理員，我有哪些選項？

身為系統管理員，[https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) 上有兩個選項可確保您的訂閱者可獲得成功的登入體驗。 
1. 第一個選項 (建議使用) 是利用目錄帳戶作為大量授權服務中心 (VLSC) 中的已指派地址。 如需詳細資訊，請參閱此文章中的[將訂閱者指派到目錄帳戶](#assigning-subscribers-to-a-directory-account)一節。
2. 第二個選項 (較不安全) 是允許您的訂閱者將其「公司或學校」電子郵件地址與「個人」帳戶 (亦即 Microsoft 帳戶或 MSA) 建立關聯。 如需詳細資訊，請參閱此文章中的[將公司或學校帳戶定義為個人帳戶](#defining-a-work-or-school-account-as-a-personal-account )一節。

> [!NOTE]
> 一旦您的公司移轉到新的 Visual Studio 訂用帳戶[管理入口網站](https://manage.visualstudio.com)，您將可以獲得新系統管理體驗的優點，此體驗允許使用者提供目錄與電子郵件地址作為訂閱者設定檔的一部分。  深入了解[移轉](https://support.microsoft.com/help/4013930/visual-studio-subscriptions-administrator-migration-details)。

## <a name="as-a-subscriber-what-options-do-i-have"></a>身為訂閱者，我有哪些選項？

從訂閱者觀點來看，先與您的系統管理員合作以了解您公司的身分識別設定非常重要。  如果有需要，您的系統管理員可能必須從其系統管理入口網站更新您的帳戶設定，或您可能需要使用您的公司電子郵件地址建立 Microsoft 帳戶 (MSA)。  採取建立 MSA 的步驟之前，請先就採取此步驟可能涉及的任何原則或問題洽詢您的系統管理員。  如需詳細資訊，請參閱此文章中的[將公司或學校帳戶定義為個人帳戶](#defining-a-work-or-school-account-as-a-personal-account )一節。  

## <a name="assigning-subscribers-to-a-directory-account"></a>將訂閱者指派到目錄帳戶 

在所有案例中，大量授權服務中心 (VLSC) 中的訂閱管理員都必須使用新訂閱者的目錄地址，或更新「現有」訂閱者的電子郵件地址。  請務必了解使用目錄地址表示任何新的訂閱者都不會收到歡迎電子郵件，系統管理員將必須通知訂閱者訂閱已被指派給他們。  依照下面的步驟執行之後，您也可以使用電子郵件[範本](#notifying-your-subscribers-with-directory-addresses)來通知您的訂閱者，並協助他們完成登入程序。

### <a name="adding-new-subscribers"></a>指派新的訂閱者
請依照這些步驟使用目錄帳戶新增訂閱者。

1. 瀏覽[大量授權服務中心](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (VLSC) 並登入。
2. 從 VLSC [系統管理] 頁面，按一下 [訂用帳戶]，然後按一下 [Visual Studio 訂用帳戶]。

    ![[ 訂用帳戶] 功能表](_img//vlsc/vlsc-subscriptions.png)

3. 按一下與該 Visual Studio 訂用帳戶關聯的 [合約編號]。

    ![選取合約](_img/vlsc/vlsc-agreement.png)

4. 按一下 [指派訂用帳戶]。

    ![指派訂用帳戶](_img/vlsc/vlsc-assign.png)

5. 選取想要的 [訂用帳戶層級]。

    ![訂用帳戶層級](_img/vlsc/vlsc-subscription-level.png)
    
6. 驗證您有可指派的訂用帳戶，然後按一下 [下一步]。
7.  輸入訂閱者詳細資料並在 [電子郵件地址] 中輸入目錄地址，然後按一下 [下一步]。

    ![電子郵件地址](_img/vlsc/vlsc-email-address.png)
    
8. 驗證訂閱者資訊，然後按一下 [完成]。

9. 使用下面的[範本](#notifying-your-subscribers-with-directory-addresses)通知訂閱者其訂用帳戶已佈建。

### <a name="updating-an-existing-subscriber"></a>更新現有的訂閱者
請依照下面的步驟使用目錄帳戶更新現有的訂閱者。

1. 瀏覽[大量授權服務中心](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (VLSC) 並登入。

2. 從 VLSC [系統管理] 頁面，按一下 [訂用帳戶]，然後按一下 [Visual Studio 訂用帳戶]。

3. 按一下與該 Visual Studio 訂用帳戶關聯的 [合約編號]。

4. 按一下 [搜尋] 列上的向下箭號 。

5. 使用 [電子郵件地址] 欄位搜尋訂閱者。

6. 從結果清中，按一下 [訂閱者] 上的 [姓氏]。

7. 按一下 [編輯]。

8. 將 [電子郵件地址] 欄位變更為想要的目錄地址，然後按一下 [儲存]。

9. 使用下面的電子郵件範本通知訂閱者其訂用帳戶已佈建。

### <a name="notifying-your-subscribers-with-directory-addresses"></a>使用目錄地址通知您的訂閱者
因為歡迎電子郵件將無法成功地傳送給您的訂閱者，請將下面的訊息複製並貼上到電子郵件中並傳送給您的訂閱者。 針對每個訂閱者，將 %WORD% 取代為適當的資訊。

----------- 複製下面的內容 (Ctrl+C) -----------

%SUBSCRIBER NAME%，您好

您已被指派 Visual Studio 訂用帳戶。  請瀏覽 https://my.visualstudio.com 並使用您的 %DIRECTORY ADDRESS% 地址登入，以啟用並存取您的訂用帳戶。 

若您有任何問題，請連絡支援小組 (https://www.visualstudio.com/subscriptions/support/)。

在頁面底部，選取下列項目：
   - [帳戶]、[訂用帳戶] 與 [計費支援]
   - 從 [問題] 中，選擇 [訂用帳戶登入支援]
   - 選擇適當的 [國家/地區]
   - 選取想要的 [輔助支援] 選項

----------- 複製到這裡 -----------



## <a name="defining-a-work-or-school-account-as-a-personal-account"></a>將公司或學校帳戶定義為個人帳戶 
請依照[將訂閱者指派到目錄帳戶](#assigning-subscribers-to-a-directory-account)一節中所述的步驟在大量授權服務中心 (VLSC) 中新增使用者或更新現有使用者的電子郵件地址。  在目錄無法識別電子郵件地址的情況下，使用者將必須逐步執行步驟以建立新的帳戶，以將新的電子郵件地址定義為個人帳戶。  Visual Studio 訂用帳戶小組從下面定義的身分識別原則建立了短期豁免，但我們正在研究移除此原則的必要功能。

> [!WARNING]
> Microsoft 建議您不要將「公司或學校」身分識別與「個人」身分識別結合。  此動作會使得組織失去帳戶擁有權與控制能力，而且即使員工離開公司，仍可存取特定產品或服務。  如需詳細資訊，請參閱來自 Microsoft Identity 小組的此[部落格文章](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/15/cleaning-up-the-azure-ad-and-microsoft-account-overlap/)。

### <a name="defining-an-email-address-as-a-personal-account"></a>將電子郵件地址定義為個人帳戶
在訂閱指派給訂閱者之後，他們將會收到要求他們瀏覽 https://my.visualstudio.com 以發揮其訂用帳戶優點的電子郵件。  當嘗試登入時，Visual Studio 訂用帳戶登入會失敗，並傳回說明無法識別帳戶的錯誤。  請要求您的訂閱者先依照這些步驟執行再登入 https://my.visualstudio.com experience。  如果有需要，您可以在指派訂閱之後使用此[範本](#notifying-your-subscribers-using-personal-accounts)來通知您的訂閱者。

1. 瀏覽 https://my.visualstudio.com，然後按一下 [建立新的 Microsoft 帳戶]。

2. 完成欄位：
    - 在 Someone@example.com 方塊中輸入收到歡迎電子郵件的電子郵件地址
    - 建立您的密碼
    - 選擇您的推廣設定
    - 按一下 [下一步]

3. 完成驗證步驟並按一下 [下一步]。

4. 新使用者可能需要完成 Visual Studio 設定檔。

5. 訂用帳戶與權益現在應該可見。

### <a name="notifying-your-subscribers-using-personal-accounts"></a>使用個人帳戶通知您的訂閱者

在上面所述的案例中，您的訂閱者將會收到「歡迎電子郵件」，但由於別名處理，他們可能會發現他們無法登入。  您可以使用下面的文字來通知您的訂閱者上述步驟，並視需要建議支援選項。  針對每個訂閱者，將 %WORD% 取代為適當的資訊。

----------- 複製下面的內容 (Ctrl+C) -----------

%SUBSCRIBER NAME%，您好

您已被指派 Visual Studio 訂用帳戶，而且根據您的歡迎電子郵件，您可能被要求登入 https://my.visualstudio.com。  雖然這是取用權益的正確網站，但我們的組織要求您執行一些額外步驟以存取網站。  請依照下面的指示執行，以建立與我們的公司電子郵件地址繫結的「Microsoft 帳戶」。  一旦完成這些步驟，您就可以使用您的電子郵件地址來存取訂用帳戶權益。
1. 瀏覽 https://my.visualstudio.com

2. 按一下右邊的 [建立新的 Microsoft 帳戶]

3. 完成表單： 
    - 在 someone@example.com 方塊中使用您的公司電子郵件地址
    - 輸入密碼
    - 選取您的推廣喜好設定
    - 按一下 [下一步]

4. 完成帳戶驗證步驟

5. 如果有需要，請完成 Visual Studio 設定檔

6. 您現在應該會看到您的權益

注意：未來瀏覽 https://my.visualstudio.com 時，系統可能會提示您選取要使用的帳戶 (例如「公司或學校帳戶」或「個人帳戶」)。  依照上面的步驟執行之後，您將需要選擇 [個人帳戶] 選項。

若您有任何問題，請連絡支援小組 (https://www.visualstudio.com/subscriptions/support/)。

在頁面底部，選取下列項目：
   - [帳戶]、[訂用帳戶] 與 [計費支援]
   - 從 [問題] 中，選擇 [訂用帳戶登入支援]
   - 選擇適當的 [國家/地區]
   - 選取想要的 [輔助支援] 選項

----------- 複製到這裡 -----------