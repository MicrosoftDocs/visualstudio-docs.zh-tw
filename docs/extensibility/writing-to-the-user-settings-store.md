---
title: 寫入使用者設置商店 |微軟文件
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bed721cc084042c3ebe57639af28b7e9f13d206
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740358"
---
# <a name="writing-to-the-user-settings-store"></a>寫入使用者設定存放區
用戶設置是可寫入的設置,如 **「工具/選項**」對話方塊中的設置、屬性視窗和某些其他對話框中的設置。 Visual Studio 擴展可能會使用這些擴展來存儲少量數據。 本演練演示如何通過將讀取和寫入使用者設置存儲,將記事本作為外部工具添加到 Visual Studio。

## <a name="writing-to-the-user-settings-store"></a>寫入使用者設定存放區

1. 創建名為"使用者設定儲存擴展"的 VSIX 專案,然後添加名為"使用者設置儲存命令"的自定義命令。 有關如何建立自訂指令的詳細資訊,請參閱[使用選單命令建立擴展](../extensibility/creating-an-extension-with-a-menu-command.md)

2. 在UserSettingsStoreCommand.cs,添加以下使用指令:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. 在 MenuItem 回檔中,刪除方法的主體並取得使用者設定儲存,如下所示:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. 現在瞭解記事本是否已設置為外部工具。 您需要遍接所有外部工具,以確定 ToolCmd 設定是否為「記事本」,如下所示:

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

5. 如果記事本尚未設定為外部工具,則將其設定為以下方式:

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

6. 測試代碼。 請記住,它添加記事本作為外部工具,因此您必須回滾註冊表,然後再運行它。

7. 生成代碼並開始調試。

8. 在 **「工具」** 選單上,按一下 **「調用使用者設定儲存命令**」 。 這將將記事本添加到 **「工具」** 選單中。

9. 現在,您應該在「工具/選項」功能表上看到記事本,按下**記事本**應顯示記事本的實例。
