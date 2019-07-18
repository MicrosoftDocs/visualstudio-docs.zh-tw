---
title: 在管理入口網站編輯訂用帳戶 | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: conceptual
description: 了解系統管理員如何編輯訂用帳戶指派。
ms.openlocfilehash: 7245facbaf966593160bc44dc15bc2fd71622347
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783481"
---
# <a name="editing-visual-studio-subscription-assignments"></a>編輯 Visual Studio 訂用帳戶指派

身為訂用帳戶管理員，您可以變更指派給您組織內個人的訂用帳戶。  本文章討論您可以進行的變更類型，並提供必要的步驟。

## <a name="making-changes-to-subscriber-information"></a>變更訂閱者資訊
您可以編輯訂閱者資訊，以更正錯誤或更新資訊。

若要編輯訂閱者，請選取滑鼠停留在訂閱者電子郵件地址上時，旁邊出現的省略符號 (…)。 隨即顯示下拉式清單。  選取 [編輯]  修改訂閱者的詳細資料。 您也可以按兩下格線中的訂閱者資料列，開啟 [編輯] 視窗。
> [!div class="mx-imgBorder"]
> ![選取要編輯的訂閱者](_img/edit-license/select-subscriber.png)

您可以更新訂閱者的名字、姓氏、國家/地區、語言和下載項目。 編輯訂閱者的資訊，然後按一下 [儲存]  。

   > [!NOTE]
   > 如果需要變更訂閱者的訂用帳戶層級，您必須從入口網站刪除使用者，然後再次新增他們。 訂用帳戶層級不可編輯。

## <a name="editing-multiple-subscribers-using-bulk-edit"></a>使用大量編輯來編輯多名訂閱者

您可以使用大量編輯程序一次編輯多名訂閱者。 這項功能主要用於公司電子郵件地址變更過的組織，或已決定限制下載存取的組織。

   > [!IMPORTANT]
   > 訂用帳戶層級 (即 Enterprise、Professional 等等) 和訂用帳戶 GUID 皆無法變更。  如果嘗試上傳這些變更的項目，上傳作業會失敗。

1. 若要一次編輯多名訂閱者，請巡覽 [訂閱者] 索引標籤。在上方功能區中，按一下 [大量編輯]  。

2. 大量編輯使用 Excel 範本編輯訂閱者資訊。 在 [大量編輯] 方塊中，按一下 [Export this Excel (匯出此 Excel)]  下載目前的訂閱者清單，包括其所有資訊。
   > [!div class="mx-imgBorder"]
   > ![編輯授權 - 匯出大量編輯清單](_img/edit-license/edit-license-bulk-edit-export.png)

3. 接下來，將檔案儲存在本機，以便輕鬆找到它，進行任何必要變更後再上傳。 為確保成功上傳，**不要編輯訂用帳戶層級或訂用帳戶 GUID**，因為這樣會造成上傳失敗。

4. 返回 Visual Studio 訂用帳戶管理入口網站的 [大量編輯] 對話方塊中，按一下 [瀏覽]  。 選取您儲存的 Excel 檔案，然後按一下 [確定]  。 您會在螢幕上看到上傳進度。
   > [!div class="mx-imgBorder"]
   > ![編輯授權 - 大量編輯檔案上傳](_img/edit-license/edit-license-bulk-file-upload1.png)

5. 上傳檔案後，您會看到通知，讓您知道作業已順利完成。 此時，您的編輯會反映在訂閱者資訊中。
