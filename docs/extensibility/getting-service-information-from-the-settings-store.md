---
title: 從設定存放區取得服務資訊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f65fe81d1b2382df3847c2cfdc0b8ffbfff5662
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342431"
---
# <a name="get-service-information-from-the-settings-store"></a>從設定存放區取得服務資訊
若要尋找所有可用的服務，或判斷是否已安裝特定的服務，您可以使用設定存放區。 您必須知道服務類別的型別。

## <a name="to-list-the-available-services"></a>若要列出可用的服務

1. 建立 VSIX 專案，名為`FindServicesExtension`，然後新增名為的自訂命令`FindServicesCommand`。 如需如何建立自訂命令的詳細資訊，請參閱[建立具有功能表命令的擴充功能](../extensibility/creating-an-extension-with-a-menu-command.md)

2. 在  *FindServicesCommand.cs*，新增下列 using 陳述式：

    ```vb
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. 取得組態設定存放區，然後尋找名為服務的子集合。 這個集合包含所有可用的服務。 在 `MenuItemCommand`方法，移除現有的程式碼，並將它取代為下列：

    ```
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

4. 建置此專案並開始偵錯。 實驗執行個體隨即出現。

5. 在實驗執行個體，在**工具**功能表上，按一下**叫用 FindServicesCommand**。

     您應該會看到列出的所有服務的訊息方塊。

     若要確認這些設定，您可以使用登錄編輯程式。

## <a name="find-a-specific-service"></a>尋找特定的服務
 您也可以使用<xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A>方法，以判斷是否已安裝特定的服務。 您必須知道服務類別的型別。

1. 在您在上一個程序中建立的專案 MenuItemCallback，搜尋 的組態設定存放區`Services`有由服務的 GUID 命名的子集合的集合。 在此情況下我們會說明服務。

    ```
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

3. 在實驗執行個體，在**工具**功能表上，按一下**叫用 FindServicesCommand**。

     您應該會看到含有文字的訊息**協助服務使用：** 後面 **，則為 True**或**False**。 若要確認這項設定，您可以使用登錄編輯程式，在先前步驟中所示。