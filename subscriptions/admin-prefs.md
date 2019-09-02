---
title: 在管理入口網站中設定合約喜好設定
author: evanwindom
ms.author: lank
manager: lank
ms.date: 08/21/2019
ms.topic: conceptual
description: 了解如何在管理入口網站中設定語言、連絡人、訂用帳戶層級及其他喜好設定
ms.openlocfilehash: 24e9ddfa92ee63e4d15eea086224e1069d4bcbc8
ms.sourcegitcommit: c90a998716b3dfa614dedc61a1bea515364efbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "70000978"
---
# <a name="set-preferences-for-your-agreements-in-the-administration-portal"></a>在管理入口網站中設定您合約的喜好設定
超級管理員現在可以在管理入口網站中，設定每個合約會全域套用的特定喜好設定。  這些喜好設定會決定您合約上的系統管理員在新增訂閱者時可以設定哪些內容，以及哪些內容只能由超級管理員全域修改。  

## <a name="access-preferences"></a>存取喜好設定
您必須使用具有合約超級管理員權限的登入識別碼登入[管理入口網站](https://manage.visualstudio.com)，才能檢視或修改喜好設定。  

設定您的喜好設定：
1. 使用具有超級管理員權限的識別碼登入管理入口網站。
2. 按一下 [管理系統管理員]  索引標籤。
   > [!div class="mx-imgBorder"]
   > ![管理員喜好設定按鈕](_img/admin-prefs/admin-prefs-button.png)

3. 按一下 [Agreement Preferences] \(合約喜好設定\)  。
這會在右側開啟一個面板，並顯示您可用的喜好設定。 

   > [!div class="mx-imgBorder"]
   > ![管理員喜好設定飛出視窗對話方塊](_img/admin-prefs/admin-prefs-flyout.png)

## <a name="set-your-preferences"></a>設定您的喜好設定
讓我們探索每個可用的喜好設定及其效果。 

### <a name="agreement"></a>合約
如果您是擁有多份合約的超級管理員，您可以在下拉式清單中選擇所需的合約。  您設定的喜好設定只會套用至該合約。  每位管理員可以在指派訂用帳戶時，根據個別情況覆寫其中一些喜好設定。 

如果只有一個合約與您用來登入的電子郵件地址建立關聯，則會顯示該合約並停用下拉式清單。 

### <a name="contact-email-address"></a>連絡人電子郵件地址
此喜好設定可讓訂閱者透過在訂閱者入口網站的[訂用帳戶頁面](https://my.visualstudio.com/subscriptions)上使用 [Contact my Admin] \(連絡我的管理員\)  按鈕來連絡系統管理員。  如果此喜好設定保留空白，則會將訂閱者訊息轉寄給合約上的所有系統管理員和超級管理員。  建議使用群組電子郵件別名或安全性群組來量身打造此連絡人電子郵件的對象。 如果您想要的話，也可以選擇輸入個人的電子郵件地址。

> [!NOTE]
> 您在此處列出的電子郵件地址「不會」提供給訂閱者。  當訂閱者在訂閱者入口網站中提交 [Contact my Admin] \(連絡我的管理員\)  要求時，訊息會轉寄到別名，而不會向訂閱者公開。 

### <a name="default-external-subscribers-setting"></a>預設外部訂閱者設定
此喜好設定可讓您決定系統管理員是否可以從組織的租用戶/目錄外部新增訂閱者。  如果您關閉此設定，則不允許任何外部訂閱者。  如果您啟用此設定，且管理員嘗試新增外部訂閱者，則會要求他們確認其選擇，並允許他們指派訂用帳戶。 管理員無法覆寫此設定。 

### <a name="default-downloads-setting"></a>預設下載設定
啟用此設定 (預設會開啟) 可讓訂閱者在管理員建立新訂用帳戶時存取下載。  管理員仍然可以根據個別訂用帳戶停用下載。  

### <a name="default-subscription-level"></a>預設訂用帳戶層級
您可以使用此設定來判斷將訂用帳戶指派給使用者時，預設會選取合約中包含的哪個訂用帳戶層級。  管理員可以將設定變更為您合約中的任何訂用帳戶層級，這只是為了避免必須重複進行您最常用的選擇。 

### <a name="default-communication-preferences"></a>預設通訊喜好設定
設定預設通訊語言和地區設定可簡化指派訂用帳戶的程序。  例如，如果您的開發小組與管理小組位於不同的國家/地區，則可以設定最適合訂閱者位置的喜好設定。 個別訂閱者的所有管理員仍然可以變更這些設定。 

## <a name="frequently-asked-questions"></a>常見問題集
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-administrators"></a>問：我可以停用 [連絡人電子郵件地址]  ，讓訂閱者無法連絡系統管理員嗎？
答：否 - 雖然您可以使用安全性群組、群組電子郵件別名或個別電子郵件地址來決定要連絡的系統管理員，但無法停用此功能。

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>問：如果我回覆訂閱者的電子郵件，他們會有我的電子郵件地址嗎？
答：因為您的回覆來自您所使用任何電子郵件用戶端，所以訂閱者收到的回覆會顯示您所使用任何電子郵件地址。  因此，如果您從群組別名回覆，則他們會看到群組別名。  如果您從自己的電子郵件地址回覆，則他們會看到該電子郵件地址。  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>問：我可以從哪裡深入了解訂閱者入口網站中的 [Contact my Admin] \(連絡我的管理員\)  功能？
答：請參閱[連絡我的管理員](contact-my-admin.md)一文。 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>問：如果我們未完成 [連絡人電子郵件地址]  ，且訂閱者使用 [Contact my Admin] \(連絡我的管理員\)  功能，那麼誰會收到其要求？
答：如果 [連絡人電子郵件地址]  喜好設定中未設定特定電子郵件地址，則合約上的所有管理員都會收到要求。 

## <a name="resources"></a>資源
- [Visual Studio 管理與訂閱支援](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="next-steps"></a>後續步驟
- 了解如何[指派訂用帳戶](assign-license.md)
- 深入了解[訂用帳戶權益](https://visualstudio.microsoft.com/vs/benefits/)的完整範圍

