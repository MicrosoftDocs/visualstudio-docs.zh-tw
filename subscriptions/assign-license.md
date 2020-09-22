---
title: 指派 Visual Studio 訂閱的授權 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 03/02/2020
ms.topic: conceptual
description: 了解系統管理員如何指派訂閱者授權
ms.openlocfilehash: f458e12cd27688f910917842de89e6377675fb69
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "91006198"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>在 Visual Studio 訂閱系統管理入口網站中指派授權
身為 Visual Studio 訂閱系統管理員，您可以使用系統管理入口網站，將訂閱指派給個別使用者和使用者群組。

針對使用者群組，您可以選擇如何指派訂閱。  
- 您可以一次指派一個訂用帳戶。
- 您也可以使用「 [大量新增](assign-license-bulk.md) 」功能，快速且輕鬆地上傳訂閱者清單及其訂用帳戶資訊。
- 如果您的組織使用 Microsoft Azure Active Directory (Azure AD) ，您可以 [使用 Azure AD 群組將訂用帳戶指派](./assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) 給使用者群組。  


## <a name="add-a-single-subscriber"></a>新增一位訂閱者
以下說明如何將 Visual Studio 訂用帳戶指派給新使用者，讓他們可以存取訂用帳戶權益。

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. 登入系統 [管理入口網站](https://manage.visualstudio.com)。
2. 若要將授權指派給單一 Visual Studio 訂閱者，請選取資料表頂端的 [ **新增**]，然後選擇 [ **個別訂閱者**]。
   > [!div class="mx-imgBorder"]
   > ![新增一位訂閱者](_img/assign-license-add/add-subscriber-individual.png "選取 [新增]，然後選擇 [個別訂閱者] 以指派單一訂用帳戶。")
3. 將資訊輸入至新訂閱者的表單欄位。 如果您的組織使用 Azure Active Directory，[名稱]**** 欄位會作為搜尋功能來尋找您目前目錄中的人員，如此您就可以從搜尋結果中選取正確的使用者。 選取該人員之後，會自動填入登入電子郵件和通知電子郵件。
   > [!div class="mx-imgBorder"]
   > ![訂閱者詳細資料](_img/assign-license-add/subscriber-details.png "輸入訂閱者名稱和其他詳細資料，或從租使用者成員選擇。")

    > [!NOTE]
    > 當您輸入訂閱者名稱時，系統管理員必須是租使用者的成員，才能顯示 Azure Active Directory 租使用者的成員。 


    如果您想要讓此訂閱者在登入 [Visual Studio 訂用帳戶入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs)時可存取軟體下載，請務必保持 [下載設定]**** 區段的 [下載] 切換按鈕為啟用狀態。 如果您選擇停用下載，使用者將無法存取軟體下載。  也會停用對產品金鑰的存取。  訂閱者仍可存取訂用帳戶中包含的所有其他權益。
   > [!div class="mx-imgBorder"]
   > ![下載的存取] (媒體/access-to-downloads.png] 選擇 [允許]，為訂閱者提供軟體下載的存取權。) 

    如果您想要將自己的參考資訊新增至訂用帳戶，您可在 [新增參考]**** 區段中執行此作業。
   > [!div class="mx-imgBorder"]
   > ![將您自己的參考資訊新增至每個訂用帳戶](media/add-subscriber-reference-notes.png "使用 [參考] 欄位可記錄有關此訂用帳戶的任何附注。")

    當您完成選取選項，並輸入訂閱者資料時，請選擇 [新增訂閱者]**** 飛出視窗底部的 [新增]****。
   > [!div class="mx-imgBorder"]
   > ![選擇 [新增] 按鈕](media/add-button.png "選取 [加入] 以儲存資訊，並將訂閱指派給訂閱者。")

## <a name="resend-assignment-emails"></a>重新傳送指派電子郵件
加入訂閱者之後，會將指派電子郵件自動傳送給新的訂閱者，並提供進一步的指示。 您可以隨時重新傳送指派電子郵件，方法是選取 [訂閱者]，然後選取頂端功能表中的 [ **重新** 傳送] 按鈕。  若要重新傳送電子郵件給多位使用者，請按住 **Ctrl** 鍵，同時選取 [訂閱者]。  當您選取 [ **重新** 傳送] 按鈕時，您會看到一個對話方塊，要求您確認是否要重新傳送給這些訂閱者。  

## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](/visualstudio/)
- [Azure DevOps 檔](/azure/devops/)
- [Azure 檔](/azure/)
- [Microsoft 365 檔](/microsoft-365/)


## <a name="next-steps"></a>下一步
- 要新增大量使用者嗎？  了解如何指派訂閱給[多個訂閱者](assign-license-bulk.md)。
- 需要協助嗎？  請聯絡 [Visual Studio 管理和訂閱支援](https://visualstudio.microsoft.com/support/support-overview-vs)。