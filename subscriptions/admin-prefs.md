---
title: 在管理入口網站中設定合約喜好設定
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 0fe9eaa4-f589-429e-a443-13bf86637d5a
ms.date: 03/19/2021
ms.topic: conceptual
description: 了解如何在管理入口網站中設定語言、連絡人、訂用帳戶層級及其他喜好設定
ms.openlocfilehash: 93a9417a88d07dcc841c6a59a7353b0ffb5e7565
ms.sourcegitcommit: d8d230791890cda532c263d04288dc13d2261c7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104757616"
---
# <a name="set-preferences-for-your-agreements-in-the-administration-portal"></a>在管理入口網站中設定您合約的喜好設定
超級管理員可以在系統管理員入口網站中設定特定的喜好設定 (系統管理員入口網站) 將會針對每個合約全域套用。  這些喜好設定將會在新增訂閱者時自動填入您系統管理員的訂用帳戶詳細資料，而且只能由超級管理員進行全域修改。  

## <a name="access-preferences"></a>存取喜好設定
您必須使用具有合約超級管理員權限的登入識別碼登入[管理入口網站](https://manage.visualstudio.com)，才能檢視或修改喜好設定。  

設定您的喜好設定：
1. 使用具有超級管理員權限的識別碼登入管理入口網站。
2. 按一下左窗格中的 [設定] 圖示。
   > [!div class="mx-imgBorder"]
   > ![管理員喜好設定按鈕](_img/admin-prefs/admin-prefs-button.png "按一下 [管理管理員]，然後按一下 [協定喜好設定] 以顯示喜好設定")

3. 按一下 [Agreement Preferences] \(合約喜好設定\)。
面板會在左側開啟，並顯示您的可用喜好設定。 

   > [!div class="mx-imgBorder"]
   > ![管理員喜好設定飛出視窗對話方塊](_img/admin-prefs/admin-prefs-flyout.png "設定您的喜好設定，然後按一下 [儲存]")

## <a name="set-your-preferences"></a>設定您的喜好設定
讓我們探索每個可用的喜好設定及其效果。 

### <a name="agreement"></a>合約
如果您有多個您是超級管理員的合約，您將能夠在展開的設定面板右邊的下拉式清單中選擇所需的合約。  您設定的喜好設定只會套用至該合約。  每位管理員可以在指派訂用帳戶時，根據個別情況覆寫其中一些喜好設定。 

如果只有一個合約與您用來登入的電子郵件地址相關聯，它就會顯示在展開的 [設定] 面板右邊，而下拉式清單將會停用。 

### <a name="contact-email-address"></a>連絡人電子郵件地址
此喜好設定可讓您的訂閱者透過在訂閱者入口網站的 [訂用帳戶][頁面](https://my.visualstudio.com/subscriptions)上，使用 [**連絡人我** 的系統管理員] 按鈕來與系統管理員聯繫。  如果此喜好設定保留空白，則會將訂閱者訊息轉寄給合約上的所有系統管理員和超級管理員。  建議使用群組電子郵件別名或安全性群組來量身打造此連絡人電子郵件的對象。 如果您想要的話，也可以選擇輸入個人的電子郵件地址。

> [!NOTE]
> 您在此處列出的電子郵件地址「不會」提供給訂閱者。  當訂閱者在訂閱者入口網站中提交「我的系統 **管理員** 」要求時，會將訊息轉送至該別名，而不會將其公開給「訂閱者」。 

### <a name="default-subscription-level"></a>預設訂用帳戶層級
您可以使用此設定來判斷將訂用帳戶指派給使用者時，預設會選取合約中包含的哪個訂用帳戶層級。  系統管理員可以將此設定變更為您合約中的任何訂用帳戶層級，這只是為了避免重複您最常用的選擇。 

### <a name="default-communication-preferences"></a>預設通訊喜好設定
設定預設通訊語言和地區設定可簡化指派訂用帳戶的程序。  例如，如果您的開發小組與管理小組位於不同的國家/地區，則可以設定最適合訂閱者位置的喜好設定。 個別訂閱者的所有管理員仍然可以變更這些設定。 

### <a name="default-external-subscribers-setting"></a>預設外部訂閱者設定
此喜好設定可讓您決定系統管理員是否可以從組織的租使用者/目錄外部新增訂閱者。  如果您關閉此設定，則不允許任何外部訂閱者。  如果您啟用此設定，且管理員嘗試新增外部訂閱者，則會要求他們確認其選擇，並允許他們指派訂用帳戶。 管理員無法覆寫此設定。 

### <a name="default-downloads-setting"></a>預設下載設定
啟用此設定 (預設會開啟) 可讓訂閱者在管理員建立新訂用帳戶時存取下載。  管理員仍然可以根據個別訂用帳戶停用下載。  停用存取下載也會停用對產品金鑰的存取。  


## <a name="frequently-asked-questions"></a>常見問題集
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-admins"></a>問：我可以停用 **連絡人電子郵件地址** ，讓訂閱者無法連絡系統管理員嗎？
答：不可以，您可以使用安全性群組、群組電子郵件別名或個別的電子郵件地址來判斷要聯繫哪些系統管理員，因此無法停用此功能。

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>問：如果我回答訂閱者的電子郵件，他們是否會有我的電子郵件地址？
答：因為您的回應會來自您所使用的電子郵件客戶程式，所以訂閱者收到的回應將會顯示您所使用的電子郵件地址。  因此，如果您從群組別名回覆，則他們會看到群組別名。  如果您從自己的電子郵件地址回覆，則他們會看到該電子郵件地址。  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>問：我可以在哪裡找到訂閱者入口網站中 [ **Contact My Admin** ] 功能的詳細資訊？
答：請查看我們的「我的系統 [管理員](contact-my-admin.md) 」文章。 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>問：如果我們未完成 **連絡人電子郵件地址** ，而「訂閱者」使用「 **連絡人我** 的系統管理員」功能來接收其要求？
答：如果 **連絡人電子郵件地址** 喜好設定中未設定特定的電子郵件地址，則合約上的所有系統管理員都會收到要求。 

## <a name="resources"></a>資源
- [Visual Studio 管理與訂閱支援](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](/visualstudio/)
- [Azure DevOps 文件](/azure/devops/) \(英文\)
- [Azure 檔](/azure/)
- [Microsoft 365 檔](/microsoft-365/)

## <a name="next-steps"></a>下一步
深入瞭解如何管理 Visual Studio 的訂閱。
- [指派個別訂用帳戶](assign-license.md)
- [指派多個訂用帳戶](assign-license-bulk.md)
- [編輯訂用帳戶](edit-license.md)
- [判斷最大使用量](maximum-usage.md)