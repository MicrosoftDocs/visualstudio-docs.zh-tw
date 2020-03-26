---
title: 在系統管理入口網站編輯訂用帳戶 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97ac8e4d-7a03-42f8-98cb-15bcaa90ef65
ms.date: 03/03/2020
ms.topic: conceptual
description: 了解系統管理員如何編輯訂用帳戶指派。
ms.openlocfilehash: d145d556467b4eecec787fe409b4faa45945bec0
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232547"
---
# <a name="edit-visual-studio-subscription-assignments"></a>編輯 Visual Studio 訂用帳戶指派
身為訂用帳戶管理員，您可以變更指派給您組織內個人的訂用帳戶。  本文章討論您可以進行的變更類型，並提供必要的步驟。

   > [!NOTE]
   > 如果需要更改通過 Azure 活動目錄組分配的訂閱者的訂閱詳細資訊，則需要從群組移除這些訂閱詳細資訊，並單獨將其添加到監管中心中。  

## <a name="change-subscriber-information"></a>變更訂閱者資訊
您可以編輯訂閱者資訊，以更正錯誤或更新資訊。

若要編輯訂閱者，請選取滑鼠停留在訂閱者電子郵件地址上時，旁邊出現的省略符號 (…)。 隨即顯示下拉式清單。  選擇 **"編輯"** 以修改訂閱者的詳細資訊。 
> [!div class="mx-imgBorder"]
> ![選取要編輯的訂閱者](_img/edit-license/select-subscriber.png)

您可以更新訂閱者的名字、姓氏、訂閱級別、電子郵件地址、國家/地區、語言、下載和引用欄位。 編輯訂閱者的資訊，然後按一下 **"保存**"。

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>使用大量編輯來編輯多名訂閱者
您可以使用大量編輯程序一次編輯多名訂閱者。 這項功能主要用於公司電子郵件地址變更過的組織，或已決定限制下載存取的組織。

   > [!IMPORTANT]
   > 訂閱級別（即企業、專業人員等）和訂閱 GUID 無法使用大量編輯進行更改。  如果需要向使用者分配特定的訂閱 GUID，請使用該過程通過選擇訂閱 ID 來添加使用者。 如果嘗試上載，在大量編輯範本中更改了這些專案，則上載將失敗。

1. 要同時編輯多個訂閱者，請導航到"訂閱伺服器"選項卡。在頂部的功能區中，按一下 **"大量編輯**"。

2. 大量編輯使用 Excel 範本編輯訂閱者資訊。 在 [大量編輯] 方塊中，按一下 [Export this Excel (匯出此 Excel)]**** 下載目前的訂閱者清單，包括其所有資訊。
   > [!div class="mx-imgBorder"]
   > ![編輯授權 - 匯出大量編輯清單](_img/edit-license/edit-license-bulk-edit-export.png)

3. 接下來，將檔案儲存在本機，以便輕鬆找到它，進行任何必要變更後再上傳。 為確保成功上載，請不要在大量編輯檔中**編輯訂閱級別或訂閱 GUID，** 否則將導致上載失敗。

4. 返回 Visual Studio 訂用帳戶管理入口網站的 [大量編輯] 對話方塊中，按一下 [瀏覽]****。 選取您儲存的 Excel 檔案，然後按一下 [確定]****。 您會在螢幕上看到上傳進度。
   > [!div class="mx-imgBorder"]
   > ![編輯授權 - 大量編輯檔案上傳](_img/edit-license/edit-license-bulk-file-upload1.png)

5. 上傳檔案後，您會看到通知，讓您知道作業已順利完成。 此時，您的編輯會反映在訂閱者資訊中。

## <a name="see-also"></a>另請參閱
- [視覺化工作室文檔](https://docs.microsoft.com/visualstudio/)
- [Azure 開發人員文檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [微軟 365 文檔](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>後續步驟
- 需要分配特定的訂閱 ID？ 查看分配訂閱 ID。 
- 如需協助以尋找特定的訂閱，請參閱[搜尋訂閱](search-license.md)。
- 需要建立您所有訂閱項目的清單嗎？  參閱[匯出訂用帳戶](exporting-subscriptions.md)。


