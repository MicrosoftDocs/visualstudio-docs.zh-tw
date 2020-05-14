---
title: 使用設定儲存 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3bbc09586f883e067e32f525a0331c1a9e253f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698522"
---
# <a name="using-the-settings-store"></a>使用設定存放區
有兩種類型的設定儲存:

- 配置設置,它們是唯讀的可視化工作室和 VSPackage 設定。 可視化工作室將所有已知的 .pkgdef 檔的設置合併到此存儲中。

- 用戶設置,這些設置是可寫入的設置,例如顯示在 **「選項」** 對話框、屬性頁和某些其他對話框中的頁面上的設置。 Visual Studio 擴展可能使用這些擴展用於本地存儲少量數據。

  本演練演示如何從配置設置存儲中讀取數據。 有關如何[寫入使用者設定儲存的說明,請參閱入使用者設定儲存](../extensibility/writing-to-the-user-settings-store.md)。

## <a name="creating-the-example-project"></a>建立範例項目
 本節演示如何使用功能表命令創建用於演示的簡單擴展專案。

1. 每個 Visual Studio 擴充都從包含擴充資產的 VSIX 部署專案開始。 建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]名為的`SettingsStoreExtension`VSIX 專案。 您可以在**Visual C# / 擴充性**下的 **「新專案**」對話框中找到 VSIX 專案範本。

2. 現在添加名為**SettingsStore 命令 的**自定義命令項範本。 在「**新增新項目」** 對話框中,轉到**可視化 C# / 擴充性**,然後選擇 **「自訂命令**」。 在視窗底部的**名稱「 欄**位中」,將命令檔名變更為**SettingsStoreCommand.cs**。 有關如何建立自訂指令的詳細資訊,請參閱[使用選單命令建立擴展](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>使用設定設定儲存
 本節演示如何檢測和顯示配置設置。

1. 在SettingsStorageCommand.cs檔中,添加以下使用指令:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. 在`MenuItemCallback`中,刪除方法的主體,並添加這些行取得設定設定儲存:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    是<xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager>服務上的<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>託管幫助器類。

3. 現在瞭解是否安裝了 Windows 電話工具。 代碼應如下所示:

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

4. 測試代碼。 建置此專案並開始偵錯。

5. 在實驗實例中,在 **「工具」** 功能表上,按下 **「調用設定存儲命令**」。

    您應該會看到一個消息框,上面寫著**微軟 Windows Phone 開發人員工具:** 後跟 **"真****"或"假**"。

   Visual Studio 將設置存儲在系統註冊表中。

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>使用註冊表編輯器驗證設定設定

1. 開啟 Regedit.exe。

2. 導航到HKEY_CURRENT_USER\軟體\微軟_VisualStudio_14.0Exp_Config\已安裝\\的產品。

    > [!NOTE]
    > 請確保正在查看包含 [14.0Exp_Config] 的密鑰,而不是 [14.0_Config。\\ 運行 Visual Studio 的實驗實例時,配置設置位於註冊表配置單元「14.0Exp_Config」。。

3. 展開 [已安裝的產品] 節點。 如果前面的步驟中的消息是微軟**Windows Phone 開發人員工具安裝:True,** 則 [已安裝的產品] 應包含一個 Microsoft Windows Phone 開發人員工具節點。 如果消息是**微軟 Windows 手機開發人員工具安裝: False**, 則 [已安裝的產品] 不應包含 Microsoft Windows Phone 開發人員工具節點。
