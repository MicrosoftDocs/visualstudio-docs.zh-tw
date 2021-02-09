---
title: 針對不屬於 Visual Studio 解決方案的應用程式進行 Debug 錯
titleSuffix: ''
Description: 瞭解如何對不屬於 Visual Studio 解決方案的應用程式進行 debug 錯。 您可能可以附加 Visual Studio 偵錯工具。
ms.custom: SEO-VS-2020
ms.date: 02/21/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3bbe6cac5d74d3767948f0c117539b95cbba570f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913430"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>在 c + +、c #、Visual Basic、F # (的 c + +、c #、、F ) # Visual Studio 的應用程式

您可能會想要對不屬於 Visual Studio 解決方案的 (*.exe* 檔案) 進行偵錯工具的偵錯工具。 它可能是 [開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) 專案，或您或其他人可能已在 Visual Studio 之外建立應用程式，或您從其他位置取得應用程式。

- 針對 Visual Studio (中的開啟資料夾專案) 沒有專案或方案檔，請參閱 [執行和偵錯工具代碼](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) ，或在 c + + 中 [使用 launch.vs.js設定偵錯工具參數](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson)。

- 針對不存在於 Visual Studio 中的應用程式，debug 的一般方式是在 Visual Studio 之外啟動應用程式，然後在 Visual Studio 偵錯工具中使用 [ **附加至進程** ] 附加至該應用程式。 如需詳細資訊，請參閱 [附加至正在](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)執行的進程。

   附加至應用程式需要手動步驟，需要幾秒鐘的時間。 由於此延遲，連接將不會協助您偵測啟動問題，或是不會等待使用者輸入並快速完成的應用程式。

   在這些情況下，您可以為應用程式建立 Visual Studio EXE 專案，或將其匯入至現有的 c #、Visual Basic 或 c + + 方案。 並非所有的程式語言都支援 EXE 專案。

>[!IMPORTANT]
>無論您附加至應用程式或將它新增至 Visual Studio 方案，都不會限制 Visual Studio 內建的應用程式的偵錯工具功能。
>
>如果您有原始程式碼，最好的方法就是將程式碼匯入 Visual Studio 專案。 然後，執行應用程式的偵錯工具組建。
>
>如果您沒有原始程式碼，而且應用程式沒有相容格式的 [debug 資訊](../debugger/how-to-set-debug-and-release-configurations.md) ，可用的偵錯工具很少。

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>為現有的應用程式建立新的 EXE 專案

1. 在 Visual Studio 中，**選取 [** 檔案  >  **開啟**  >  **專案**]。

1. 在 [**開啟專案**] 對話方塊的 [**檔案名**] 旁的下拉式清單中，選取 [**所有專案** 檔] （若尚未選取）。

1. 流覽至 *.exe* 檔案，選取該檔案，然後選取 [ **開啟**]。

   檔案會出現在新的暫時 Visual Studio 方案中。

1. 從 [**調試** 程式] 功能表中選取執行命令，例如 **開始調試** 程式，開始對應用程式進行偵錯工具。

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>將應用程式匯入至現有的 Visual Studio 解決方案

1. 在 Visual Studio 中開啟 c + +、c # 或 Visual Basic 方案，**然後選取 [** 檔案  >  **加入**  >  **現有專案**]。

1. 在 [**開啟專案**] 對話方塊的 [**檔案名**] 旁的下拉式清單中，選取 [**所有專案** 檔] （若尚未選取）。

1. 流覽至 *.exe* 檔案，選取該檔案，然後選取 [ **開啟**]。

   檔案會在目前的方案下顯示為新專案。

1. 選取新檔案之後，請從 [**調試** 程式] 功能表中選取 [執行] 命令（例如 [**開始調試** 程式]），開始對應用程式進行偵錯工具。

### <a name="see-also"></a>另請參閱
- [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)
- [偵錯工具安全性](../debugger/debugger-security.md)
- [DBG 檔案](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))