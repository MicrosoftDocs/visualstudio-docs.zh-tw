---
title: 指派 Visual Studio 訂用帳戶的授權 | Microsoft Docs
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 07/16/2018
ms.topic: conceptual
description: 了解系統管理員如何指派訂閱者授權
ms.openlocfilehash: 6e9eb19ce4f9947f730bcd32be5ddcc931770bde
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783545"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>在 Visual Studio 訂用帳戶系統管理員入口網站中指派授權

身為 Visual Studio 訂用帳戶系統管理員，您可以使用系統管理員入口網站，將訂用帳戶指派給個別使用者和使用者群組。

若為使用者群組，您可以一次指派一個訂用帳戶給他們，或者使用 [大量新增]  功能，快速輕鬆地上傳訂閱者清單與其訂用帳戶資訊。

## <a name="individual-assignments"></a>個人工作分派

以下說明如何將 Visual Studio 訂用帳戶授權指派給新使用者，使其可以存取訂用帳戶權益。

1. 登入[系統管理員入口網站](https://manage.visualstudio.com)。

2. 若要將授權指派給單一 Visual Studio 訂閱者，請選取資料表頂端的 [新增]  。
   > [!div class="mx-imgBorder"]
   > ![新增一位訂閱者](media/add-single-subscriber.png)

3. 將資訊輸入至新訂閱者的表單欄位。 如果您的組織使用 Azure Active Directory，此欄位會作為搜尋功能來尋找您目前目錄中的人員，如此您就可以從搜尋結果中選取正確的使用者。 選取該人員之後，會自動填入其名稱、登入電子郵件和通知電子郵件。
   > [!div class="mx-imgBorder"]
   > ![新增通知電子郵件地址](media/add-new-subscriber-notification-email.png)

    如果您想要讓此訂閱者在登入 [Visual Studio 訂用帳戶入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs)時可存取軟體下載，請務必保持 [下載設定]  區段的 [下載] 切換按鈕為啟用狀態。 如果您選擇停用下載，則使用者無法存取軟體下載，但仍可存取訂用帳戶中所含的所有其他權益。
   > [!div class="mx-imgBorder"]
   > ![存取下載項目](media/access-to-downloads.png)

    如果您想要變更訂閱者接收資訊的語言，您可在 [通訊喜好設定]  區段中執行此作業。
   > [!div class="mx-imgBorder"]
   > ![變更傳送通知電子郵件時所要使用的語言](media/change-subscriber-communication-preference.png)

    如果您想要將自己的參考資訊新增至訂用帳戶，您可在 [新增參考]  區段中執行此作業。
   > [!div class="mx-imgBorder"]
   > ![在每個訂閱中新增您自己的參考資訊](media/add-subscriber-reference-notes.png)

    當您完成選取選項，並輸入訂閱者資料時，請選擇 [新增訂閱者]  飛出視窗底部的 [新增]  。
   > [!div class="mx-imgBorder"]
   > ![選擇 [新增] 按鈕](media/add-button.png)

4. 在您新增訂閱者之後，會將具有進一步指示的指派電子郵件自動傳送給新訂閱者。 您可以選取訂閱者並按一下上方功能表中的 [重新傳送]  按鈕，隨時重新傳送指派電子郵件。
   > [!div class="mx-imgBorder"]
   > ![隨時重新傳送啟用電子郵件給任何使用者或多位使用者](media/resend-subscriber-activation-emails.png)

## <a name="bulk-assignments"></a>大量指派

1. 若要一次新增多位訂閱者，請巡覽至 [管理訂閱者]  索引標籤。在上方功能區中，按一下 [大量新增]  。
   > [!div class="mx-imgBorder"]
   > ![新增多位訂閱者](media/add-multiple-subscribers.png)

2. 大量指派會使用 Microsoft Excel 範本來上傳訂閱者。 在 [Upload Multiple Subscribers] (上傳多位訂閱者)　對話方塊中，按一下 [下載]  來下載範本。
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
