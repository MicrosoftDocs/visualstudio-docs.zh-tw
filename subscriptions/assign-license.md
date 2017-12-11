---
Title: "指派 Visual Studio 訂用帳戶的授權"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: "了解系統管理員如何指派訂閱者授權"
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: e2a32e911c85603b2d08adb0edad76bcfbc6d6ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>在 Visual Studio 訂用帳戶系統管理員入口網站中指派授權
## <a name="assigning-a-single-user"></a>指派單一使用者
如果您有可用的 Visual Studio 訂用帳戶授權，則可以將這些授權指派給新使用者，讓他們可以存取其訂用帳戶權益。 
1.  若要指派單一 Visual Studio 訂閱者，請按一下資料表頂端的 [新增]。

![新增訂閱者](_img\assign-license-add\assign-license-add.png)

2.  將資訊輸入至新訂閱者的表單欄位。 如果您的組織使用 Azure Active Directory，則此欄位作為搜尋函式來尋找您目前目錄中的人員，因此您可以從搜尋結果中選取正確的使用者。 選取該人員之後，會自動填入其名稱、登入電子郵件和通知電子郵件，如下所示。 

如果您的組織用來接收電子郵件的電子郵件與登入的電子郵件不同，則可以選擇在這裡輸入它。 選取超連結，指出「進行通訊的電子郵件與登入的電子郵件不同嗎」？ 

如果您想要此訂閱者可以登入 [Visual Studio 訂用帳戶入口網站](https:/my.visualstudio.com)，而且可以存取軟體下載以及所有其他訂用帳戶服務和資源 (包含 Microsoft Azure、Visual Studio Team Services、Xamarin 和 Pluralsight 訓練、技術支援和其他項目)，請務必選取 [下載] 方塊。 如果您選擇取消核取此方塊，則使用者無法存取軟體下載，但訂用帳戶中所含之所有其他權益的存取權不受影響。 完成後，請按一下 [新增]。

![輸入訂閱者資訊](_img\assign-license-add\add-subscriber-1.png)
![輸入訂閱者資訊](_img\assign-license-add\add-subscriber-2.png)

3.  新增訂閱者之後，會將具有進一步指示的指派電子郵件自動傳送給新訂閱者。 您可以按一下上方功能表中的 [重新傳送] 按鈕，隨時重新傳送指派電子郵件。

![已新增訂閱者](_img\assign-license-add\add-subscriber-complete.png)

## <a name="bulk-assignments"></a>大量指派
1.  若要一次新增多位訂閱者，請巡覽至 [訂閱者] 索引標籤。在上方功能區中，按一下 [大量新增]。 

![大量新增](_img\assign-license-add\bulk-assign-add.png)

2. 大量指派會使用 Microsoft Excel 範本來上傳訂閱者。 在 [Upload Multiple Subscribers] (上傳多位訂閱者)　對話方塊中，按一下 [下載] 來下載範本。 請一律下載這個範本的最新版本。 如果您使用舊版本，則大量上傳可能會失敗。
!Upload Multiple Subscribers] (上傳多位訂閱者) (_img\assign-license-add\bulk-assign-upload.png)
3.  在 Excel 試算表中，請將您想要指派訂用帳戶之個人的資訊填入欄位中。 參考是選擇性欄位。 如果您已正確填入範本的任何部分，則應該會看到描述問題的錯誤訊息。 完成時，請將檔案儲存至硬碟。
**為了協助確保順利上傳，請觀察下列最佳做法：**
- 確定表單欄位未包含逗號。
- 移除表單欄位 (例如使用者名稱) 前後的空格。
- 請確定使用者名稱未包含兩部分名字或姓氏之間的額外空格 (例如，兩部分名字 (例如 "Maggie May") 不應該鍵入為 "Maggie  May"，因為系統不會修剪額外空格)

![大量新增範本](_img\assign-license-add\bulk-template.png)

4.  返回 Visual Studio 訂用帳戶管理入口網站，並在 [Upload Multiple Subscribers] (上傳多位訂閱者) 對話方塊中按一下 [瀏覽]。 巡覽至您儲存的 Excel 檔案，然後按一下 [確定]。 您會在螢幕上看到上傳進度。 

![大量新增上傳](_img\assign-license-add\bulk-assign-upload-2.png)

如果範本包含錯誤，則上傳會失敗，而且您會看到錯誤，因此您可以修正範本，並嘗試重新大量上傳。

![上傳失敗](_img\assign-license-add\bulk-assign-upload-fail.png)

上傳成功時，您會看到訂閱者清單和確認訊息。

![上傳完成](_img\assign-license-add\bulk-assign-upload-complete.png)