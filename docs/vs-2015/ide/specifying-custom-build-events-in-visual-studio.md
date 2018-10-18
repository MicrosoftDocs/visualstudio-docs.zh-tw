---
title: 在 Visual Studio 中指定自訂建置事件 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fcda3d11f080f0d013eb5305c9138e7764e1436b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263941"
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>在 Visual Studio 中指定自訂建置事件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以指定自訂建置事件，在建置開始之前或完成之後自動執行命令。 例如，您可以在建置開始之前執行 .bat 檔案，或在建置完成之後將新檔案複製到資料夾。 只有在建置成功到達建置流程中的這些點時，建置事件才會執行。  
  
 如需您所使用之程式設計語言的特定資訊，請參閱下列主題：  
  
-   Visual Basic -- [如何：指定建置事件 (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)。  
  
-   Visual C# 和 F# -- [如何：指定建置事件 (C#)](../ide/how-to-specify-build-events-csharp.md)。  
  
-   Visual C++ -- [指定建置事件](http://msdn.microsoft.com/library/788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc)。  
  
## <a name="syntax"></a>語法  
 建置事件遵循與 DOS 命令相同的語法，不過您可以使用巨集更輕鬆地建立建置事件。 如需可用巨集的清單，請參閱[建置前事件/建置後事件命令列對話方塊](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)。  
  
 為了獲得最佳結果，請依照下列格式秘訣：  
  
-   在執行 .bat 檔案的所有建置事件之前加入 `call` 陳述式。  
  
     範例：`call C:\MyFile.bat`  
  
     範例：`call C:\MyFile.bat call C:\MyFile2.bat`  
  
-   以引號括住檔案路徑。  
  
     範例 (適用於 [!INCLUDE[win8](../includes/win8-md.md)])：如果是 "$(TargetPath)"，則為 "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe"  
  
-   使用分行符號來分隔多個命令。  
  
-   視需要包含萬用字元。  
  
     範例：`for %I in (*.txt *.doc *.html) do copy %I c:\`<我的目錄>`\`  
  
    > [!NOTE]
    >  在批次指令碼中，上述程式碼中的 `%I` 應該是 `%%I`。  
  
## <a name="see-also"></a>另請參閱  
 [編譯和建置](../ide/compiling-and-building-in-visual-studio.md)   
 [建置前事件/建置後事件命令列對話方塊](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [MSBuild 特殊字元](../msbuild/msbuild-special-characters.md)   
 [逐步解說：建置應用程式](../ide/walkthrough-building-an-application.md)



