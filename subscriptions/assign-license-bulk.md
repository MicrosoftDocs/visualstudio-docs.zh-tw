---
title: 指派 Visual Studio 訂用帳戶使用者群組的授權 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 03/02/2020
ms.topic: conceptual
description: 瞭解管理員如何使用批次新增功能或 Microsoft Azure 活動目錄群組向多個訂閱者分配授權
ms.openlocfilehash: eb641d86733ef794f1d53ae6eee45e0bdf4fde18
ms.sourcegitcommit: deab74e8f41b30b28c041b048d67b3fff2cceab9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80994444"
---
# <a name="assign-subscriptions-to-multiple-users"></a>指派訂閱給多個使用者
訂用帳戶系統管理入口網站可讓您以一次一個或以大型群組方式新增使用者。  若要新增個別使用者，請參閱[新增單一使用者](assign-license.md)。

要添加大型使用者組,可以使用批量添加功能,或者您的組織正在使用 Microsoft Azure 活動目錄 (Azure AD),則可以使用 Azure AD 組。 本文將解釋這兩個選項的過程。 

## <a name="use-bulk-add-to-assign-subscriptions"></a>使用批次新增分配訂閱
1. 登錄中的https://manage.visualstudio.com可視化工作室訂閱管理門戶。

2. 要新增多個訂閱者,請瀏覽到 **'管理訂閱者'** 選項卡。選擇「**新增**」選項卡,然後在下拉清單中選擇 **「 批次」** 加入 。  

2. 大量添加使用Microsoft Excel範本上傳訂閱者資訊。 在 [Upload Multiple Subscribers] (上傳多位訂閱者)　對話方塊中，按一下 [下載]**** 來下載範本。
   > [!div class="mx-imgBorder"]
   > ![下載 Excel 範本，以上傳多位訂閱者](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > 請一律下載這個範本的最新版本。 如果您使用舊版本，則大量上傳可能會失敗。

3. 在 Excel 試算表中，請將您想要指派訂用帳戶之個人的資訊填入欄位中。 (*引用*是可選欄位。完成後,將檔保存在本地。

   為了協助確保順利上傳，請觀察下列最佳做法：

    - 確定表單欄位未包含逗號。
    - 移除表單欄位前後的空格。
    - 請確定使用者名稱在兩段式名字或姓氏之間未包含額外的空格 (例如，如果某人的名字有兩個部分，如 "Maggie May"，應該鍵入為 "MaggieMay"，因為系統不會修剪額外的空格)。
    - 確保所有必需的欄位都已完成。 
    - 檢查**錯誤訊息**列。  如果列出了任何錯誤,請先在嘗試上載檔之前解決這些錯誤。 

4. 回到 Visual Studio 訂閱管理入口網站。 在 [上傳多位訂閱者]**** 對話方塊中，按一下 [瀏覽]****。
   > [!div class="mx-imgBorder"]
   > ![瀏覽至先前儲存的範本，以上傳多位訂閱者](media/bulk-add-browse-saved-template.png)

5. 巡覽至您儲存的 Excel 檔案，然後按一下 [確定]****。
   > [!div class="mx-imgBorder"]
   > ![上傳 Excel 範本，以上傳多位訂閱者](media/bulk-upload-subscribers.png)

    上傳進度對話方塊隨即出現。

    如果範本包含錯誤，則上傳會失敗，而且您會看到錯誤，因此您可以修正範本，並嘗試重新大量上傳。
   > [!div class="mx-imgBorder"]
   > ![當上傳多位訂閱者失敗時顯示錯誤訊息](_img/assign-license-bulk/bulk-add-upload-failure.png)

   如果遇到故障,請執行以下步驟:
   1. 開啟您創建的 Excel 檔,更正問題並儲存該檔。
   0. 返回到管理門戶並選擇 **「添加**」。
   0. 選擇**批次新增**。
   0. 由於已保存 Excel 檔,因此無需下載範本。  按下 **「瀏覽**」,找到您剛剛儲存的文件,然後按下「**打開**」。
   0. 按一下 [確定]  。


    上傳成功時，您會看到訂閱者清單和確認訊息。
   > [!div class="mx-imgBorder"]
   > ![當上傳多位訂閱者成功時顯示確認訊息](_img/assign-license-bulk/bulk-add-upload-success.png)

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>使用 Azure 的目錄群組分配訂閱 
使用此功能可以輕鬆保持訂閱分配的頂部。 您可以在訂閱管理門戶中添加 Azure 活動目錄安全組,這將確保為組中的所有個人分配訂閱。 為了簡化操作,當個人離開組織並從 Azure 活動目錄中刪除時,他們對訂閱的訪問也會被刪除。 


> [!IMPORTANT]
>
> 以下限制適用於使用 Azure AD 群組新增訂閱者:
> - 組必須至少包含一個成員。  不支援空組。
> - 組必須少於 1,000 個使用者 
> - 所有用戶必須位於組的頂部。  不支援嵌狀群組
> - 只支援信任的協定
> - 群組的所有成員必須具有與其 Azure AD 帳號關聯的電子郵件地址
> - 對於使用 Azure AD 組添加的訂閱,不支援通知的單獨電子郵寄地址。  

1. 登錄到[https://manage.visualstudio.com](https://manage.visualstudio.com)中的可視化工作室訂閱管理門戶。

2. 要一次添加多個訂閱者,導航到 **「管理訂閱者」** 選項卡。

3. 選擇「**新增**」選項卡,然後在下拉清單中選擇**Azure 的目錄群組**。  

   > [!div class="mx-imgBorder"]
   > ![使用 Azure AD 選擇批次新增](_img/assign-license-bulk/bulk-add-aad.png)

4. 開始輸入要添加到表單欄位中的 Azure AD 組的名稱。 這將搜索組織內的可用 Azure AD 組。 

5. 選擇群組時,該欄位將自動使用組名稱填充。 您可以選擇在添加該組中的使用者。 接下來,您可以選擇組的訂閱級別、下載許可權和通信首選項。 如果需要,可以將詳細資訊添加到參考欄位中。 

   > [!div class="mx-imgBorder"]
   > ![使用 Azure AD 選擇批次新增](_img/assign-license-bulk/bulk-add-aad-details.png)

6. 按下 **"添加**",然後按下 **「確認**」。。 

7. 要查看添加的組,請滾動到使用者清單的底部。  

8. 選擇 **「查看訂閱者**」 以顯示組的成員。 您可以查看有關組中訂閱者的詳細資訊,但不能對訂閱者或分配的訂閱進行任何編輯。    

> [!NOTE]
> 如果已單獨為隨後添加為 Azure AD 組的一部分的使用者分配了訂閱,則這些訂閱將作為組的一部分添加,並且將不再單獨列出。 但是,如果單個訂閱針對不同的訂閱級別,則它們將有兩個訂閱。  範例:如果使用者具有單獨的 Visual Studio 專業訂閱,並且他們是您為其分配 Visual Studio 企業版訂閱的組的成員,則他們將同時擁有這兩個訂閱。  


> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

## <a name="frequently-asked-questions"></a>常見問題集
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>問:是否可以選擇要在 Azure AD 組中分配的多個訂閱等級? 
答:否 - 組中的每個人都收到相同的訂閱。 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>問:是否可以編輯在 Azure AD 群組中添加的個人的使用者詳細資訊?  
答:否 -- 要修改單個訂閱者的資訊,您需要從 Azure AD 安全組中刪除它們並單獨為其分配訂閱。  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>問:我向 Azure AD 安全組添加了某人,但看不到他們在訂閱管理門戶中添加,並且他們沒有訂閱。 為什麼看不到呢？  
答:根據組織配置 Azure AD 的方式,在添加使用者之前,可能會看到長達 24 小時的延遲。 如果時間超過 24 小時,[請聯絡支援](https://visualstudio.microsoft.com/support/support-overview-vs)人員。  

## <a name="see-also"></a>另請參閱
- [視覺化工作室文件](https://docs.microsoft.com/visualstudio/)
- [Azure 開發人員文件](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [微軟 365 文件](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>後續步驟
- 只有一或兩個訂閱者要新增嗎？  參閱[新增單一使用者](assign-license.md)
- 需要協助嗎？ 聯絡[視覺化工作室管理與訂閱支援](https://visualstudio.microsoft.com/support/support-overview-vs)。
