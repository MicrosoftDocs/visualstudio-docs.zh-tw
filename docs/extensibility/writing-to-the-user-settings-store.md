---
title: 寫入使用者設定存放區 |Microsoft Docs
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe8187fe11f4818433aed847a7bc67d4a889ad3a
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206888"
---
# <a name="writing-to-the-user-settings-store"></a>寫入使用者設定存放區
使用者設定為可寫入的設定，在像是**工具 / 選項**對話方塊中，屬性 視窗中，然後某些其他對話方塊。 Visual Studio 擴充功能可能會使用這些來儲存少量資料。 本逐步解說示範如何將 「 記事本 」 加入 Visual Studio 是以外部工具讀取和寫入使用者設定存放區。

## <a name="writing-to-the-user-settings-store"></a>寫入使用者設定存放區

1. 建立名為 UserSettingsStoreExtension VSIX 專案，然後新增名為 UserSettingsStoreCommand 的自訂命令。 如需如何建立自訂命令的詳細資訊，請參閱[建立擴充的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)

2. 在 UserSettingsStoreCommand.cs，新增下列 using 陳述式：

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. 在 MenuItemCallback，刪除方法的主體和取得的使用者設定儲存，，如下所示：

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. 現在找出 「 記事本 」 是否已設為 外部工具。 您必須逐一查看所有外部的工具，來判斷是否 ToolCmd 設定"Notepad"，如下所示：

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

5. 如果尚未設定為 外部工具 記事本，請依下列方式設定：

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

6. 測試程式碼。 請記住它做為外部工具，將 [記事本]，所以您必須回復登錄第二次執行之前。

7. 建置程式碼，並開始偵錯。

8. 在 **工具**功能表上，按一下**叫用 UserSettingsStoreCommand**。 這會新增 [記事本] 來**工具**功能表。

9. 現在您應該會看到 [記事本] 在 [工具] / [選項] 功能表，然後按一下**記事本**應該會顯示在 [記事本] 的執行個體。