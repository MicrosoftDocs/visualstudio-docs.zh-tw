---
title: 從設定存放區取得服務資訊 |Microsoft Docs
description: 瞭解如何使用設定存放區來尋找所有可用的服務，或判斷是否已安裝特定的服務。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 57a273d994e6b8a4b34a139ab98713cc8c6cd83b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968121"
---
# <a name="get-service-information-from-the-settings-store"></a>從設定存放區取得服務資訊
您可以使用 [設定] 存放區來尋找所有可用的服務，或判斷是否已安裝特定的服務。 您必須知道服務類別的型別。

## <a name="to-list-the-available-services"></a>列出可用的服務

1. 建立名為的 VSIX 專案 `FindServicesExtension` ，然後新增名為的自訂命令 `FindServicesCommand` 。 如需有關如何建立自訂命令的詳細資訊，請參閱[使用功能表命令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能

2. 在 *FindServicesCommand.cs* 中，新增下列 using 指示詞：

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. 取得設定存放區，然後尋找名為服務的子集合。 此集合包含所有可用的服務。 在 `MenuItemCommand` 方法中，移除現有的程式碼，並將它取代為下列程式碼：

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

4. 建置此專案並開始偵錯。 實驗實例隨即出現。

5. 在實驗性實例中，按一下 [ **工具** ] 功能表上的 [叫用 **FindServicesCommand**]。

     您應該會看到列出所有服務的訊息方塊。

     若要確認這些設定，您可以使用登錄編輯程式。

## <a name="find-a-specific-service"></a>尋找特定的服務
 您也可以使用 <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> 方法來判斷是否已安裝特定的服務。 您必須知道服務類別的型別。

1. 在您于上一個程式中建立的專案 MenuItemCallback 中，搜尋設定存放區中的 `Services` 集合，其中包含由服務的 GUID 命名的子集合。 在此案例中，我們會尋找說明服務。

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

3. 在實驗性實例中，按一下 [ **工具** ] 功能表上的 [叫用 **FindServicesCommand**]。

     您應該會看到含有 text **Help Service**  的訊息：後面接著 **True** 或 **False**。 若要確認這項設定，您可以使用登錄編輯程式，如先前的步驟所示。
