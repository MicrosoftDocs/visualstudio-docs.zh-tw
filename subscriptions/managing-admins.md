---
title: "在 Visual Studio 訂用帳戶系統管理員入口網站中管理系統管理員權限"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/19/2018
Ms.topic: Get-Started-Article
Description: Learn how manage admins & super admins in the Visual Studio Subscriptions Administrator Portal.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 83bf27d5aaa99c2095ad8a1fafd7541df90f316b
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="managing-administrator-rights-in-the-visual-studio-subscriptions-administrator-portal"></a>在 Visual Studio 訂用帳戶系統管理員入口網站中管理系統管理員權限

## <a name="overview"></a>概觀 
在 Visual Studio 訂用帳戶系統管理員入口網站 (https://manage.visualstudio.com) 中，有兩個管理角色：

**超級系統管理員：**第一次設定組織時，主要或通知連絡人預設會成為超級系統管理員。 主要或通知連絡人可以選擇指派其他的超級系統管理員或系統管理員。 除了管理個別訂閱者的訂用帳戶之外，超級系統管理員還可以新增或移除其他系統管理員與其他超級系統管理員。 如果系統中有兩個以上的超級系統管理員，則超級系統管理員可以刪除所有超級系統管理員，但最後必須保留兩個以策安全。 

**系統管理員：**系統管理員可以管理超級系統管理員在合約中指派給他們的訂閱者。  他們可以將訂用帳戶指派給個人、編輯訂用帳戶，以及新增或移除訂用帳戶。   (系統管理員是由超級系統管理員指派。)  

## <a name="adding-an-administrator-with-super-admin-rights"></a>**使用**超級系統管理員權限新增系統管理員：

1. 使用具有超級系統管理員權限的帳戶登入 Visual Studio 訂用帳戶[系統管理員入口網站](https://manage.visualstudio.com)。

2. 按一下頁面頂端的 [管理系統管理員] 索引標籤。 (只有超級系統管理員可以存取此索引標籤。沒有超級系統管理員權限的系統管理員必須使用 [管理訂閱者] 索引標籤來管理個別訂閱者。)

3. 按一下 [新增] 以建立新系統管理員。 

4. 填寫 [新增系統管理員] 快顯視窗中的所有必要詳細資料。
  - 若您的組織已註冊 Azure Active Directory (AAD)，請開始在 [名稱] 欄位中輸入名稱，並在下拉式清單中選取正確的項目。 針對新使用者，輸入全名並忽略 [找不到任何識別] 通知。
  - 一旦識別正確的使用者，將會自動填寫 [登入電子郵件地址] 欄位。 若尚未提供新系統管理員電子郵件地址，請輸入新系統管理員電子郵件地址。

5. 選取您要指派給新系統管理員管理的 [PCN]，方式是按一下 [合約] 下的下拉式清單。 若您要讓其上線的PCN 之下有一或多個合約，您可以為系統管理員提供可以存取這些合約的權限。 

**更多關於合約的事項：**當只有一個合約可用時，[合約] 下的下拉式功能會停用。  當您正在設定的使用者被授與超級系統管理員權限時，會自動選取所有合約。

6. 按一下 [超級系統管理員] 方塊以為此系統管理員啟用超級系統管理員權限。  

7. 若要完成新增此系統管理員的作業，請按一下 [新增]。

**新增系統管理員時可能會收到的錯誤：**某些使用者可能會在嘗試新增系統管理員時收到錯誤訊息。 如果要新增的超級系統管理員電子郵件地址未列在公司的 AAD 中，很可能就會發生此情況。 若要完成新增系統管理員的作業，只要忽略該錯誤並再次按一下 [新增] 即可。 

8. 建立超級系統管理員之後，您將會在系統管理員清單中看到他們，而且其帳戶將以綠色核取記號來標示以指出其超級系統管理員狀態。 

### <a name="optional--add-a-different-notification-email"></a>選擇性：新增不同的通知電子郵件。
若您的組織使用不同的地址/帳戶來接收電子郵件，您現在可以輸入「通訊」地址。 選取 [Add a different notification email for receiving communication] \(新增不同的通知電子郵件以接收通訊)\。 

*範例：*當 Rene 使用其公司認證登入時，他使用 rene@contoso.com。  不過，Rene 的公司只使用該地址來管理目錄存取。  傳送及接收電子郵件時，Rene 使用 rene.collado@contoso.com，因此其超級系統管理員已輸入第二個地址以確保不會漏接歡迎郵件。  若您的公司未這樣設定，則輸入 [登入電子郵件地址] 應該就足夠。

## <a name="adding-an-administrator-without-super-admin-rights"></a>在**沒有** 超級系統管理員權限的情況下新增系統管理員：

您必須依照上述相同程序，才能在沒有超級系統管理員權限的情況下新增系統管理員，但考量下列方面：
-  在沒有超級系統管理員權限的情況下新增系統管理員時，不需要新增額外電子郵件地址，而且 [超級系統管理員] 核取方塊會維持空白。
-  沒有超級系統管理員權限的使用者在其設定檔組態項目中的 [管理系統管理員] 下不會看到綠色核取記號圖示。
