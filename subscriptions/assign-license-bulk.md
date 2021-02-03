---
title: 指派 Visual Studio 訂用帳戶使用者群組的授權 | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 02/02/2021
ms.topic: how-to
description: 瞭解系統管理員如何使用「大量新增」功能或 Microsoft Azure Active Directory 群組，將授權指派給多個「訂閱者」
ms.openlocfilehash: 995859dce259b3a4edf968fac98723e226cf59d5
ms.sourcegitcommit: d124123528776993eb5e7461dae8da3975d11d0d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2021
ms.locfileid: "99511367"
---
# <a name="assign-subscriptions-to-multiple-users"></a>指派訂閱給多個使用者
訂用帳戶系統管理入口網站可讓您以一次一個或以大型群組方式新增使用者。  若要新增個別使用者，請參閱[新增單一使用者](assign-license.md)。

若要加入大量的使用者，您可以使用「大量新增」功能，或者，如果您的組織使用 Microsoft Azure Active Directory (Azure AD) ，您可以使用 Azure AD 群組。 本文將說明這兩個選項的程式。  觀賞這段影片或繼續閱讀，以深入瞭解大量新增功能。 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vxNq]

## <a name="use-bulk-add-to-assign-subscriptions"></a>使用大量新增來指派訂閱
1. 登入 Visual Studio 訂閱管理入口網站 <https://manage.visualstudio.com> 。

1. 若要一次加入多個訂閱者，請流覽至 [ **管理訂閱者** ] 索引標籤。選擇 [ **加入** ] 索引標籤，然後在下拉式清單中選擇 [ **大量新增** ]。  

1. 大量新增會使用 Microsoft Excel 範本來上傳訂閱者資訊。 在 [上傳多個訂閱者] 對話方塊中，選取 [ **下載** ] 以下載範本。
   > [!div class="mx-imgBorder"]
   > ![下載 Excel 範本，以上傳多位訂閱者](media/download-template-upload-subscribers.png "下載空白 Excel 範本以開始大量指派程式。")
   >
   > [!NOTE]
   > 請一律下載這個範本的最新版本。 如果您使用舊版本，則大量上傳可能會失敗。

1. 在 Excel 試算表中，請將您想要指派訂用帳戶之個人的資訊填入欄位中。  (*參考* 是選擇性欄位。在完成之後，) 將檔案儲存在本機。

    > [!NOTE]
    > 範本中的其中一個欄位可讓系統管理員啟用或停用訂閱者下載軟體的能力。  停用下載也會停用其產品金鑰的存取權。

   為了協助確保順利上傳，請觀察下列最佳做法：

    - 確定表單欄位未包含逗號。
    - 移除表單欄位前後的空格。
    - 請確定使用者名稱在兩段式名字或姓氏之間未包含額外的空格 (例如，如果某人的名字有兩個部分，如 "Maggie May"，應該鍵入為 "MaggieMay"，因為系統不會修剪額外的空格)。
    - 請確定所有必要的欄位都已完成。 
    - 檢查 **錯誤訊息** 資料行。  如果列出任何錯誤，請先解決這些錯誤，然後再嘗試上傳檔案。 

1. 回到 Visual Studio 訂閱管理入口網站。 在 [ **上傳多個訂閱者** ] 對話方塊中，選取 **[流覽]**。
   > [!div class="mx-imgBorder"]
   > ![瀏覽至先前儲存的範本，以上傳多位訂閱者](media/bulk-add-browse-saved-template.png "您可以流覽至檔案位置，或將它拖放到此對話方塊中。")

1. 流覽至您儲存的 Excel 檔案，然後選取 **[確定]**。
   > [!div class="mx-imgBorder"]
   > ![上傳 Excel 範本，以上傳多位訂閱者](media/bulk-upload-subscribers.png "包含您資料的範本會出現在這裡。 選取 [確定] 以開始上傳。")

    上傳進度對話方塊隨即出現。

    如果範本包含錯誤，則上傳會失敗，而且您會看到錯誤，因此您可以修正範本，並嘗試重新大量上傳。
   > [!div class="mx-imgBorder"]
   > ![當上傳多位訂閱者失敗時顯示錯誤訊息](_img/assign-license-bulk/bulk-add-upload-failure.png "如果您上傳的檔案包含錯誤，則會出現此訊息。 請解決錯誤，然後再次執行大量新增程式。")

   如果您遇到失敗，請遵循下列步驟：
   1. 開啟您所建立的 Excel 檔案，更正問題，然後儲存檔案。
   0. 返回系統管理入口網站並關閉錯誤訊息。
   0. 選擇 [新增]  。
   0. 選取 [ **大量新增**]。
   0. 因為您已經儲存 Excel 檔案，所以不需要下載範本。  選取 **[流覽]**，找出您剛剛儲存的檔案，然後選取 [ **開啟**]。
   0. 選取 [確定]。


    上傳成功時，您會看到訂閱者清單和確認訊息。
   > [!div class="mx-imgBorder"]
   > ![當上傳多位訂閱者成功時顯示確認訊息](_img/assign-license-bulk/bulk-add-upload-success.png "當您的上傳成功完成時，您會收到確認訊息。")

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>使用 Azure Active Directory 群組指派訂用帳戶 
使用這項功能可讓您輕鬆地在訂用帳戶指派上保持最上層。 您可以在訂用帳戶管理入口網站中新增 Azure Active Directory 安全性群組，以確保群組中的所有人員都已獲指派訂用帳戶。 為了方便使用，當個人離開您的組織並從 Azure Active Directory 中移除時，也會移除其訂用帳戶的存取權。 


> [!IMPORTANT]
>
> 下列限制適用于使用 Azure AD 群組來新增訂閱者：
> - 初次將群組新增至系統管理員入口網站時，系統管理員必須是 AAD 租使用者的成員。  新增群組之後，對群組成員資格所做的變更不需要系統管理員介入。 
> - 群組至少必須包含一個成員。  不支援空白群組。
> - 群組的使用者必須少於1000個。 
> - 所有使用者都必須在群組的最上層。  「不支援」巢狀群組。
> - 僅支援信任的協定。  (只能信任可 ' overallocate ' 訂用帳戶的協定。 ) 
> - 群組的所有成員都必須有與其 Azure AD 帳戶相關聯的電子郵件地址。
> - 使用 Azure AD 群組新增的訂閱不支援通知的個別電子郵件地址。  

觀賞這段影片或繼續閱讀，以深入瞭解如何使用 Azure Active Directory 群組功能新增訂閱者。 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

1. 登入 Visual Studio 訂閱系統管理入口網站 [https://manage.visualstudio.com](https://manage.visualstudio.com) 。

2. 若要一次加入多個訂閱者，請流覽至 [ **管理訂閱者** ] 索引標籤。

3. 選擇 [ **加入** ] 索引標籤，然後在下拉式清單中選取 **Azure Active Directory 群組** ]。  

   > [!div class="mx-imgBorder"]
   > ![選擇使用 Azure AD 的大量新增](_img/assign-license-bulk/bulk-add-aad.png "選擇 [使用 Azure AD 的大量新增] 功能，從您的 Azure Active Directory 群組提取訂閱者。")

4. 開始輸入您想要新增至表單欄位的 Azure AD 組名。 這會搜尋您組織內的可用 Azure AD 群組。 

5. 當您選取群組時，欄位會自動填入組名。 在新增群組之前，您將可以選擇先查看該群組中的使用者。 接下來，您可以選擇訂用帳戶層級、下載許可權，以及群組的通訊喜好設定。 您可以視需要將詳細資料新增至參考欄位。 

   > [!div class="mx-imgBorder"]
   > ![選擇您的 Azure AD 群組](_img/assign-license-bulk/bulk-add-aad-details.png "選擇您的 Azure AD 組名，以從該群組新增訂閱者。")

6. 選取 [ **新增** ]，然後 **確認**。 

7. 若要查看已新增的群組，請滾動至使用者清單的底部。  

8. 選取 [ **View 訂閱者** ] 以顯示群組的成員。 您可以查看群組中訂閱者的詳細資料，但無法對訂閱者或指派的訂閱進行任何編輯。    

> [!NOTE]
> 如果您已將訂用帳戶個別指派給後續新增成為 Azure AD 群組一部分的使用者，這些訂用帳戶將會新增為群組的一部分，且不會再個別列出。 不過，如果個別訂用帳戶是針對不同的訂用帳戶層級，則會有兩個訂用帳戶。  範例：如果使用者有個別的 Visual Studio Professional 訂用帳戶，而且他們是您指派 Visual Studio Enterprise 訂用帳戶之群組的成員，他們將會有這兩個訂閱。  
>
> 如果您從已指派訂用帳戶的 Azure Active Directory 群組中移除訂閱者，則可能需要24小時的時間，更新才會反映在系統管理員入口網站中。 


## <a name="frequently-asked-questions"></a>常見問題集
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>問：我可以選擇要在 Azure AD 群組內指派多個訂用帳戶層級嗎？ 
答：否--群組中的每個人都會收到相同的訂用帳戶。 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>問：我可以編輯 Azure AD 群組中新增的個人訂閱者詳細資料嗎？  
答：否--若要修改個別訂閱者的資訊，您必須將其從 Azure AD 安全性群組中移除，並個別指派訂用帳戶給他們。  

### <a name="q-why-cant-i-see-the-option-to-use-azure-active-directory-groups-to-add-subscribers"></a>問：為什麼看不到使用 Azure Active Directory 群組來加入訂閱者的選項？
答：這項功能目前僅適用于具有信任協定的組織。  選取 [ **詳細資料** ] 按鈕，以顯示您的合約資訊。

   > [!div class="mx-imgBorder"]
   > ![按一下 [詳細資料] 按鈕](_img/assign-license-bulk/bulk-add-agreement.png "按一下 [詳細資料] 按鈕，以查看您擁有的合約類型")

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>問：我已將某人新增至我的 Azure AD 安全性群組，但我在訂用帳戶管理入口網站中看不到他們新增的帳戶，且他們沒有訂用帳戶。 為什麼不用？  
答：根據組織設定 Azure AD 的方式，您可能會在新增使用者之前看到最多24小時的延遲。 如果超過24小時，請造訪 [Visual Studio 管理和訂閱支援](https://my.visualstudio.com/gethelp)。  

## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](/visualstudio/)
- [Azure DevOps 文件](/azure/devops/) \(英文\)
- [Azure 檔](/azure/)
- [Microsoft 365 檔](/microsoft-365/)

## <a name="next-steps"></a>下一步
- 只有一或兩個訂閱者要新增嗎？  參閱[新增單一使用者](assign-license.md)
- 需要協助嗎？ 請聯絡 [Visual Studio 管理和訂閱支援](https://visualstudio.microsoft.com/support/support-overview-vs)。