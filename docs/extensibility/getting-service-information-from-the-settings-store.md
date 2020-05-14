---
title: 從設置商店獲取服務資訊 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b15d5c9f122ca66d21940b9998969b0d39d1a74d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711379"
---
# <a name="get-service-information-from-the-settings-store"></a>從設定儲存處取得服務資訊
您可以使用設定儲存查找所有可用服務或確定是否安裝了特定服務。 您必須知道服務類的類型。

## <a name="to-list-the-available-services"></a>列出可用服務

1. 建立名為`FindServicesExtension`的 VSIX 專案,然後`FindServicesCommand`添加名為的自定義命令。 有關如何建立自訂指令的詳細資訊,請參閱[使用選單命令建立擴展](../extensibility/creating-an-extension-with-a-menu-command.md)

2. 在*FindServicesCommand.cs*中,新增以下使用指令:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. 獲取配置設置存儲,然後查找名為"服務"的子集合。 此集合包括所有可用的服務。 在`MenuItemCommand`方法中,刪除現有代碼並將其取代為以下內容:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string message = "Available services:\n";
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");
        int n = 0;
        foreach (string service in collection)
        {
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";
        }

        MessageBox.Show(message);
    }
    ```

4. 建置此專案並開始偵錯。 出現實驗實例。

5. 在實驗實例中,在 **「工具」** 功能表上,按一下 **「調用查找服務命令**」。。

     您應該會看到一個消息框,列出所有服務。

     要驗證這些設置,可以使用註冊錶編輯器。

## <a name="find-a-specific-service"></a>尋找特定服務
 您還可以使用方法<xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A>來確定是否安裝了特定服務。 您必須知道服務類的類型。

1. 在上一過程中創建的專案的 MenuItem 回撥中,搜索配置設定存儲中具有由`Services`服務的 GUID 命名的子集合的集合。 在這種情況下,我們將查找幫助服務。

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);
        string message = "Help Service Available: " + hasHelpService;

        MessageBox.Show(message);
    }
    ```

2. 建置此專案並開始偵錯。

3. 在實驗實例中,在 **「工具」** 功能表上,按一下 **「調用查找服務命令**」。。

     您應該會看到一條消息,其中文本 **"幫助服務可用":** 後跟 **"真****"或"假**"。 要驗證此設置,可以使用註冊錶編輯器,如前面的步驟所示。
