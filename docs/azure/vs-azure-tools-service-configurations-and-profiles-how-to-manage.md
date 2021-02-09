---
title: 如何管理服務組態和設定檔 | Microsoft Docs
description: 了解如何使用服務組態和設定檔組態檔案 | 其儲存部署環境的設定及雲端服務的發佈設定。
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/11/2017
ms.author: ghogen
ms.openlocfilehash: e1c97670a91f2d90a01fef24f592e6ce2d5b05fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99843809"
---
# <a name="how-to-manage-service-configurations-and-profiles"></a>如何管理服務組態和設定檔
## <a name="overview"></a>概觀
當您發佈雲端服務時，Visual Studio 會將組態資訊儲存在兩種組態檔中：服務組態和設定檔。 服務組態 (.cscfg 檔) 可儲存 Azure 雲端服務的部署環境設定。 Azure 會在管理雲端服務時使用這些組態檔。 另一方面，設定檔 (.azurePubxml 檔案) 可儲存雲端服務的發佈設定。 這些設定是您使用發佈精靈時所選內容的記錄，可由 Visual Studio 在本機使用。 本主題說明如何使用這兩種類型的組態檔。

## <a name="service-configurations"></a>服務組態
您可以建立多個服務組態，以便用於每個部署環境。 例如，您可針對用來執行和測試 Azure 應用程式的本機環境建立一個服務組態，針對實際執行環境建立另一個服務組態。

您可以根據需求來新增、刪除、重新命名和修改這些服務組態。 您可以從 Visual Studio 管理這些服務組態，如下圖所示。

![管理服務組態](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-service-config.png)

您也可以從角色的屬性頁開啟 [管理組態] 對話方塊。 若要在 Azure 專案中開啟角色的屬性，請開啟該角色的捷徑功能表，然後選擇 [屬性]。 在 [設定] 索引標籤上，展開 [服務組態] 清單，然後選取 [管理] 以開啟 [管理組態] 對話方塊。

### <a name="to-add-a-service-configuration"></a>新增服務組態
1. 在方案總管中，開啟 Azure 專案的快捷方式功能表，然後選取 [ **管理** 設定]。

    [管理服務組態] 對話方塊隨即出現。
2. 若要新增服務組態，您必須建立一份現有的組態。 若要這樣做，請從 [名稱] 清單中選擇您要複製的組態，然後選取 [建立複本] 。
3. (選擇性) 若要給予服務組態不同的名稱，請從 [名稱] 清單中選擇新的服務組態，然後選取 [重新命名] 。 在 [名稱] 文字方塊中輸入您要用於此服務組態的名稱，然後按選取 [確定]。

    方案總管中的 Azure 專案已新增了一個叫做 ServiceConfiguration.[New Name].cscfg 的新服務組態檔。

### <a name="to-delete-a-service-configuration"></a>刪除服務組態
1. 在方案總管中，開啟 Azure 專案的快捷方式功能表，然後選取 [ **管理** 設定]。

    [管理服務組態] 對話方塊隨即出現。
2. 若要刪除服務組態，請從 [名稱] 清單中選擇您要刪除的組態，然後選取 [移除]。 隨即出現一個對話方塊，以確認您要刪除此組態。
3. 選取 [刪除]。

     在 [方案總管] 中，此服務組態檔會從 Azure 專案中移除。

### <a name="to-rename-a-service-configuration"></a>重新命名服務組態
1. 在方案總管中，開啟 Azure 專案的快捷方式功能表，然後選取 [ **管理** 設定]。

    [管理服務組態] 對話方塊隨即出現。
2. 若要將服務組態重新命名，請從 [名稱] 清單中選擇新的服務組態，然後選取 [重新命名]。 在 [ **名稱** ] 文字方塊中，輸入您要用於此服務設定的名稱，然後選取 **[確定]**。

    在 [方案總管] 中，此服務組態檔的名稱會在 Azure 專案中變更。

### <a name="to-change-a-service-configuration"></a>變更服務組態
* 如果您想要變更服務組態，請開啟 Azure 專案中您要變更的特定角色的捷徑功能表，然後按一下 [屬性] 。 如需詳細資訊，請參閱 [如何：使用 Visual Studio 設定 Azure 雲端服務的角色](vs-azure-tools-configure-roles-for-cloud-service.md) 。

## <a name="make-different-setting-combinations-by-using-profiles"></a>使用設定檔製作不同的設定組合
只要使用設定檔，您就能針對不同用途，以不同的設定組合來自動填滿 [發佈精靈]  。 例如，您可有一個設定檔用於偵錯，另一個設定檔用於發行組建。 在此情況下，[偵錯] 設定檔會啟用 [IntelliTrace] 並選取 [偵錯] 組態，而 [發行] 設定檔會停用 [IntelliTrace] 並選取 [發行] 組態。 您也可以使用不同的設定檔，部署使用不同儲存體帳戶的服務。

當您第一次執行精靈時，會建立預設設定檔。 Visual Studio 將以副檔名為 .azurePubXml 的檔案儲存設定檔，而該檔案會加入至 Azure 專案的 [設定檔] 資料夾。 如果您在執行精靈時手動指定不同的選擇，此檔案會自動更新。 執行下列程序之前，您應該已經發佈您的雲端服務至少一次。

### <a name="to-add-a-profile"></a>新增設定檔
1. 開啟 Azure 專案的捷徑功能表，然後選取 [發佈] 。
2. 選取 [目標設定檔] 清單旁邊的 [儲存設定檔] 按鈕，如下圖所示。 這會為您建立設定檔。

    ![建立新的設定檔](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/create-new-profile.png)
3. 建立設定檔之後，選取 [目標設定檔] 清單中的 [<管理...>]。

    [管理設定檔] 對話方塊隨即出現，如下圖所示。

    ![管理設定檔對話方塊](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-profiles.png)
4. 在 [名稱] 清單中選擇某個設定檔，然後選取 [建立複本]。
5. 選擇 [**關閉**] 按鈕。

    新的設定檔會出現在 [目標設定檔] 清單中。
6. 在 [目標設定檔]  清單中，選取您剛建立的設定檔。 [發佈精靈] 設定會填入您所選設定檔中的選項。
7. 選取 [上一步] 和 [下一步] 按鈕以顯示「發佈精靈」的每個頁面，然後自訂此設定檔的設定。 如需相關資訊，請參閱 [發佈 Azure 應用程式精靈](vs-azure-tools-publish-azure-application-wizard.md) 。
8. 自訂完設定之後，選取 [下一步]  以返回「設定」頁面。 當您使用這些設定來發佈服務，或是選取設定檔清單旁邊的 [儲存]  時，就會儲存設定檔。

### <a name="to-rename-or-delete-a-profile"></a>重新命名或刪除設定檔
1. 開啟 Azure 專案的捷徑功能表，然後選取 [發佈] 。
2. 在 [目標設定檔] 清單中，選取 [管理]。
3. 在 [管理設定檔] 對話方塊方塊中，選取您要刪除的設定檔，然後選取 [移除]。
4. 在出現的確認對話方塊中，選取 [確定] 。
5. 選取 [關閉]。

### <a name="to-change-a-profile"></a>變更設定檔
1. 開啟 Azure 專案的捷徑功能表，然後選取 [發佈] 。
2. 在 [目標設定檔]  清單中，選取您要變更的設定檔。
3. 選取 [上一步] 和 [下一步] 按鈕以顯示「發佈精靈」的每個頁面，然後變更您想要的設定。 如需相關資訊，請參閱 [發佈 Azure 應用程式精靈](vs-azure-tools-publish-azure-application-wizard.md) 。
4. 變更完設定之後，選取 [下一步] 以返回 **「設定」** 頁面。
5. (選擇性) 選取 [發佈]  以使用新設定來發佈雲端服務。 如果您不想在此時發佈雲端服務，而關閉 [發佈精靈]，Visual Studio 會詢問您是否要將變更儲存至設定檔。

## <a name="next-steps"></a>下一步
若要瞭解如何從 Visual Studio 設定 Azure 專案的其他部分，請參閱設定 [Azure 專案](vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address.md)。
