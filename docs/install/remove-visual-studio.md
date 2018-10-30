---
title: 移除 Visual Studio 2017 | Microsoft Docs
description: 了解如何逐步從您的電腦完全移除 Visual Studio。
ms.custom: ''
ms.date: 09/12/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
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
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e72482dce3df2ceaa5d5131838ce08b13a05cd90
ms.sourcegitcommit: c5e72875206b8c5737c29d5b1ec7b86eec747303
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49382762"
---
# <a name="remove-visual-studio"></a>移除 Visual Studio

如果您遇到重大錯誤，且無法修復或解除安裝 Visual Studio，您可以執行 `InstallCleanup.exe` 工具來針對已安裝的所有 Visual Studio 2017 (與更新版本) 執行個體移除安裝檔案與產品資訊。 執行此工具只可作為修復或解除安裝失敗時的最後手段，而且可能將其他 Visual Studio 安裝或其他需要修復之產品中的功能解除安裝。

在下列指示中，您可以透過具有下列行為的不同命令列參數來執行此工具：

| 參數 | 行為 |
| ------ | -------- |
| `-i`   | 如果未傳遞其他參數，此參數會是預設值，而且只會移除主要安裝目錄和產品資訊。 如果在執行 `InstallCleanup.exe` 工具之後想要重新安裝相同版本，則適合此行為。 |
| `-f`   | 指定此參數會移除主要安裝目錄、產品資訊，以及安裝在安裝目錄外部但可能與其他 Visual Studio 安裝或其他產品共用的大多數其他功能。 如果想要移除 Visual Studio 且稍後不會重新安裝，則適合此行為。 |

1. 關閉 Visual Studio 安裝程式。
2. 開啟系統管理員命令提示字元。 若要開啟系統管理員命令提示字元，請遵循下列步驟：
   * 按一下 [開始]**** 功能表
   * 輸入 **cmd**。
   * 以滑鼠右鍵按一下 [命令提示字元]****，然後按一下 [以系統管理員身分執行]****。
3. 輸入 `InstallCleanup.exe` 公用程式的完整路徑，並傳遞您想要的任何命令列參數。 根據預設，公用程式的路徑如下所示：
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

如果您在 Visual Studio 安裝程式目錄下找不到 `InstallCleanup.exe` (一律位於 `%ProgramFiles(x86)%\Microsoft Visual Studio`)，請遵循指示[安裝 Visual Studio](install-visual-studio.md)，並在工作負載選擇畫面顯示時關閉視窗，並再次執行上述步驟。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio 2017](install-visual-studio.md)
* [更新 Visual Studio 2017](update-visual-studio.md)
* [修改 Visual Studio 2017](modify-visual-studio.md)
* [解除安裝 Visual Studio 2017](uninstall-visual-studio.md)
