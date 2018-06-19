---
title: 從設定存放區取得服務資訊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 11731e36517ae6245dddd1ebdd3b002fb3c37391
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127499"
---
# <a name="getting-service-information-from-the-settings-store"></a>從設定存放區取得服務資訊
若要尋找所有可用的服務，或判斷是否已安裝特定的服務，您可以使用 「 設定存放區。 您必須知道服務類別的型別。  
  
### <a name="to-list-the-available-services"></a>若要列出可用的服務  
  
1.  建立名為 FindServicesExtension VSIX 專案，然後再加入 名為 FindServicesCommand 自訂命令。 如需如何建立自訂命令的詳細資訊，請參閱[建立擴充的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  在 FindServicesCommand.cs，加入下列 using 陳述式：  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3.  取得組態設定存放區，然後尋找名為服務的子集合。 這個集合會包含所有可用的服務。 在 MenuItemCommand 方法中，移除現有的程式碼，並以下列內容取代它：  
  
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
  
4.  建置此專案並開始偵錯。 實驗執行個體隨即出現。  
  
5.  在實驗執行個體，在**工具**功能表上，按一下 **叫用 FindServicesCommand**。  
  
     您應該會看到列出的所有服務的訊息方塊。  
  
     若要確認這些設定，您可以使用登錄編輯程式。  
  
## <a name="finding-a-specific-service"></a>尋找特定的服務  
 您也可以使用<xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A>方法，以判斷是否已安裝特定的服務。 您必須知道服務類別的型別。  
  
1.  在您建立之前程序中的專案 MenuItemCallback，搜尋的組態設定存放區`Services`具有名為服務的 guid 的子集合的集合。 在此情況下，我們會尋找說明服務。  
  
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
  
2.  建置此專案並開始偵錯。  
  
3.  在實驗執行個體，在**工具**功能表上，按一下 **叫用 FindServicesCommand**。  
  
     您應該會看到訊息的文字**協助服務可用：** 後面**True**或**False**。 若要確認這項設定，您可以使用登錄編輯程式，在先前步驟中所示。