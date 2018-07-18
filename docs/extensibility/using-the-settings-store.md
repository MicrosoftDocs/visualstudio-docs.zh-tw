---
title: 使用 「 設定存放區 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3919ee3973194967f9d0367ecd13c495b3b62af2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139285"
---
# <a name="using-the-settings-store"></a>使用 「 設定存放區
有兩種類型的設定存放區：  
  
-   組態設定，這是唯讀的 Visual Studio 和 VSPackage 設定。 Visual Studio 會合併到此存放區的所有已知的.pkgdef 檔的設定。  
  
-   使用者設定，這是可寫入的設定，例如在頁面上會顯示**選項**對話方塊、 屬性頁和某些其他對話方塊。 Visual Studio 擴充功能可能會使用這些本機存放裝置的少量資料。  
  
 本逐步解說示範如何讀取組態設定存放區中的資料。 請參閱[寫入使用者設定存放區](../extensibility/writing-to-the-user-settings-store.md)如需說明如何將寫入使用者設定存放區。  
  
## <a name="creating-the-example-project"></a>建立範例專案  
 本節說明如何建立簡單的擴充功能專案中示範的功能表命令。  
  
1.  每個 Visual Studio 擴充功能開頭 VSIX 部署專案，以將包含延伸模組資產。 建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSIX 專案，名為`SettingsStoreExtension`。 您可以找到 VSIX 專案範本，在**新專案**對話方塊底下**Visual C# / 擴充性**。  
  
2.  現在，加入名為的自訂命令項目範本**SettingsStoreCommand**。 在**加入新項目**對話方塊中，移至**Visual C# / 擴充性**選取**自訂命令**。 在**名稱**視窗的底部欄位中，將命令檔名稱變更為**SettingsStoreCommand.cs**。 如需如何建立自訂命令的詳細資訊，請參閱[建立擴充的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>使用組態設定存放區  
 本節說明如何偵測並顯示組態設定。  
  
1.  在 SettingsStorageCommand.cs 檔案中，加入下列 using 陳述式：  
  
    ```  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
2.  在`MenuItemCallback`、 移除方法主體，以及加入這行取得組態設定存放區：  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
    SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> Managed 協助程式類別是透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>服務。  
  
3.  立即找出是否安裝 Windows Phone 工具。 程式碼看起來應該像這樣：  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");  
        string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  測試程式碼。 建置此專案並開始偵錯。  
  
5.  在實驗執行個體，在**工具**功能表上，按一下 **叫用 SettingsStoreCommand**。  
  
     您應該會看到訊息指出**Microsoft Windows Phone Developer Tools:** 後面**True**或**False**。  
  
 Visual Studio 就會在系統登錄中設定存放區。  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>若要使用登錄編輯程式確認組態設定  
  
1.  開啟 Regedit.exe。  
  
2.  瀏覽至 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\。  
  
    > [!NOTE]
    >  請確定您要尋找在索引鍵，其中包含 \14.0Exp_Config\ 和不 \14.0_Config\\。 當您執行 Visual Studio 的實驗執行個體時，組態設定不在 「 14.0Exp_Config"的登錄區中。  
  
3.  展開 \Installed Products\ 節點。 如果在先前步驟中的訊息是**Microsoft Windows Phone 開發人員工具安裝： True**，則 \Installed Products\ 應該包含 Microsoft Windows Phone Developer Tools 節點。 如果訊息為**Microsoft Windows Phone 開發人員工具安裝： False**，然後 \Installed Products\ 不應包含 Microsoft Windows Phone Developer Tools 節點。