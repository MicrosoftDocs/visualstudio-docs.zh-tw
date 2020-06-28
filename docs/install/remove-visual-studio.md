---
title: 移除 Visual Studio
titleSuffix: ''
description: 瞭解如何在您的電腦上逐步完整地移除 Visual Studio。
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: how-to
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
ms.openlocfilehash: b26e837ec2c4155c1be0b3639368c4315d2aecd3
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85418921"
---
# <a name="remove-visual-studio"></a>移除 Visual Studio

如果您遇到嚴重錯誤，且無法修復或卸載 Visual Studio，您可以執行 `InstallCleanup.exe` 工具來移除所有已安裝之 Visual Studio 2017 或 Visual Studio 2019 實例的安裝檔案和產品資訊。

> [!WARNING]
> 如果修復或卸載失敗，請使用 Installcleanup.exe 工具**作為最後手段**。 此工具可能會將其他 Visual Studio 安裝或其他產品的功能卸載，這可能也需要修復或重新安裝。

## <a name="run-installcleanupexe"></a>執行 InstallCleanup.exe

您可以使用下列其中一個命令列參數搭配 `InstallCleanup.exe` 工具：

| 參數 | 行為 |
| ------ | -------- |
| `-i`   | 如果未傳遞其他參數，則此參數為預設值。 它只會移除主要安裝目錄和產品資訊。 如果您想要在執行工具之後重新安裝相同版本的 Visual Studio，請使用此參數 `InstallCleanup.exe` 。 |
| `-f`   | 此參數會移除安裝目錄外部安裝的主要安裝目錄、產品資訊和其他大部分的功能，也可能與其他 Visual Studio 安裝或其他產品共用。 如果您想要移除 Visual Studio，而不需要在稍後重新安裝，請使用此參數。 |

以下是執行此工具的方法 `InstallCleanup.exe` ：

1. 關閉 Visual Studio 安裝程式。
1. 開啟系統管理員命令提示字元。 若要開啟系統管理員命令提示字元，請遵循下列步驟：
   * 於 [在這裡輸入要搜尋的文字] 方塊中鍵入 **cmd**。
   * 以右鍵按一下 [命令提示字元]****，然後選擇 [以系統管理員身分執行]****。
1. 輸入工具的完整路徑 `InstallCleanup.exe` ，並新增您偏好的命令列參數。 根據預設，此工具的路徑如下所示。 雙引號括住包含空格的命令：

   ```
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe"
   ```

   > [!NOTE]
   > 如果您 `InstallCleanup.exe` 在 Visual Studio 安裝程式目錄下找不到永遠位於的位置 `%ProgramFiles(x86)%\Microsoft Visual Studio` ，以下是接下來要執行的動作。 依照指示[安裝 Visual Studio](install-visual-studio.md)。 然後，在顯示工作負載選取畫面時，關閉視窗，並再次遵循此頁面上的步驟。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](install-visual-studio.md)
* [更新 Visual Studio 2017](update-visual-studio.md)
* [修改 Visual Studio 2017](modify-visual-studio.md)
* [解除安裝 Visual Studio](uninstall-visual-studio.md)
