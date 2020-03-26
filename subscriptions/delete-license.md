---
title: 在 Visual Studio 訂閱系統管理入口網站中刪除訂閱指派 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 03/03/2020
ms.topic: conceptual
description: 了解系統管理員如何刪除訂閱指派
ms.openlocfilehash: a884cb56b9c04558023659317ecce2d06a8ec54d
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232545"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>刪除 Visual Studio 訂閱的指派
當訂閱者因為離開公司、完成專案，或轉換至新的工作角色等原因，而不再需要 Visual Studio 訂閱時，您可以將其訂閱移除，並指派給其他人。 請注意，當您重新分配訂閱時，並非所有訂閱者權益都將重置。  新的使用者將能夠過領取任何未領取的金鑰，並檢視先前已領取的金鑰，然而系統「不會重設」**** 領取限制。  針對擁有 Enterprise 合約 (EA) 的組織，原始使用者曾使用的任何權益 (例如 Pluralsight 訓練) 都會被重設。 

## <a name="delete-a-subscription-assignment"></a>刪除訂閱分配
1. 按一下您想要移除的訂閱者名稱。 要選擇要刪除的多個訂閱者，可以按一下訂閱者名稱左側的圓圈以選擇每個訂閱者名稱。  或者，您可以按住**CTRL**金鑰，然後按一下要刪除的每個訂閱者。  按**CTRL + A**以選擇和刪除所有訂閱者。 
2. 若要刪除選取的訂閱者，請按一下 [刪除]****。
3. 當出現確認刪除的訊息時，請按一下 [確定]****。
   > [!div class="mx-imgBorder"]
   > ![刪除訂閱者](_img/delete-license/delete-subscribers.png)

   > [!NOTE]
   > 使用範本進行大量刪除不可用。 有關通過 Azure 活動目錄安全性群組管理訂閱分配的組織，請參閱[我們的文章](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions)，瞭解有關刪除如何發生的詳細資訊。  

## <a name="see-also"></a>另請參閱
- [視覺化工作室文檔](https://docs.microsoft.com/visualstudio/)
- [Azure 開發人員文檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [微軟 365 文檔](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>後續步驟
- 需要在不刪除的情況下變更訂閱？  了解如何[編輯訂閱](edit-license.md)
- 如需協助以尋找特定的訂閱，請參閱[搜尋訂閱](search-license.md)。
- 需要建立您所有訂閱項目的清單嗎？  請參閱[匯出訂閱](exporting-subscriptions.md)。


