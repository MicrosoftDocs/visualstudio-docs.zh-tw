---
title: 寫入使用者設定存放區 |Microsoft Docs
description: 瞭解如何使用本逐步解說，以外部工具的形式讀取和寫入使用者設定存放區，以將 [記事本] 新增至 Visual Studio。
ms.custom: SEO-VS-2020
ms.date: 05/23/2019
ms.topic: how-to
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ff3fa6f061f894abce17d2e6c58bfb791740a90
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061767"
---
# <a name="writing-to-the-user-settings-store"></a>寫入使用者設定存放區
使用者設定是可寫入的設定，例如 [ **工具/選項** ] 對話方塊、[屬性] 視窗和某些其他對話方塊中的設定。 Visual Studio 擴充功能可能會使用這些資料來儲存少量的資料。 本逐步解說將示範如何在使用者設定存放區中讀取和寫入，以將 [記事本] 新增至 Visual Studio 作為外部工具。

## <a name="writing-to-the-user-settings-store"></a>寫入使用者設定存放區

1. 建立名為 UserSettingsStoreExtension 的 VSIX 專案，然後加入名為 UserSettingsStoreCommand 的自訂命令。 如需如何建立自訂命令的詳細資訊，請參閱[使用功能表命令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能

2. 在 UserSettingsStoreCommand 中，新增下列 using 指示詞：

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
