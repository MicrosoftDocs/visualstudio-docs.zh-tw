---
title: 使用設定存放區 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9c42835e720fd3c33e53d862192e3e2863a4423
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632603"
---
# <a name="using-the-settings-store"></a>使用設定存放區
有兩種設定存放區：

- [設定]，這是唯讀的 Visual Studio 和 VSPackage 設定。 Visual Studio 將所有已知 .pkgdef 檔案中的設定合併到此存放區。

- 使用者設定，這是可寫入的設定，例如顯示在 [**選項**] 對話方塊、屬性頁和特定其他對話方塊的頁面上。 Visual Studio 延伸模組可能會使用這些擴充功能來儲存少量資料的本機儲存體。

  本逐步解說說明如何從設定存放區讀取資料。 如需如何寫入使用者設定存放區的說明，請參閱[寫入使用者設定存放區](../extensibility/writing-to-the-user-settings-store.md)。

## <a name="creating-the-example-project"></a>建立範例專案
 本節說明如何使用功能表命令來建立簡單的擴充功能專案以供示範。

1. 每個 Visual Studio 延伸模組會以包含擴充功能資產的 VSIX 部署專案開始。 建立名為 `SettingsStoreExtension` 的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX 專案。 您可以在 [**新增專案**] 對話方塊中的 [**視覺C# /** 擴充性] 下找到 VSIX 專案範本。

2. 現在，新增名為**SettingsStoreCommand**的自訂命令專案範本。 在 [**新增專案**] 對話方塊中，移至 [**視覺效果C# /** 擴充性]，然後選取 [**自訂命令**]。 在視窗底部的 [**名稱**] 欄位中，將命令檔名稱變更為**SettingsStoreCommand.cs**。 如需如何建立自訂命令的詳細資訊，請參閱[使用功能表命令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能

## <a name="using-the-configuration-settings-store"></a>使用 Configuration Settings Store
 本節說明如何偵測和顯示設定。

1. 在 SettingsStorageCommand.cs 檔案中，新增下列 using 指示詞：

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. 在 `MenuItemCallback` 中，移除方法的主體，並新增下列幾行取得設定存放區：

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    @No__t_0 是透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> 服務的受控協助程式類別。

3. 現在找出是否已安裝 Windows Phone 工具。 程式碼看起來應該像這樣：

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

4. 測試程式碼。 建置此專案並開始偵錯。

5. 在實驗實例中，按一下 [**工具**] 功能表上的 [叫用**SettingsStoreCommand**]。

    您應該會看到一個訊息方塊，指出**Microsoft Windows Phone 開發人員工具：** 後面接著**True**或**False**。

   Visual Studio 會將設定存放區保留在系統登錄中。

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>若要使用登錄編輯程式來驗證設定

1. 開啟 Regedit.exe。

2. 流覽至 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts \\。

    > [!NOTE]
    > 請確定您查看的是包含 \14.0Exp_Config\ 的機碼，而不是 \14.0_Config \\。 當您執行 Visual Studio 的實驗實例時，configuration 設定會在登錄 hive "14.0 Exp_Config" 中。

3. 展開 [\Installed Products \] 節點。 如果上述步驟中的訊息是**Microsoft Windows Phone 開發人員工具已安裝： True**，然後 \Installed Products \ 應該包含 Microsoft Windows Phone developer tools 節點。 如果訊息是**Microsoft Windows Phone 開發人員工具已安裝： False**，則 [\Installed Products] \ 不應包含 [Microsoft Windows Phone 開發人員工具] 節點。
