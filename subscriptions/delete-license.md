---
title: 在 Visual Studio 訂閱系統管理入口網站中刪除訂閱指派 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 06/16/2020
ms.topic: how-to
description: 了解系統管理員如何刪除訂閱指派
ms.openlocfilehash: 4f952f574132afbd405c82c75fcddfc952bffb48
ms.sourcegitcommit: b8ce85a6d9c7fcceaad0fba625202f5ecf8f368c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2020
ms.locfileid: "87434268"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>刪除 Visual Studio 訂閱的指派
當訂閱者因為離開公司、完成專案，或轉換至新的工作角色等原因，而不再需要 Visual Studio 訂閱時，您可以將其訂閱移除，並指派給其他人。 請注意，當您重新指派訂閱時，不會重設所有的訂閱者權益。  新的使用者將能夠過領取任何未領取的金鑰，並檢視先前已領取的金鑰，然而系統「不會重設」**** 領取限制。  針對擁有 Enterprise 合約 (EA) 的組織，原始使用者曾使用的任何權益 (例如 Pluralsight 訓練) 都會被重設。 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yG2q]

## <a name="delete-a-subscription-assignment"></a>刪除訂用帳戶指派
1. 按一下您想要移除的訂閱者名稱。 若要選取要移除的多個訂閱者，您可以按一下訂閱者名稱左邊的圓圈來選取每一個。  或者，您可以按住**CTRL**鍵，然後按一下您想要移除的每個訂閱者。 若要移除某個範圍的訂閱者，請按一下第一個，按下**Shift**鍵，然後按一下最後一個。  按**CTRL + A**選取並移除所有訂閱者。 
2. 若要刪除選取的訂閱者，請按一下 [刪除]****。
3. 當出現確認刪除的訊息時，請按一下 [確定]****。
   > [!div class="mx-imgBorder"]
   > ![刪除訂閱者](_img/delete-license/delete-subscribers.png "選擇您想要刪除的使用者，然後按一下 [刪除]。您可以使用 CTRL 和 Shift 鍵來選取多個訂閱者。")

   > [!NOTE]
   > 無法使用範本的大量刪除。 針對透過 Azure Active Directory 安全性群組來管理訂用帳戶指派的組織，請參閱[我們的文章](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions)，以取得有關刪除如何發生的詳細資訊。  

## <a name="see-also"></a>另請參閱
- [Visual Studio 文件](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [Microsoft 365 檔](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>後續步驟
- 需要在不刪除的情況下變更訂閱？  了解如何[編輯訂閱](edit-license.md)
- 如需協助以尋找特定的訂閱，請參閱[搜尋訂閱](search-license.md)。
- 需要建立您所有訂閱項目的清單嗎？  請參閱[匯出訂閱](exporting-subscriptions.md)。


