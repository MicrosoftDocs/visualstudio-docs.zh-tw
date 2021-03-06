---
title: 設定每月 Visual Studio 訂閱的管理員 |Microsoft 檔
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 8b30e2bc-2ac3-4fcc-b296-128731471032
ms.date: 02/18/2021
ms.topic: how-to
description: 設定每月訂閱的系統管理員
ms.openlocfilehash: c018dbc3437c03c6d029a98c84e0b6cceaef9e2c
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249543"
---
# <a name="set-up-admins-for-visual-studio-monthly-subscriptions"></a>設定 Visual Studio 每月訂閱的管理員

Visual Studio 每月訂閱是由系統管理員管理。 這些人可以指派訂用帳戶、編輯指派、新增或刪除訂用帳戶，以及執行其他訂用帳戶管理工作。

## <a name="the-azure-subscription-owner-is-the-first-admin"></a>Azure 訂用帳戶擁有者是第一個系統管理員

當您購買 Visual Studio 每月訂用帳戶時，如果是用來進行購買的 Azure 訂用帳戶擁有者，系統會自動將您設定為這些訂用帳戶的系統管理員。

您可以透過 [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions)購買每月訂閱，或藉由聯絡雲端解決方案提供者。 如果您透過 Visual Studio Marketplace 進行購買，購買體驗的結尾將提供您管理使用者的機會。 選擇該選項會帶您前往 Visual Studio 訂用帳戶的系統管理入口網站 [https://manage.visualstudio.com](https://manage.visualstudio.com) 。

一旦您購買了訂用帳戶，就可以隨時瀏覽[系統管理入口網站](https://manage.visualstudio.com)。 只需登入入口網站，然後在左上角選取適當的 Azure 訂用帳戶。

作為用來購買每月訂用帳戶的 Azure 訂用帳戶擁有者，您也可以指派其他系統管理員。

## <a name="add-admins"></a>加入管理員

若要新增系統管理員：

1. 連接到 Azure 入口網站，網址為 [portal.azure.com](https://portal.azure.com)。
2. 使用您用來購買 Visual Studio 每月訂閱的帳戶登入。
3. 在 [ **Azure 服務**] 下，選擇 [ **成本管理 + 計費**]。
   > [!div class="mx-imgBorder"]
   > ![選擇 Azure 服務下的成本管理 + 計費](_img/cloud-admin/azure-cost-billing.png "從 Azure 服務群組選擇成本管理")
4. 在 [ **我的訂閱** ] 清單中，選擇您用來進行購買的 Azure 訂用帳戶。
   > [!div class="mx-imgBorder"]
   > ![選擇訂用帳戶](_img/cloud-admin/subscription-list.png "選擇您想要用來進行購買的 Azure 訂用帳戶。")
5. 按一下 [ **存取控制] (IAM)**，位於左側流覽窗格中的清單頂端附近。
6. 按一下頁面頂端的 [ **新增** ] 索引標籤。
7. 按一下 [ **新增角色指派**]。
   > [!div class="mx-imgBorder"]
   > ![選擇 [存取控制]、[新增]、[新增角色指派]](_img/cloud-admin/access-control-add.png "從左側清單中選擇 [存取控制]，然後選擇 [新增]。")
8. 在右側的飛出窗格中，按一下窗格頂端的 [角色] 下拉式清單，向下捲動並選取 [使用者存取系統管理員]。
9. 在使用者清單中，向下捲動至您想要設為系統管理員的使用者，並加以選取。 
   > [!div class="mx-imgBorder"]
   > ![選擇角色、使用者存取系統管理員](_img/cloud-admin/add-role-user-access-admin.png "選擇 [角色]，選取 [使用者存取系統管理員]，然後選取使用者的名稱，讓他們成為系統管理員。")
10. 按一下 [儲存]。
11. 按一下 [角色指派] 索引標籤，確認您選取的使用者現在會顯示為 [使用者存取系統管理員]。

新的系統管理員現在可以登入系統 [管理入口網站](https://manage.visualstudio.com)，從頁面左上角的清單中選取用來購買每月訂閱的相同 Azure 訂用帳戶，然後開始管理這些訂用帳戶。

> [!NOTE]
> 如果您看到使用者有權編輯您未以系統管理員身份建立的每月訂用帳戶，他們可能會在基礎 Azure 訂用帳戶中擁有可讓他們管理訂用帳戶的角色。 這些角色包括：擁有者、參與者、服務管理員或共同管理員。如需詳細資訊，請造訪 [新增帳單管理員](/azure/devops/organizations/billing/add-backup-billing-managers)。

如需 Visual Studio 每月訂閱的詳細資訊，請參閱購買訂閱下的 [總覽](vscloud-overview.md) 。 若要購買 Visual Studio 每月訂閱，請造訪 Visual Studio Marketplace [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription) 。

## <a name="resources"></a>資源
- [訂閱支援](https://visualstudio.microsoft.com/subscriptions/support/)


## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](/visualstudio/)
- [Azure DevOps 文件](/azure/devops/) \(英文\)
- [Azure 檔](/azure/)
- [Microsoft 365 檔](/microsoft-365/)

## <a name="next-steps"></a>下一步
深入瞭解如何管理 Visual Studio 訂閱。
- [指派個別訂用帳戶](assign-license.md)
- [指派多個訂用帳戶](assign-license-bulk.md)
- [編輯訂用帳戶](edit-license.md)
- [判斷最大使用量](maximum-usage.md)