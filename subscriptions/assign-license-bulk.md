---
title: 指派 Visual Studio 訂用帳戶使用者群組的授權 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 05/10/2020
ms.topic: how-to
description: 瞭解系統管理員如何使用大量新增功能或 Microsoft Azure Active Directory 群組，將授權指派給多個訂閱者
ms.openlocfilehash: 8bda423ccd5362fba6389195814a44cca286b5a7
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87235130"
---
# <a name="assign-subscriptions-to-multiple-users"></a>指派訂閱給多個使用者
訂用帳戶系統管理入口網站可讓您以一次一個或以大型群組方式新增使用者。  若要新增個別使用者，請參閱[新增單一使用者](assign-license.md)。

若要新增大量使用者群組，您可以使用大量新增功能，或者如果您的組織使用 Microsoft Azure Active Directory （Azure AD），您可以使用 Azure AD 群組。 本文將說明這兩個選項的程式。 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vxNq]

## <a name="use-bulk-add-to-assign-subscriptions"></a>使用大量新增來指派訂閱
1. 登入 Visual Studio 訂用帳戶管理入口網站，網址為 <https://manage.visualstudio.com> 。

1. 若要一次加入多個訂閱者，請流覽至 [**管理訂閱者**] 索引標籤。選擇 [**新增**] 索引標籤，然後在下拉式選單中選擇 [**大量新增**]。  

1. 大量新增使用 Microsoft Excel 範本來上傳訂閱者資訊。 在 [Upload Multiple Subscribers] (上傳多位訂閱者)　對話方塊中，按一下 [下載]**** 來下載範本。
   > [!div class="mx-imgBorder"]
   > ![下載 Excel 範本，以上傳多位訂閱者](media/download-template-upload-subscribers.png "下載空白 Excel 範本以開始大量指派程式。")
   >
   > [!NOTE]
   > 請一律下載這個範本的最新版本。 如果您使用舊版本，則大量上傳可能會失敗。

1. 在 Excel 試算表中，請將您想要指派訂用帳戶之個人的資訊填入欄位中。 （*參考*是選擇性欄位）。完成之後，請將檔案儲存在本機。

    > [!NOTE]
    > 範本中的其中一個欄位可讓系統管理員啟用或停用訂閱者下載軟體的能力。  停用下載也會停用其產品金鑰的存取權。

   為了協助確保順利上傳，請觀察下列最佳做法：

    - 確定表單欄位未包含逗號。
    - 移除表單欄位前後的空格。
    - 請確定使用者名稱在兩段式名字或姓氏之間未包含額外的空格 (例如，如果某人的名字有兩個部分，如 "Maggie May"，應該鍵入為 "MaggieMay"，因為系統不會修剪額外的空格)。
    - 請確定所有必要的欄位皆已完成。 
    - 檢查 [**錯誤訊息**] 資料行。  如果列出任何錯誤，請在嘗試上傳檔案之前先解決。 

1. 回到 Visual Studio 訂閱管理入口網站。 在 [上傳多位訂閱者]**** 對話方塊中，按一下 [瀏覽]****。
   > [!div class="mx-imgBorder"]
   > ![瀏覽至先前儲存的範本，以上傳多位訂閱者](media/bulk-add-browse-saved-template.png "您可以流覽至檔案位置，或將它拖放到這個對話方塊中。")

1. 巡覽至您儲存的 Excel 檔案，然後按一下 [確定]****。
   > [!div class="mx-imgBorder"]
   > ![上傳 Excel 範本，以上傳多位訂閱者](media/bulk-upload-subscribers.png "您的資料將會出現在此範本中。 按一下 [確定] 開始上傳。")

    上傳進度對話方塊隨即出現。

    如果範本包含錯誤，則上傳會失敗，而且您會看到錯誤，因此您可以修正範本，並嘗試重新大量上傳。
   > [!div class="mx-imgBorder"]
   > ![當上傳多位訂閱者失敗時顯示錯誤訊息](_img/assign-license-bulk/bulk-add-upload-failure.png "如果您上傳的檔案包含錯誤，則會顯示此訊息。 請解決錯誤，然後再次執行大量新增進程。")

   如果您遇到失敗，請遵循下列步驟：
   1. 開啟您建立的 Excel 檔案，更正問題，然後儲存檔案。
   0. 返回 [node.js] 入口網站，然後選擇 [**新增**]。
   0. 選取 [**大量新增**]。
   0. 因為您已經儲存 Excel 檔案，所以您不需要下載範本。  按一下 **[流覽]**，找出您剛儲存的檔案，然後按一下 [**開啟**]。
   0. 按一下 [確定]。


    上傳成功時，您會看到訂閱者清單和確認訊息。
   > [!div class="mx-imgBorder"]
   > ![當上傳多位訂閱者成功時顯示確認訊息](_img/assign-license-bulk/bulk-add-upload-success.png "當您的上傳成功完成時，您會收到確認訊息。")

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>使用 Azure Active Directory 群組來指派訂閱 
使用這項功能可讓您輕鬆地掌握訂用帳戶指派。 您可以在訂用帳戶系統管理入口網站中新增 Azure Active Directory 安全性群組，以確保群組中的所有人員都已獲指派訂閱。 為了讓您更輕鬆，當個人離開您的組織並從 Azure Active Directory 中移除時，也會移除他們對訂閱的存取權。 


> [!IMPORTANT]
>
> 下列限制適用于用於新增訂閱者的 Azure AD 群組：
> - 當您一開始將群組新增至管理入口網站時，系統管理員必須是 AAD 租使用者的成員。  新增群組之後，對群組成員資格的變更不需要系統管理員介入。 
> - 群組必須包含至少一個成員。  不支援空的群組。
> - 群組必須少於1000個使用者。 
> - 所有使用者都必須位於群組的最高層級。  「不支援」巢狀群組。
> - 僅支援信任的合約。
> - 群組的所有成員都必須有與其 Azure AD 帳戶相關聯的電子郵件地址。
> - 使用 Azure AD 群組新增的訂閱不支援個別的通知電子郵件地址。  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

1. 登入 Visual Studio 訂用帳戶管理入口網站，網址為 [https://manage.visualstudio.com](https://manage.visualstudio.com) 。

2. 若要一次加入多個訂閱者，請流覽至 [**管理訂閱者**] 索引標籤。

3. 選擇 [**新增**] 索引標籤，然後在下拉式選單中選取 [ **Azure Active Directory 群組**]。  

   > [!div class="mx-imgBorder"]
   > ![使用 Azure AD 選擇大量新增](_img/assign-license-bulk/bulk-add-aad.png "選擇 [使用 Azure AD 大量新增] 功能，從您的 Azure Active Directory 群組提取訂閱者。")

4. 開始輸入您想要新增至 [表單] 欄位的 Azure AD 組名。 這會在您的組織內搜尋可用的 Azure AD 群組。 

5. 當您選取群組時，欄位會自動填入組名。 在新增群組之前，您可以選擇先查看該群組中的使用者。 接下來，您可以選擇訂用帳戶層級、下載許可權，以及群組的通訊喜好設定。 如有需要，您可以將詳細資料新增至參考欄位。 

   > [!div class="mx-imgBorder"]
   > ![選擇您的 Azure AD 群組](_img/assign-license-bulk/bulk-add-aad-details.png "選擇您的 Azure AD 組名，以從該群組新增訂閱者。")

6. 依序按一下 [**新增**] 和 [**確認**]。 

7. 若要查看新增的群組，請前往使用者清單的底部。  

8. 選取 [ **View 訂閱者**] 以顯示群組的成員。 您可以在群組中查看訂閱者的詳細資料，但無法對訂閱者或其指派的訂閱進行任何編輯。    

> [!NOTE]
> 如果您已將訂用帳戶個別指派給後續新增為 Azure AD 群組之一部分的使用者，這些訂用帳戶將會新增為群組的一部分，且不會再個別列出。 不過，如果個別的訂用帳戶屬於不同的訂用帳戶層級，則會有兩個訂閱。  範例：如果使用者擁有個別的 Visual Studio Professional 訂用帳戶，而他們是您指派 Visual Studio Enterprise 訂閱之群組的成員，則兩者都有。  


## <a name="frequently-asked-questions"></a>常見問題集
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>問：我可以選擇要在 Azure AD 群組中指派多個訂用帳戶層級嗎？ 
答：否--群組中的每個人都會收到相同的訂用帳戶。 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>問：我可以編輯 Azure AD 群組中新增之個人的訂閱者詳細資料嗎？  
答：否--若要修改個別訂閱者的資訊，您必須將其從 Azure AD 安全性群組中移除，並個別為其指派訂用帳戶。  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>問：我已將某人新增到我的 Azure AD 安全性群組，但在訂用帳戶系統管理入口網站中看不到它們，而且他們沒有訂用帳戶。 為什麼不用？  
答：根據您的組織設定 Azure AD 的方式，您可能會在新增使用者之前，看到最多24小時的延遲。 如果超過24小時，[請聯絡支援](https://visualstudio.microsoft.com/support/support-overview-vs)人員。  

## <a name="see-also"></a>另請參閱
- [Visual Studio 文件](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [Microsoft 365 檔](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>後續步驟
- 只有一或兩個訂閱者要新增嗎？  參閱[新增單一使用者](assign-license.md)
- 需要協助嗎？ 連絡人[Visual Studio 系統管理與](https://visualstudio.microsoft.com/support/support-overview-vs)訂用帳戶支援。
