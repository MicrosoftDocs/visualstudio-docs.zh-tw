---
title: 如何管理服務組態和設定檔 |Microsoft Docs
description: 了解如何使用服務組態和設定檔設定檔 |其中儲存的部署環境的設定，並發佈雲端服務的設定。
author: ghogen
manager: douge
assetId: 7da8c551-fb06-4057-b5c7-c77f4b39d803
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/11/2017
ms.author: ghogen
ms.openlocfilehash: 3f7c7341b115f0899ac4c90d574a65dfdb4087bc
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001992"
---
# <a name="how-to-manage-service-configurations-and-profiles"></a>如何管理服務設定與設定檔
## <a name="overview"></a>總覽
當您發行雲端服務時，Visual Studio 會將組態資訊儲存在組態檔的兩種： 服務組態和設定檔。 服務組態 （.cscfg 檔） 儲存 Azure 雲端服務的部署環境的設定。 管理您的雲端服務時，azure 會使用這些組態檔。 相反地，設定檔 （.azurePubxml 檔案） 存放區發行雲端服務的設定。 這些設定是您使用發行精靈 中，並在本機將供 Visual Studio 時所選的記錄。 本主題說明如何使用這兩種類型的組態檔。

## <a name="service-configurations"></a>服務組態
您可以建立要用於每個部署環境的多個服務組態。 例如，您可以建立您用來執行和測試 Azure 應用程式和您的生產環境的另一個服務組態的本機環境的服務組態。

您可以新增、 刪除、 重新命名，並修改這些服務組態，根據您的需求。 您可以從 Visual Studio 中，管理這些服務組態，如下圖所示。

![管理服務組態](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-service-config.png)

您也可以開啟**管理組態**從角色的屬性頁 對話方塊。 若要開啟 Azure 專案中的 角色內容，開啟該角色的捷徑功能表，然後選擇 **屬性**。 在上**設定**索引標籤上，展開**服務組態**清單，然後再選取**管理**以開啟**管理組態** 對話方塊。

### <a name="to-add-a-service-configuration"></a>若要新增服務組態
1. 在 [方案總管] 中，開啟 Azure 專案的捷徑功能表，然後選取**管理組態**。
   
    **管理服務組態** 對話方塊隨即出現。
2. 若要新增的服務組態，您必須建立一份現有的組態。 若要這樣做，請選擇 複製 名稱 清單，然後選取您想要的組態**建立複本**。
3. （選擇性）若要給予服務組態不同的名稱，從 [名稱] 清單中選擇新的服務組態，然後按**重新命名**。 在 **名稱**文字方塊中，輸入您想要用於這個服務組態，然後選取名稱**確定**。
   
    名為 Serviceconfiguration.< 新服務組態檔。[New Name].cscfg 加入方案總管 中的 Azure 專案。

### <a name="to-delete-a-service-configuration"></a>若要刪除服務組態
1. 在 [方案總管] 中，開啟 Azure 專案的捷徑功能表，然後選取**管理組態**。
   
    **管理服務組態** 對話方塊隨即出現。
2. 若要刪除服務組態，選擇您想要刪除的組態**名稱**列出，然後選取**移除**。 對話方塊會出現以確認您想要刪除此組態。
3. 選取 **刪除**。
   
     服務組態檔會從 [方案總管] 中的 Azure 專案中移除。

### <a name="to-rename-a-service-configuration"></a>若要重新命名服務組態
1. 在 [方案總管] 中，開啟 Azure 專案的捷徑功能表，然後按**管理組態**。
   
    **管理服務組態** 對話方塊隨即出現。
2. 若要重新命名服務組態，請選擇 新的服務組態，從**名稱**清單，然後再選取**重新命名**。 在 **名稱**文字中，輸入您想要用於此服務組態，然後選取名稱**確定**。
   
    在方案總管 中的 Azure 專案中變更服務組態檔的名稱。

### <a name="to-change-a-service-configuration"></a>若要變更服務組態
* 如果您想要變更服務組態中，開啟您想要在 Azure 專案中，變更，然後選取特定角色的捷徑功能表**屬性**。 請參閱[如何： 使用 Visual Studio 在 Azure 雲端服務設定的角色](vs-azure-tools-configure-roles-for-cloud-service.md)如需詳細資訊。

## <a name="make-different-setting-combinations-by-using-profiles"></a>使用設定檔時，進行不同的設定組合
使用設定檔，您可以自動填寫**發行精靈**與不同的用途的不同設定組合。 比方說，您可以有一個設定檔用於偵錯，和另一個用於發行組建。 在此情況下，您**偵錯**設定檔會有**IntelliTrace**啟用和**偵錯**選取的組態和**發行**設定檔會有**IntelliTrace**停用並**發行**選取的組態。 您也可以使用不同的設定檔部署使用不同的儲存體帳戶的服務。

當您第一次執行精靈時，會使用預設設定檔。 Visual Studio 會儲存在副檔名為.azurePubXml，它會加入至您的 Azure 專案底下的檔案中的設定檔**設定檔**資料夾。 如果您手動指定不同的選擇，稍後再執行精靈時，檔案會自動更新。 執行下列程序之前，您應該已經發佈您的雲端服務至少一次。

### <a name="to-add-a-profile"></a>新增設定檔
1. 開啟您的 Azure 專案的捷徑功能表，然後選取**發佈**。
2. 旁**目標設定檔**清單中，選取**儲存設定檔**按鈕，如下圖所示。 這會為您建立設定檔。
   
    ![建立新的設定檔](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/create-new-profile.png)
3. 在建立設定檔之後，請選取 **< 管理...> >** 中**目標設定檔**清單。
   
    **管理設定檔**對話方塊隨即出現，如下圖所示。
   
    ![管理設定檔 對話方塊](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-profiles.png)
4. 在 **名稱**清單中，選擇的設定檔，然後選取**建立副本**。
5. 選擇**關閉** 按鈕。
   
    新的設定檔會出現在 目標設定檔清單。
6. 在 **目標設定檔**清單中，選取您剛才建立的設定檔。 發佈精靈 設定會填入您所選取的設定檔中的選項。
7. 選取 [**上一步**並**下一步]** 按鈕以顯示每個頁面的 [發行精靈]，然後自訂此設定檔設定。 請參閱[發佈 Azure 應用程式精靈](http://go.microsoft.com/fwlink/p/?LinkID=623085)的資訊。
8. 您完成自訂設定之後，請選取**下一步**回到 設定 頁面。 當您使用這些設定發行服務時，或如果您選取 儲存設定檔**儲存**旁邊的設定檔清單。

### <a name="to-rename-or-delete-a-profile"></a>若要重新命名或刪除設定檔
1. 開啟您的 Azure 專案的捷徑功能表，然後選取**發佈**。
2. 在 **目標設定檔**清單中，選取**管理**。
3. 在 [**管理設定檔**] 對話方塊中，選取您想要刪除的設定檔並選取**移除**。
4. 在出現確認對話方塊中，選取**確定**。
5. 選取 **關閉**。

### <a name="to-change-a-profile"></a>若要變更設定檔
1. 開啟您的 Azure 專案的捷徑功能表，然後選取**發佈**。
2. 在 **目標設定檔**清單中，選取您想要變更的設定檔。
3. 選取 [**上一步**並**下一步]** 按鈕以顯示每個頁面的 [發行精靈]，然後變更您想要的設定。 請參閱[發佈 Azure 應用程式精靈](http://go.microsoft.com/fwlink/p/?LinkID=623085)的資訊。
4. 您完成設定變更之後，請選取**下一步**回到**設定**頁面。
5. （選擇性） 選取**發佈**發行雲端服務使用新的設定。 如果您不想要發佈雲端服務，在此階段中，而且您關閉 發行精靈，Visual Studio 會詢問您如果您想要將變更儲存至設定檔。

## <a name="next-steps"></a>後續步驟
若要了解如何設定 Azure 專案從 Visual Studio 的其他部分，請參閱[設定 Azure 專案](http://go.microsoft.com/fwlink/p/?LinkID=623075)

