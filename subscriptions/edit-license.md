---
title: 在系統管理入口網站中編輯 Visual Studio 訂用帳戶 |Microsoft 檔
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 97ac8e4d-7a03-42f8-98cb-15bcaa90ef65
ms.date: 02/18/2021
ms.topic: how-to
description: 瞭解系統管理員如何編輯訂用帳戶指派。
ms.openlocfilehash: f24c949224d895f4cc2926ab30db637835e7886c
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249791"
---
# <a name="edit-visual-studio-subscription-assignments"></a>編輯 Visual Studio 訂用帳戶指派
訂用帳戶管理員可讓您變更指派給組織內個人的訂用帳戶。  本文章討論您可以進行的變更類型，並提供必要的步驟。

   > [!NOTE]
   > 如果您需要變更透過 Azure Active Directory 群組指派之訂閱者的訂用帳戶詳細資料，您必須將其從群組中移除，並個別將其新增至系統管理入口網站。  

## <a name="change-subscriber-information"></a>變更訂閱者資訊
您可以編輯訂閱者資訊，以更正錯誤或更新資訊。

若要編輯訂閱者，請選取滑鼠停留在訂閱者電子郵件地址上時，旁邊出現的省略符號 (…)。 隨即顯示下拉式清單。  選取 [ **編輯** ] 以修改訂閱者的詳細資料。 
> [!div class="mx-imgBorder"]
> ![選取要編輯的訂閱者](_img/edit-license/select-subscriber.png "按一下省略號，然後選擇 [編輯]。")

您可以更新訂閱者的名字、姓氏、訂用帳戶層級、電子郵件地址、國家/地區、語言、下載和參考欄位。 編輯訂閱者的資訊，然後按一下 [ **儲存**]。

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>使用大量編輯來編輯多名訂閱者

您可以使用大量編輯程序一次編輯多名訂閱者。 這項功能主要用於公司電子郵件地址變更過的組織，或已決定限制下載存取的組織。

觀賞這段影片或繼續閱讀，以瞭解如何使用大量編輯來編輯多個訂閱者。 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vkAF]

> [!NOTE]
> 請勿變更範本中的訂用帳戶 Guid。 請參閱我們的文章，以瞭解如何 [指派特定的訂](assign-guid.md)用帳戶 guid。

1. 若要一次編輯多個訂閱者，請流覽至 [訂閱者] 索引標籤。在頂端的功能區中，按一下 [ **大量編輯**]。

2. 大量編輯使用 Excel 範本編輯訂閱者資訊。 在 [大量編輯] 方塊中，按一下 [Export this Excel (匯出此 Excel)] 下載目前的訂閱者清單，包括其所有資訊。
   > [!div class="mx-imgBorder"]
   > ![編輯授權 - 匯出大量編輯清單](_img/edit-license/edit-license-bulk-edit-export.png "按一下 [匯出此 excel]，即可建立目前訂用帳戶的清單。")

3. 接下來，將檔案儲存在本機，以便輕鬆找到它，進行任何必要變更後再上傳。 

4. 返回 Visual Studio 訂用帳戶管理入口網站的 [大量編輯] 對話方塊中，按一下 [瀏覽]。 選取您儲存的 Excel 檔案，然後按一下 [確定]。 您會在螢幕上看到上傳進度。
   > [!div class="mx-imgBorder"]
   > ![編輯授權 - 大量編輯檔案上傳](_img/edit-license/edit-license-bulk-file-upload1.png "流覽至已完成的 Excel 檔案的位置，選取該檔案，然後按一下 [確定]。")

5. 上傳檔案後，您會看到通知，讓您知道作業已順利完成。 此時，您的編輯會反映在訂閱者資訊中。

## <a name="resources"></a>資源
- [訂閱支援](https://visualstudio.microsoft.com/subscriptions/support/)

## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](/visualstudio/)
- [Azure DevOps 文件](/azure/devops/) \(英文\)
- [Azure 檔](/azure/)
- [Microsoft 365 檔](/microsoft-365/)

## <a name="next-steps"></a>下一步
- 需要指派特定的訂用帳戶識別碼嗎？ 簽出指派訂用帳戶識別碼。 
- 如需協助以尋找特定的訂閱，請參閱[搜尋訂閱](search-license.md)。
- 需要建立您所有訂閱項目的清單嗎？  參閱[匯出訂用帳戶](exporting-subscriptions.md)。