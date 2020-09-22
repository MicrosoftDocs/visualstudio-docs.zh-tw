---
title: 寫入使用者設定存放區 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 764d9b81297c6bbefd1f5fdf7c77e4d514bb5045
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839118"
---
# <a name="writing-to-the-user-settings-store"></a>寫入使用者設定存放區
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用者設定是可寫入的設定，例如 [ **工具/選項** ] 對話方塊、[屬性] 視窗和某些其他對話方塊中的設定。 Visual Studio 擴充功能可能會使用這些資料來儲存少量的資料。 本逐步解說將示範如何在使用者設定存放區中讀取和寫入，以將 [記事本] 新增至 Visual Studio 作為外部工具。  
  
### <a name="backing-up-your-user-settings"></a>備份您的使用者設定  
  
1. 您必須能夠重設外部工具設定，以便您可以進行 debug 和重複程式。 若要這樣做，您必須儲存原始設定，讓您可以視需要還原它們。  
  
2. 開啟 Regedit.exe。  
  
3. 流覽至 HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0Exp\External 工具] \\ 。  
  
    > [!NOTE]
    > 確定您正在查看包含 \14.0Exp\ 的索引鍵，而不是 \ 14.0 \\ 。 當您執行 Visual Studio 的實驗實例時，您的使用者設定會位於登錄 hive "14.0 Exp" 中。  
  
4. 以滑鼠右鍵按一下 [\External Tools] \ 子機碼，然後按一下 [ **匯出**]。 請確定選取的是選取的 **分支** 。  
  
5. 儲存產生的外部工具 .reg 檔案。  
  
6. 稍後，當您想要重設外部工具設定時，請選取 HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0Exp\External Tools] 登錄機碼，然後按一下內容功能表上的 [ **刪除** ]。  
  
7. 出現 [ **確認金鑰刪除** ] 對話方塊時，按一下 [ **是**]。  
  
8. 以滑鼠右鍵按一下您稍早儲存的 External Tools .reg 檔案，按一下 [ **開啟檔案**]，然後按一下 [ **登錄編輯程式**]。  
  
## <a name="writing-to-the-user-settings-store"></a>寫入使用者設定存放區  
  
1. 建立名為 UserSettingsStoreExtension 的 VSIX 專案，然後加入名為 UserSettingsStoreCommand 的自訂命令。 如需如何建立自訂命令的詳細資訊，請參閱[使用功能表命令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能  
  
2. 在 UserSettingsStoreCommand.cs 中，新增下列 using 語句：  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3. 在 MenuItemCallback 中，刪除方法的主體並取得使用者設定存放區，如下所示：  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4. 現在瞭解記事本是否已設定為外部工具。 您必須逐一查看所有外部工具，以判斷 ToolCmd 設定是否為「記事本」，如下所示：  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already an External Tool.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
    }  
  
    ```  
  
5. 如果 [記事本] 尚未設定為外部工具，請依照下列方式設定：  
  
    ```vb  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already installed.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
  
        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";  
         if (!hasNotepad)  
        {  
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");  
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");  
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");  
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");  
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");  
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);  
  
            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);  
        }  
    }  
    ```  
  
6. 測試程式碼。 請記住，它會將 [記事本] 新增為外部工具，因此您必須先復原登錄，再執行第二次。  
  
7. 建立程式碼並開始進行偵錯工具。  
  
8. 按一下 [ **工具** ] 功能表上的 [叫用 **UserSettingsStoreCommand**]。 這會將 [記事本] 新增至 [ **工具** ] 功能表。  
  
9. 現在您應該會在 [工具]/[選項] 功能表上看到 [記事本]，而按一下 [ **記事本** ] 應該會顯示 [記事本] 實例。
