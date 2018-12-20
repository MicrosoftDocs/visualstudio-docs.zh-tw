---
title: 指定自訂建置事件
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6c5bde6b6dce7655043f3dc766a5faa81fa944e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055124"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>在 Visual Studio 中指定自訂建置事件

您可以指定自訂建置事件，在建置開始之前或完成之後自動執行命令。 例如，您可以在建置開始之前執行 *.bat* 檔案，或在建置完成之後將新檔案複製到資料夾。 只有在建置成功到達建置流程中的這些點時，建置事件才會執行。

 如需您所使用之程式設計語言的特定資訊，請參閱下列主題：

-   Visual Basic--[如何：指定建置事件 (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)。

-   C# 和 F#--[如何：指定建置事件 (C#)](../ide/how-to-specify-build-events-csharp.md)。

-   Visual C++ -- [指定建置事件](/cpp/ide/specifying-build-events)。

## <a name="syntax"></a>語法

建置事件遵循與 DOS 命令相同的語法，不過您可以使用巨集更輕鬆地建立建置事件。 如需可用巨集的清單，請參閱[建置前事件/建置後事件命令列對話方塊](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)。

 為了獲得最佳結果，請依照下列格式秘訣：

- 在執行 *.bat* 檔案的所有建置事件之前新增 `call` 陳述式。

   範例：`call C:\MyFile.bat`

   範例：`call C:\MyFile.bat call C:\MyFile2.bat`

- 以引號括住檔案路徑。

   範例 (適用於 [!INCLUDE[win8](../debugger/includes/win8_md.md)])：如果是 "$(TargetPath)"，則為 "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe"

- 使用分行符號來分隔多個命令。

- 視需要包含萬用字元。

   範例：`for %I in (*.txt *.doc *.html) do copy %I c:\`<我的目錄>`\`

  > [!NOTE]
  >  在批次指令碼中，上述程式碼中的 `%I` 應該是 `%%I`。

## <a name="see-also"></a>另請參閱

- [編譯和建置](../ide/compiling-and-building-in-visual-studio.md)
- [建置前事件/建置後事件命令列對話方塊](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [MSBuild 特殊字元](../msbuild/msbuild-special-characters.md)
- [逐步解說：建置應用程式](../ide/walkthrough-building-an-application.md)
