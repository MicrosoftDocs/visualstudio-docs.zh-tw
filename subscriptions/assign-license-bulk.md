---
title: 指派 Visual Studio 訂用帳戶使用者群組的授權 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: 了解系統管理員如何指派多個訂閱者授權
ms.openlocfilehash: 7d54dcf3cf3e7fea7845a4e9a0053de4ba734ae9
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2019
ms.locfileid: "68610518"
---
# <a name="assign-subscriptions-to-multiple-users"></a>指派訂閱給多個使用者
訂用帳戶系統管理入口網站可讓您以一次一個或以大型群組方式新增使用者。  若要新增個別使用者，請參閱[新增單一使用者](assign-license.md)。

## <a name="use-bulk-add-to-assign-subscriptions"></a>使用大量新增方式指派訂用帳戶
1. 登入 Visual Studio 訂閱系統管理入口網站 (https://manage.visualstudio.com )。
2. 若要一次新增多位訂閱者，請巡覽至 [管理訂閱者]  索引標籤。在上方功能區中，按一下 [大量新增]  。
   > [!div class="mx-imgBorder"]
   > ![新增多位訂閱者](media/add-multiple-subscribers.png)

2. 大量新增方式會使用 Microsoft Excel 範本來上傳訂閱者資訊。 在 [Upload Multiple Subscribers] (上傳多位訂閱者)　對話方塊中，按一下 [下載]  來下載範本。
   > [!div class="mx-imgBorder"]
   > ![下載 Excel 範本，以上傳多位訂閱者](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > 請一律下載這個範本的最新版本。 如果您使用舊版本，則大量上傳可能會失敗。

3. 在 Excel 試算表中，請將您想要指派訂用帳戶之個人的資訊填入欄位中。 ([參考]  是選擇性欄位。)完成之後，請將檔案儲存在本機。

   為了協助確保順利上傳，請觀察下列最佳做法：

    - 確定表單欄位未包含逗號。
    - 移除表單欄位前後的空格。
    - 請確定使用者名稱在兩段式名字或姓氏之間未包含額外的空格 (例如，如果某人的名字有兩個部分，如 "Maggie May"，應該鍵入為 "MaggieMay"，因為系統不會修剪額外的空格)。

4. 回到 Visual Studio 訂閱管理入口網站。 在 [上傳多位訂閱者]  對話方塊中，按一下 [瀏覽]  。
   > [!div class="mx-imgBorder"]
   > ![瀏覽至先前儲存的範本，以上傳多位訂閱者](media/bulk-add-browse-saved-template.png)

5. 巡覽至您儲存的 Excel 檔案，然後按一下 [確定]  。
   > [!div class="mx-imgBorder"]
   > ![上傳 Excel 範本，以上傳多位訂閱者](media/bulk-upload-subscribers.png)

    上傳進度對話方塊隨即出現。

    如果範本包含錯誤，則上傳會失敗，而且您會看到錯誤，因此您可以修正範本，並嘗試重新大量上傳。
   > [!div class="mx-imgBorder"]
   > ![當上傳多位訂閱者失敗時顯示錯誤訊息](media/bulk-add-template-failed.png)

    上傳成功時，您會看到訂閱者清單和確認訊息。
   > [!div class="mx-imgBorder"]
   > ![當上傳多位訂閱者成功時顯示確認訊息](media/bulk-add-template-success.png)

## <a name="next-steps"></a>後續步驟
- 只有一或兩個訂閱者要新增嗎？  參閱[新增單一使用者](assign-license.md)
- 了解如何[編輯](edit-license.md)現有的訂用帳戶
- 需要協助嗎？ 請聯絡 [Visual Studio 管理與訂閱支援](https://visualstudio.microsoft.com/support/support-overview-vs)。
