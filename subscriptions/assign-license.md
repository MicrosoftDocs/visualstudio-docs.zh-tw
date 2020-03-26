---
title: 指派 Visual Studio 訂閱的授權 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 03/02/2020
ms.topic: conceptual
description: 了解系統管理員如何指派訂閱者授權
ms.openlocfilehash: 87334251532dbaa127d4def8c33a9814c28d42e1
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232711"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>在 Visual Studio 訂閱系統管理入口網站中指派授權
身為 Visual Studio 訂閱系統管理員，您可以使用系統管理入口網站，將訂閱指派給個別使用者和使用者群組。

對於使用者組，您可以選擇如何分配訂閱。  
- 您可以一次分配一個訂閱。
- 您還可以使用[大量新增](assign-license-bulk.md)功能快速輕鬆地上傳訂閱者清單及其訂閱資訊。
- 如果您的組織使用 Microsoft Azure 活動目錄 （Azure AD），則可以使用 Azure AD 組將訂閱分配給使用者組。  （此功能分階段部署，您的組織可能不會立即使用此功能。


## <a name="add-a-single-subscriber"></a>新增一位訂閱者
下面瞭解如何為新使用者分配 Visual Studio 訂閱，以便他們可以訪問訂閱權益。

1. 登錄到[監管中心](https://manage.visualstudio.com)。
2. 要將許可證分配給表頂部的單個 Visual Studio 訂閱者，請選擇"**添加**"，然後選擇 **"單個訂閱者**"。
   > [!div class="mx-imgBorder"]
   > ![新增一位訂閱者](_img/assign-license-add/add-subscriber-individual.png)
3. 將資訊輸入至新訂閱者的表單欄位。 如果您的組織使用 Azure Active Directory，[名稱]**** 欄位會作為搜尋功能來尋找您目前目錄中的人員，如此您就可以從搜尋結果中選取正確的使用者。 選取該人員之後，會自動填入登入電子郵件和通知電子郵件。
   > [!div class="mx-imgBorder"]
   > ![訂閱者詳細資料](_img/assign-license-add/subscriber-details.png)

    如果您想要讓此訂閱者在登入 [Visual Studio 訂用帳戶入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs)時可存取軟體下載，請務必保持 [下載設定]**** 區段的 [下載] 切換按鈕為啟用狀態。 如果您選擇停用下載，則使用者無法存取軟體下載，但仍可存取訂用帳戶中所含的所有其他權益。
   > [!div class="mx-imgBorder"]
   > ![存取下載項目](media/access-to-downloads.png)

    如果您想要將自己的參考資訊新增至訂用帳戶，您可在 [新增參考]**** 區段中執行此作業。
   > [!div class="mx-imgBorder"]
   > ![在每個訂閱中新增您自己的參考資訊](media/add-subscriber-reference-notes.png)

    當您完成選取選項，並輸入訂閱者資料時，請選擇 [新增訂閱者]**** 飛出視窗底部的 [新增]****。
   > [!div class="mx-imgBorder"]
   > ![選擇 [新增] 按鈕](media/add-button.png)

## <a name="resend-assignment-emails"></a>重新發送分配電子郵件
添加訂閱者後，分配電子郵件將自動發送到新訂閱者，並提供進一步說明。 您可以隨時通過選擇訂閱者並按一下頂部功能表中的 **"重新發送"** 按鈕再次發送分配電子郵件。  要向多個使用者重新發送電子郵件，請按住**Ctrl**金鑰，同時選擇訂閱者。  按一下"**重新發送"** 按鈕時，您將看到一個對話方塊，要求您確認要重新發送給這些訂閱者。  

## <a name="see-also"></a>另請參閱
- [視覺化工作室文檔](https://docs.microsoft.com/visualstudio/)
- [Azure 開發人員文檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [微軟 365 文檔](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>後續步驟
- 要新增大量使用者嗎？  了解如何指派訂閱給[多個訂閱者](assign-license-bulk.md)。
- 需要協助嗎？  聯繫[視覺化工作室管理和訂閱支援](https://visualstudio.microsoft.com/support/support-overview-vs)。


