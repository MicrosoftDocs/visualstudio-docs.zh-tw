---
title: 在系統管理入口網站編輯訂用帳戶 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97ac8e4d-7a03-42f8-98cb-15bcaa90ef65
ms.date: 03/03/2020
ms.topic: conceptual
description: 了解系統管理員如何編輯訂用帳戶指派。
ms.openlocfilehash: a0f72bf6a6561060fd4eddcf2fc11f0f4cf97f15
ms.sourcegitcommit: 1b7412f1a5b039b2b294c6001013f399ea7aa5bc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82564221"
---
# <a name="edit-visual-studio-subscription-assignments"></a>編輯 Visual Studio 訂用帳戶指派
身為訂用帳戶管理員，您可以變更指派給您組織內個人的訂用帳戶。  本文章討論您可以進行的變更類型，並提供必要的步驟。

   > [!NOTE]
   > 如果您需要變更透過 Azure Active Directory 群組指派之訂閱者的訂用帳戶詳細資料，您必須將其從群組中移除，並個別將其新增至系統管理入口網站。  

## <a name="change-subscriber-information"></a>變更訂閱者資訊
您可以編輯訂閱者資訊，以更正錯誤或更新資訊。

若要編輯訂閱者，請選取滑鼠停留在訂閱者電子郵件地址上時，旁邊出現的省略符號 (…)。 隨即顯示下拉式清單。  選取 [**編輯**] 以修改訂閱者的詳細資料。 
> [!div class="mx-imgBorder"]
> ![選取要編輯的訂閱者](_img/edit-license/select-subscriber.png)

您可以更新訂閱者的名字、姓氏、訂閱等級、電子郵件地址、國家/地區、語言、下載和參考欄位。 編輯訂閱者的資訊，然後按一下 [**儲存**]。

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>使用大量編輯來編輯多名訂閱者


您可以使用大量編輯程序一次編輯多名訂閱者。 這項功能主要用於公司電子郵件地址變更過的組織，或已決定限制下載存取的組織。

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vkAF]

   > [!IMPORTANT]
   > 訂用帳戶層級（即 Enterprise、Professional 等等）和訂用帳戶 Guid 無法使用大量編輯加以更改。  如果您需要為使用者指派特定的訂用帳戶 Guid，請選擇訂用帳戶識別碼，以使用新增使用者的程式。 如果您嘗試上傳，並在大量編輯範本中變更這些專案，上傳將會失敗。

1. 若要一次編輯多個訂閱者，請流覽至 [訂閱者] 索引標籤。在頂端的功能區中，按一下 [**大量編輯**]。

2. 大量編輯使用 Excel 範本編輯訂閱者資訊。 在 [大量編輯] 方塊中，按一下 [Export this Excel (匯出此 Excel)]**** 下載目前的訂閱者清單，包括其所有資訊。
   > [!div class="mx-imgBorder"]
   > ![編輯授權 - 匯出大量編輯清單](_img/edit-license/edit-license-bulk-edit-export.png)

3. 接下來，將檔案儲存在本機，以便輕鬆找到它，進行任何必要變更後再上傳。 若要確保成功上傳，請勿編輯 [大量編輯] 檔案中**的訂用帳戶層級或訂**用帳戶 GUID，因為這樣會導致上傳失敗。

4. 返回 Visual Studio 訂用帳戶管理入口網站的 [大量編輯] 對話方塊中，按一下 [瀏覽]****。 選取您儲存的 Excel 檔案，然後按一下 [確定]****。 您會在螢幕上看到上傳進度。
   > [!div class="mx-imgBorder"]
   > ![編輯授權 - 大量編輯檔案上傳](_img/edit-license/edit-license-bulk-file-upload1.png)

5. 上傳檔案後，您會看到通知，讓您知道作業已順利完成。 此時，您的編輯會反映在訂閱者資訊中。

## <a name="see-also"></a>請參閱
- [Visual Studio 檔](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [Microsoft 365 檔](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>後續步驟
- 需要指派特定的訂用帳戶識別碼嗎？ 請參閱指派訂用帳戶識別碼。 
- 如需協助以尋找特定的訂閱，請參閱[搜尋訂閱](search-license.md)。
- 需要建立您所有訂閱項目的清單嗎？  參閱[匯出訂用帳戶](exporting-subscriptions.md)。


