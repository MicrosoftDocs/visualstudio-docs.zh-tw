---
title: 為每月訂閱設置管理員 |微軟文檔
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: 為每月訂閱設置管理員
ms.openlocfilehash: a5d7c6e9442efd70ea3e7c2b7e7da4239e226aa2
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "78289837"
---
# <a name="set-up-administrators-for-visual-studio-monthly-subscriptions"></a>為視覺化工作室每月訂閱設置管理員

視覺化工作室每月訂閱由管理員管理。 這些人可以指派訂用帳戶、編輯指派、新增或刪除訂用帳戶，以及執行其他訂用帳戶管理工作。

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Azure 訂用帳戶擁有者是第一個系統管理員

購買 Visual Studio 每月訂閱時，作為用於進行購買的 Azure 訂閱的擁有者，將自動設置為這些訂閱的管理員。

您可以通過[視覺化工作室市場](https://marketplace.visualstudio.com/subscriptions)購買每月訂閱，也可以聯繫雲解決方案供應商。 如果您透過 Visual Studio Marketplace 進行購買，購買體驗的結尾將提供您管理使用者的機會。 選擇該選項將帶您到視覺化工作室訂閱監管中心 - [https://manage.visualstudio.com](https://manage.visualstudio.com)。

一旦您購買了訂用帳戶，就可以隨時瀏覽[系統管理入口網站](https://manage.visualstudio.com)。 只需登錄到門戶，並在左上角選擇相應的 Azure 訂閱。

作為用於購買每月訂閱的 Azure 訂閱的擁有者，您還可以分配其他管理員。

## <a name="add-administrators"></a>新增系統管理員

增系統管理員：

1. 連線到 Azure 入口網站：[portal.azure.com](https://portal.azure.com)。
2. 使用用於購買 Visual Studio 每月訂閱的帳戶登錄。
3. 在**Azure 服務**下，選擇**成本管理 + 計費**。
   > [!div class="mx-imgBorder"]
   > ![選擇 Azure 服務下的成本管理和計費](_img/cloud-admin/azure-cost-billing.png)
4. 在 [我的訂閱]**** 清單中，選擇您用來進行購買的 Azure 訂用帳戶。
   > [!div class="mx-imgBorder"]
   > ![選擇訂用帳戶](_img/cloud-admin/subscription-list.png)
5. 按一下**訪問控制項 （IAM），該控制項**位於左側功能窗格中清單頂部附近。
6. 按一下頁面頂端的 [新增]**** 索引標籤。
7. 按一下 **"添加角色指派**"。
   > [!div class="mx-imgBorder"]
   > ![選擇"存取控制"，"添加"，添加角色指派](_img/cloud-admin/access-control-add.png)
8. 在右側的飛出窗格中，按一下窗格頂端的 [角色]**** 下拉式清單，向下捲動並選取 [使用者存取系統管理員]****。
9. 在使用者清單中，向下捲動至您想要設為系統管理員的使用者，並加以選取。 
   > [!div class="mx-imgBorder"]
   > ![選擇角色，使用者訪問管理員](_img/cloud-admin/add-role-user-access-admin.png)
10. 按一下 [儲存]****。
11. 按一下 [角色指派]**** 索引標籤，確認您選取的使用者現在會顯示為 [使用者存取系統管理員]。

新管理員現在可以登錄到[監管中心](https://manage.visualstudio.com)，選擇用於從頁面左上角清單中購買每月訂閱的相同 Azure 訂閱，並開始管理這些訂閱。

> [!NOTE]
> 如果您看到使用者有權訪問編輯未作為管理員建立的每月訂閱，則使用者可能在基礎 Azure 訂閱中具有允許他們管理訂閱的角色。 這些角色包括：擁有者、參與者、服務管理員或共同管理員。有關詳細資訊，請訪問[添加計費管理器](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts)。

有關 Visual Studio 每月訂閱的資訊，請參閱購買訂閱下的[概述](vscloud-overview.md)。 要購買 Visual Studio 每月訂閱，請訪問[https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription)

## <a name="see-also"></a>另請參閱
- [視覺化工作室文檔](https://docs.microsoft.com/visualstudio/)
- [Azure 開發人員文檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [微軟 365 文檔](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>後續步驟
詳細瞭解如何管理視覺化工作室訂閱。
- [分配單個訂閱](assign-license.md)
- [分配多個訂閱](assign-license-bulk.md)
- [編輯訂閱](edit-license.md)
- [確定最大使用量](maximum-usage.md)



