---
title: 針對不屬於 Visual Studio 解決方案的應用程式進行 Debug
titleSuffix: ''
ms.custom: ''
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8cb71acb9c1c332f269f77129fa2d11a9a874f8
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350143"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>針對不屬於 Visual Studio 解決方案的應用程式進行 Debug （c + +、c #、Visual Basic、F #）

您可能想要對不屬於 Visual Studio 解決方案的應用程式（*.exe*檔）進行 debug 錯。 它可能是[開啟的資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)專案，或者您或其他人可能已在 Visual Studio 外部建立應用程式，或您從其他地方得到應用程式。

- 若為 Visual Studio 中的開啟資料夾專案（沒有專案或方案檔），請參閱[執行和偵錯工具代碼](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code)，或針對 c + +，[使用 launch.vs.js設定偵錯工具參數](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson)。

- 針對不存在於 Visual Studio 中的應用程式，常見的 debug 方法是在 Visual Studio 外部啟動應用程式，然後在 Visual Studio 偵錯工具中使用 [**附加至進程**] 附加至該應用程式。 如需詳細資訊，請參閱[附加至](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)執行中的進程。

   附加至應用程式需要手動步驟，需要幾秒鐘的時間。 由於此延遲的原因，附加將無法協助您偵測啟動問題，或不會等待使用者輸入並快速完成的應用程式。

   在這些情況下，您可以為應用程式建立 Visual Studio EXE 專案，或將它匯入至現有的 c #、Visual Basic 或 c + + 方案。 並非所有的程式語言都支援 EXE 專案。

>[!IMPORTANT]
>無論您附加至應用程式或將它新增至 Visual Studio 解決方案，應用程式都不 Visual Studio 內建的偵錯工具功能會受到限制。
>
>如果您有原始程式碼，最好的方法是將程式碼匯入 Visual Studio 專案。 然後，執行應用程式的 debug 組建。
>
>如果您沒有原始程式碼，而且應用程式沒有相容格式的[debug 資訊](../debugger/how-to-set-debug-and-release-configurations.md)，可用的調試功能就很少。

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>為現有的應用程式建立新的 EXE 專案

1. 在 Visual Studio 中，**選取 [** 檔案] [  >  **開啟**  >  **專案**]。

1. 在 [**開啟專案**] 對話方塊中，選取 [**所有專案**檔] （如果尚未選取），位於 [**檔案名**] 旁的下拉式清單中。

1. 流覽至 *.exe*檔案，加以選取，然後選取 [**開啟**]。

   檔案會出現在新的暫存 Visual Studio 解決方案中。

1. 從 [**調試**程式] 功能表選取執行命令，例如 [**開始調試**]，開始對應用程式進行偵錯工具。

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>將應用程式匯入現有的 Visual Studio 解決方案

1. 在 Visual Studio 中開啟 c + +、c # 或 Visual Basic 方案，**然後選取 [** 檔案] [新增] [  >  **Add**  >  **現有專案**]。

1. 在 [**開啟專案**] 對話方塊中，選取 [**所有專案**檔] （如果尚未選取），位於 [**檔案名**] 旁的下拉式清單中。

1. 流覽至 *.exe*檔案，加以選取，然後選取 [**開啟**]。

   檔案會在目前的方案下顯示為新專案。

1. 選取新的檔案之後，請從 [**調試**程式] 功能表選取執行命令（例如 [**開始調試**]）來開始偵錯工具。

### <a name="see-also"></a>另請參閱
- [偵錯工具設定和準備](../debugger/debugger-settings-and-preparation.md)
- [偵錯工具安全性](../debugger/debugger-security.md)
- [DBG 檔案](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))