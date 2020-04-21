---
title: 移除 Visual Studio
titleSuffix: ''
description: 瞭解如何逐步從計算機中完全刪除 Visual Studio。
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 98886df1c7fb09fa30d5c54abe19452780195b6a
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649201"
---
# <a name="remove-visual-studio"></a>移除 Visual Studio

如果您遇到災難性錯誤,無法修復或卸載 Visual Studio,則`InstallCleanup.exe`可以運行 該工具,以刪除 Visual Studio 2017 或 Visual Studio 2019 的所有已安裝實例的安裝檔和產品資訊。

> [!WARNING]
> 如果維修或卸載失敗,僅將"安裝清理"工具**作為最後手段**使用。 此工具可能會從其他 Visual Studio 安裝或其他產品卸載功能,然後可能需要修復或重新安裝這些功能。

## <a name="run-installcleanupexe"></a>執行安裝清理.exe

您可以將以下指令列交換機之一`InstallCleanup.exe`用於該工具:

| Switch | 行為 |
| ------ | -------- |
| `-i`   | 如果未傳遞其他交換機,則此開關為預設值。 它僅刪除主安裝目錄和產品資訊。 如果要在運行該工具後重新安裝同一版本的 Visual Studio,`InstallCleanup.exe`請使用此開關。 |
| `-f`   | 此開關刪除主安裝目錄、產品資訊以及安裝在安裝目錄之外的大多數其他功能,這些功能也可能與其他 Visual Studio 安裝或其他產品共用。 如果要刪除 Visual Studio 而不稍後重新安裝,請使用此開關。 |

以下是執行`InstallCleanup.exe`該工具的方式:

1. 關閉 Visual Studio 安裝程式。
1. 開啟系統管理員命令提示字元。 若要開啟系統管理員命令提示字元，請遵循下列步驟：
   * 於 [在這裡輸入要搜尋的文字] 方塊中鍵入 **cmd**。
   * 以右鍵按一下 [命令提示字元]****，然後選擇 [以系統管理員身分執行]****。
1. 輸入`InstallCleanup.exe`工具的完整路徑並添加您喜歡的命令列開關。 默認情況下,工具的路徑如下所示。 雙引號包含包含空白的指令:

   ```
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe"
   ```

   > [!NOTE]
   > 如果在"視覺工作室安裝程式"`InstallCleanup.exe`目錄下找不到,該目錄始終`%ProgramFiles(x86)%\Microsoft Visual Studio`位於 中,下面是下一步操作。 以說明[安裝視覺工作室](install-visual-studio.md)。 然後,當顯示工作負載選擇螢幕時,關閉視窗並再次按照此頁面上的步驟操作。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](install-visual-studio.md)
* [更新 Visual Studio 2017](update-visual-studio.md)
* [修改 Visual Studio 2017](modify-visual-studio.md)
* [解除安裝 Visual Studio](uninstall-visual-studio.md)
