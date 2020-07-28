---
title: 指派 Visual Studio 訂閱的授權 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 03/02/2020
ms.topic: conceptual
description: 了解系統管理員如何指派訂閱者授權
ms.openlocfilehash: e8eba6ad97d0f5e7e1da0e75093c33658f26a56a
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87235013"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>在 Visual Studio 訂閱系統管理入口網站中指派授權
身為 Visual Studio 訂閱系統管理員，您可以使用系統管理入口網站，將訂閱指派給個別使用者和使用者群組。

對於使用者群組，您可以選擇如何指派訂閱。  
- 您可以一次指派一個訂用帳戶。
- 您也可以使用[大量新增](assign-license-bulk.md)功能，快速且輕鬆地上傳訂閱者清單及其訂用帳戶資訊。
- 如果您的組織使用 Microsoft Azure Active Directory （Azure AD），您可以[使用 Azure AD 群組來指派](https://docs.microsoft.com/visualstudio/subscriptions/assign-license-bulk#use-azure-active-directory-groups-to-assign-subscriptions)使用者群組的訂閱。  


## <a name="add-a-single-subscriber"></a>新增一位訂閱者
以下說明如何將 Visual Studio 訂用帳戶指派給新的使用者，讓他們可以存取訂閱權益。

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. 登入系統[管理入口網站](https://manage.visualstudio.com)。
2. 若要將授權指派給單一 Visual Studio 訂閱者，請在資料表的頂端選取 [**新增**]，然後選擇 [**個別訂閱者**]。
   > [!div class="mx-imgBorder"]
   > ![新增一位訂閱者](_img/assign-license-add/add-subscriber-individual.png "按一下 [新增]，然後選擇 [個別訂閱者] 來指派單一訂用帳戶。")
3. 將資訊輸入至新訂閱者的表單欄位。 如果您的組織使用 Azure Active Directory，[名稱]**** 欄位會作為搜尋功能來尋找您目前目錄中的人員，如此您就可以從搜尋結果中選取正確的使用者。 選取該人員之後，會自動填入登入電子郵件和通知電子郵件。
   > [!div class="mx-imgBorder"]
   > ![訂閱者詳細資料](_img/assign-license-add/subscriber-details.png "輸入訂閱者名稱和其他詳細資料，或從租使用者成員的中選擇。")

    > [!NOTE]
    > 若要在您輸入訂閱者名稱時顯示 Azure Active Directory 租使用者的成員，則系統管理員必須是租使用者的成員。 


    如果您想要讓此訂閱者在登入 [Visual Studio 訂用帳戶入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs)時可存取軟體下載，請務必保持 [下載設定]**** 區段的 [下載] 切換按鈕為啟用狀態。 如果您選擇停用下載，使用者將無法存取軟體下載。  也會停用對產品金鑰的存取。  訂閱者仍可存取訂用帳戶中包含的所有其他權益。
   > [!div class="mx-imgBorder"]
   > ![下載時的存取權]（media/access-to-downloads.png "選擇 [允許] 以提供訂閱者軟體下載的存取權）。

    如果您想要將自己的參考資訊新增至訂用帳戶，您可在 [新增參考]**** 區段中執行此作業。
   > [!div class="mx-imgBorder"]
   > ![將您自己的參考資訊新增至每個訂用帳戶](media/add-subscriber-reference-notes.png "使用 [參考欄位] 來記錄與此訂用帳戶相關的任何附注。")

    當您完成選取選項，並輸入訂閱者資料時，請選擇 [新增訂閱者]**** 飛出視窗底部的 [新增]****。
   > [!div class="mx-imgBorder"]
   > ![選擇 [新增] 按鈕](media/add-button.png "按一下 [新增] 以儲存資訊，並將訂閱指派給訂閱者。")

## <a name="resend-assignment-emails"></a>重新傳送指派電子郵件
新增訂閱者之後，系統會將指派電子郵件自動傳送給新的訂閱者，並提供進一步的指示。 您可以選取訂閱者，然後按一下頂端功能表中的 [**重新**傳送] 按鈕，隨時重新傳送指派電子郵件。  若要重新傳送電子郵件給多個使用者，請在選取訂閱者時按住**Ctrl**鍵。  當您按一下 [**重新**傳送] 按鈕時，您會看到對話方塊，要求您確認是否要重新傳送給那些訂閱者。  

## <a name="see-also"></a>另請參閱
- [Visual Studio 文件](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [Microsoft 365 檔](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>後續步驟
- 要新增大量使用者嗎？  了解如何指派訂閱給[多個訂閱者](assign-license-bulk.md)。
- 需要協助嗎？  連絡人[Visual Studio 系統管理與](https://visualstudio.microsoft.com/support/support-overview-vs)訂用帳戶支援。


