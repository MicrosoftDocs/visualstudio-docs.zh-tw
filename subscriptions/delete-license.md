---
title: 在訂用帳戶系統管理員入口網站中刪除 Visual Studio 訂用帳戶指派 |Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 10/26/2020
ms.topic: how-to
description: 瞭解系統管理員如何在 Visual Studio 訂閱系統管理入口網站中刪除訂用帳戶指派
ms.openlocfilehash: 22a1c55bcaef436d1a29eb84b93a57f407114a1e
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904476"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>刪除 Visual Studio 訂閱的指派
當訂閱者因為離開公司、完成專案，或轉換至新的工作角色等原因，而不再需要 Visual Studio 訂閱時，您可以將其訂閱移除，並指派給其他人。 請注意，當您重新指派訂閱時，不會重設所有訂閱者權益。  新的使用者將能夠過領取任何未領取的金鑰，並檢視先前已領取的金鑰，然而系統「不會重設」  領取限制。  針對擁有 Enterprise 合約 (EA) 的組織，原始使用者曾使用的任何權益 (例如 Pluralsight 訓練) 都會被重設。 

觀賞這段影片，或繼續閱讀以瞭解如何刪除指派。  

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yG2q]

## <a name="delete-a-subscription-assignment"></a>刪除訂用帳戶指派
1. 按一下您想要移除的訂閱者名稱。 若要選取多個要移除的訂閱者，您可以按一下訂閱者名稱左邊的圓形來選取每一個訂閱者。  或者，您可以按住 **CTRL** 鍵，然後按一下您想要移除的每個訂閱者。 若要移除訂閱者的範圍，請按一下第一個，按下 **Shift** 鍵，然後按一下最後一個。  按 **CTRL + A** 選取並移除所有訂閱者。 在此範例中，會刪除三個訂閱者（琥珀色、Kai 和 Madison）。 
2. 若要刪除選取的訂閱者，請按一下 [刪除]  。
3. 當出現確認刪除的訊息時，請按一下 [確定]  。
   > [!div class="mx-imgBorder"]
   > ![刪除訂閱者](_img/delete-license/delete-subscribers.png "選擇您想要刪除的使用者 (s) ，然後按一下 [刪除]。您可以使用 CTRL 和 Shift 鍵來選取多個訂閱者。")

   > [!NOTE]
   > 使用範本的大量刪除無法使用。 
   >
   > 如果您透過 Azure Active Directory 安全性群組新增了訂用帳戶指派，則可能需要24小時的時間，才能在系統管理員入口網站中更新刪除。  如需使用 Azure Active Directory 群組來管理訂用帳戶的詳細資訊，請參閱 [我們的文章](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) 。 

## <a name="see-also"></a>請參閱
- [Visual Studio 檔](/visualstudio/)
- [Azure DevOps 檔](/azure/devops/)
- [Azure 檔](/azure/)
- [Microsoft 365 檔](/microsoft-365/)

## <a name="next-steps"></a>下一步
- 需要在不刪除的情況下變更訂閱？  了解如何[編輯訂閱](edit-license.md)
- 如需協助以尋找特定的訂閱，請參閱[搜尋訂閱](search-license.md)。
- 需要建立您所有訂閱項目的清單嗎？  請參閱[匯出訂閱](exporting-subscriptions.md)。