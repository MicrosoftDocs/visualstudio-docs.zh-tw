---
title: 指定自訂建置事件
description: 瞭解如何在組建開始之前或完成之後，自動在 Visual Studio 中執行命令。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d0728154e21893ac45fc0e17cc3d0407551dbb3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951026"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>在 Visual Studio 中指定自訂建置事件

您可以指定自訂建置事件，在建置開始之前或完成之後自動執行命令。 例如，您可以在組建開始之前執行 *.bat* 檔，或在組建完成後將新檔案複製到資料夾。 只有在建置成功到達建置流程中的這些點時，建置事件才會執行。

如需您所使用之程式設計語言的特定資訊，請參閱下列主題：

- Visual Basic--[如何：指定 (Visual Basic) 的組建事件 ](../ide/how-to-specify-build-events-visual-basic.md)。

- C# 和 F# -- [如何：指定建置事件 (C#)](../ide/how-to-specify-build-events-csharp.md)。

- Visual C++ -- [指定建置事件](/cpp/build/specifying-build-events)。

## <a name="syntax"></a>Syntax

建置事件遵循與 DOS 命令相同的語法，不過您可以使用巨集更輕鬆地建立建置事件。 如需可用宏的清單，請參閱 [預先建立事件/後置事件命令列對話方塊](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)。

為了獲得最佳結果，請依照下列格式秘訣：

- `call`在所有執行 *.bat* 檔案的組建事件之前加入語句。

   範例： `call C:\MyFile.bat`

   範例： `call C:\MyFile.bat call C:\MyFile2.bat`

- 以引號括住檔案路徑。

   範例 (適用於 [!INCLUDE[win8](../debugger/includes/win8_md.md)])：如果是 "$(TargetPath)"，則為 "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe"

- 使用分行符號來分隔多個命令。

- 視需要包含萬用字元。

   範例： `for %I in (*.txt *.doc *.html) do copy %I c:\` *mydirectory*`\`

  > [!NOTE]
  > 在批次指令碼中，上述程式碼中的 `%I` 應該是 `%%I`。

## <a name="see-also"></a>另請參閱

- [編譯和建置](../ide/compiling-and-building-in-visual-studio.md)
- [預先建立事件/後置事件命令列對話方塊](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [MSBuild 特殊字元](../msbuild/msbuild-special-characters.md)
- [逐步解說：建置應用程式](../ide/walkthrough-building-an-application.md)
