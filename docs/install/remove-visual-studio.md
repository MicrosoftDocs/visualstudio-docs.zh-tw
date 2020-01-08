---
title: 移除 Visual Studio
titleSuffix: ''
description: 瞭解如何在您的電腦上逐步完整地移除 Visual Studio。
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fec652e0089a8baae79b6fa9446249710ea2f40d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594509"
---
# <a name="remove-visual-studio"></a>移除 Visual Studio

如果您遇到重大錯誤，且無法修復或卸載 Visual Studio，您可以執行 `InstallCleanup.exe` 工具，以移除所有 Visual Studio 2017 或 Visual Studio 2019 之已安裝實例的安裝檔案和產品資訊。

> [!WARNING]
> 如果修復或卸載失敗，請使用 Installcleanup.exe 工具**作為最後手段**。 此工具可能會將其他 Visual Studio 安裝或其他產品的功能卸載，這可能也需要修復或重新安裝。

## <a name="run-installcleanupexe"></a>執行 Installcleanup.exe

您可以使用下列其中一個命令列參數搭配 `InstallCleanup.exe` 工具：

| 參數 | 行為 |
| ------ | -------- |
| `-i`   | 如果未傳遞其他參數，則此參數為預設值。 它只會移除主要安裝目錄和產品資訊。 如果您想要在執行 `InstallCleanup.exe` 工具之後重新安裝相同版本的 Visual Studio，請使用此參數。 |
| `-f`   | 此參數會移除安裝目錄外部安裝的主要安裝目錄、產品資訊和其他大部分的功能，也可能與其他 Visual Studio 安裝或其他產品共用。 如果您想要移除 Visual Studio，而不需要在稍後重新安裝，請使用此參數。 |

以下是執行 `InstallCleanup.exe` 工具的方法：

1. 關閉 Visual Studio 安裝程式。
1. 開啟系統管理員命令提示字元。 若要開啟系統管理員命令提示字元，請遵循下列步驟：
   * 於 [在這裡輸入要搜尋的文字] 方塊中鍵入 **cmd**。
   * 以右鍵按一下 [命令提示字元]，然後選擇 [以系統管理員身分執行]。
1. 輸入 `InstallCleanup.exe` 工具的完整路徑，並新增您偏好的命令列參數。 根據預設，此工具的路徑如下所示：

   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

   > [!NOTE]
   > 如果您在 [Visual Studio 安裝程式] 目錄下找不到 `InstallCleanup.exe`，這一律位於 `%ProgramFiles(x86)%\Microsoft Visual Studio`，以下是接下來要執行的動作。 依照指示[安裝 Visual Studio](install-visual-studio.md)。 然後，在顯示工作負載選取畫面時，關閉視窗，並再次遵循此頁面上的步驟。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>請參閱

* [安裝 Visual Studio](install-visual-studio.md)
* [更新 Visual Studio](update-visual-studio.md)
* [修改 Visual Studio](modify-visual-studio.md)
* [解除安裝 Visual Studio](uninstall-visual-studio.md)
