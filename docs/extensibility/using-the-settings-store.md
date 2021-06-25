---
title: 使用設定存放區 |Microsoft Docs
description: 瞭解如何從設定設定存放區讀取資料，這是唯讀的 Visual Studio 和 VSPackage 設定。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4d7fff5bc3eeeb3b4515e2e47027f5b88fb7807d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898379"
---
# <a name="using-the-settings-store"></a>使用設定存放區
有兩種設定存放區：

- 設定是唯讀 Visual Studio 和 VSPackage 設定。 Visual Studio 將所有已知 .pkgdef 檔案的設定合併到這個存放區。

- 使用者設定，這是可寫入的設定，例如在 [ **選項** ] 對話方塊中的頁面上顯示的設定、屬性頁，以及某些其他對話方塊。 Visual Studio 擴充功能可能會將這些資料用於少量資料的本機儲存體。

  本逐步解說示範如何從設定存放區讀取資料。 請參閱 [寫入使用者設定存放區](../extensibility/writing-to-the-user-settings-store.md) ，以取得如何寫入使用者設定存放區的說明。

## <a name="creating-the-example-project"></a>建立範例專案
 本節說明如何使用功能表命令來建立簡單的擴充功能專案，以供示範之用。

1. 每個 Visual Studio 擴充功能都會以 VSIX 部署專案開始，其中將包含延伸模組資產。 建立 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 名為的 VSIX 專案 `SettingsStoreExtension` 。 您可以在 [ **新增專案** ] 對話方塊中的 **Visual c #/** 擴充性下找到 VSIX 專案範本。

2. 現在，新增名為 **SettingsStoreCommand** 的自訂命令專案範本。 在 [ **加入新專案** ] 對話方塊中，移至 **Visual c #/** 擴充性，然後選取 [ **自訂命令**]。 在視窗底部的 [ **名稱** ] 欄位中，將命令檔名稱變更為 **SettingsStoreCommand .cs**。 如需如何建立自訂命令的詳細資訊，請參閱[使用功能表命令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能

## <a name="using-the-configuration-settings-store"></a>使用設定存放區
 本節說明如何偵測和顯示設定。

1. 在 SettingsStorageCommand .cs 檔案中，加入下列 using 指示詞：

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. 在中 `MenuItemCallback` ，移除方法的主體，並新增這些行以取得設定存放區：

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager>是服務上的 managed helper 類別 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> 。

3. 現在瞭解是否已安裝 Windows Phone 工具。 程式碼看起來應該像這樣：

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

5. 在實驗性實例中，按一下 [ **工具** ] 功能表上的 [叫用 **SettingsStoreCommand**]。

    您應該會看到一個訊息方塊，指出 **Microsoft Windows Phone 開發人員工具：**  接著是 **True** 或 **False**。

   Visual Studio 將設定存放區保留在系統登錄中。

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>使用登錄編輯程式來確認設定

1. 開啟 Regedit.exe。

2. 流覽至 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\ 。

    > [!NOTE]
    > 確定您正在查看包含 \ 14.0Exp_Config \ 而非 \ 14.0_Config 的索引鍵 \\ 。 當您執行 Visual Studio 的實驗實例時，設定會位於登錄 hive "14.0Exp_Config"。

3. 展開 [\Installed Products] 節點。 如果先前步驟中的訊息是 **已安裝 Microsoft Windows Phone Developer tools： True**，則 \Installed Products \ 應該包含 Microsoft Windows Phone developer tools 節點。 如果訊息是 **Microsoft Windows Phone 開發人員工具已安裝： False**，則 [\Installed 產品] 不應包含 [Microsoft Windows Phone 開發人員工具] 節點。
