---
title: 移除 Visual Studio
titleSuffix: ''
description: 了解如何逐步從您的電腦完全移除 Visual Studio。
ms.date: 03/30/2019
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
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e363065d96169660817a548fb97d39f09cf679c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810386"
---
# <a name="remove-visual-studio"></a>移除 Visual Studio

如果發生重大錯誤，且無法修復或解除安裝 Visual Studio，您可以執行 `InstallCleanup.exe` 工具來移除所有已安裝 Visual Studio 2017 或 Visual Studio 2019 執行個體的安裝檔案與產品資訊。 只有當修復或解除安裝失敗，且要解除安裝其他 Visual Studio 安裝的功能或其他產品可能也需要修復時，才能執行此工具作為最後手段。

在下列指示中，您可以使用具有下列行為的不同命令列參數來執行此工具：

| 參數 | 行為 |
| ------ | -------- |
| `-i`   | 如果未傳遞其他參數，此參數會是預設值，而且只會移除主要安裝目錄和產品資訊。 如果在執行 `InstallCleanup.exe` 工具之後想要重新安裝相同版本，則適合此行為。 |
| `-f`   | 指定此參數會移除主要安裝目錄、產品資訊，以及安裝在安裝目錄外部但可能與其他 Visual Studio 安裝或其他產品共用的大多數其他功能。 如果想要移除 Visual Studio 且稍後不會重新安裝，則適合此行為。 |

1. 關閉 Visual Studio 安裝程式。
2. 開啟系統管理員命令提示字元。 若要開啟系統管理員命令提示字元，請遵循下列步驟：
   * 於 [在這裡輸入要搜尋的文字] 方塊中鍵入 **cmd**。
   * 以滑鼠右鍵按一下 [命令提示字元]，然後按一下 [以系統管理員身分執行]。
3. 輸入 `InstallCleanup.exe` 公用程式的完整路徑，並傳遞您想要的任何命令列參數。 根據預設，公用程式的路徑如下所示：

   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

如果您在 Visual Studio 安裝程式目錄下找不到 `InstallCleanup.exe` (一律位於 `%ProgramFiles(x86)%\Microsoft Visual Studio`)，請遵循指示[安裝 Visual Studio](install-visual-studio.md)，並在工作負載選擇畫面顯示時關閉視窗，並再次執行上述步驟。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](install-visual-studio.md)
* [更新 Visual Studio](update-visual-studio.md)
* [修改 Visual Studio](modify-visual-studio.md)
* [解除安裝 Visual Studio](uninstall-visual-studio.md)
