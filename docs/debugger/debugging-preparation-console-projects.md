---
title: 準備 debug 主控台專案 |Microsoft Docs
description: '取得有關準備 (c #、c + +、Visual Basic、F # ) Visual Studio 中的主控台專案。'
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e39cb7df53a12b97d297ee739338c42a3201089f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872517"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>調試準備：主控台專案 (c #、c + +、Visual Basic、F # ) 

準備 debug 主控台專案的方式類似于準備錯 Windows 專案，還有一些其他考慮，例如設定命令列引數，以及如何暫停應用程式以進行偵錯工具。 如需詳細資訊，請參閱 < [Windows Forms 應用程式](../debugger/debugging-preparation-windows-forms-applications.md)，和[偵錯準備： Windows Forms 應用程式 (.NET)](/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100))。 由於所有主控台應用程式都有相似性，這個主題的內容會涵蓋下列專案類型：

- C #、Visual Basic 和 F # 主控台應用程式

- C++ 主控台應用程式 (.NET)

- C++ 主控台應用程式 (Win32)

  主控台應用程式使用 [主控台] 視窗接受輸入訊息並顯示輸出訊息。 若要寫入 **主控台** 視窗，您的應用程式必須使用 **主控台** 物件，而不是 Debug 物件。 若要寫入至 [Visual Studio 輸出] 視窗，請與平常一樣使用 Debug 物件。 請您務必知道您的應用程式要寫於何處，否則您可能會在錯誤的地方尋找訊息。 如需詳細資訊，請參閱 [Console 類別](/dotnet/api/system.console)、[Debug 類別](/dotnet/api/system.diagnostics.debug)以及[輸出視窗](../ide/reference/output-window.md)。

## <a name="set-command-line-arguments"></a>設定命令列引數

您可能需要為您的主控台應用程式指定命令列引數。 如需詳細資訊，請參閱 [c + + 偵錯工具的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)、 [Visual Basic 偵錯工具的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)，或 [c # Debug 設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)。

跟所有的專案屬性一樣，這些引數會持續保留於偵錯工作階段和 Visual Studio 工作階段之間。 因此，如果主控台應用程式是您先前曾進行過調試的應用程式，請記住，在 [ **\<Project> 屬性頁**] 對話方塊中輸入的先前會話可能有引數。

## <a name="start-the-application"></a>啟動應用程式

 某些主控台應用程式啟動時，會執行至完成，然後結束。 這種行為可能會讓您沒有足夠的時間中斷執行和進行偵錯。 若要對應用程式進行偵錯，請使用下列其中一項程序啟動應用程式：

- 在您的程式碼中設定中斷點，然後啟動應用程式。

- 使用 **F10** (**調試** 程式來啟動您的應用程式  >  ) 或 **F11** (**調試** 程式  >  **逐步** 執行) ，然後使用其他選項（例如 [**執行**]）流覽程式碼。

- 在 [程式碼編輯器] 中，以滑鼠右鍵按一下行，然後選取 [ **執行至游標處**]。

  對主控台應用程式進行偵錯時，您可能想要從命令提示字元，而不是從 Visual Studio 啟動應用程式。 在這種情況下，您可以從命令提示字元啟動應用程式並且將 Visual Studio 偵錯工具附加至其中。 如需詳細資訊，請參閱 [附加至正在](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)執行的進程。

  當您從 Visual Studio 啟動主控台應用程式時，[主控台] 視窗有時候會出現在 Visual Studio 視窗後面。 如果您嘗試從 Visual Studio 啟動主控台應用程式而且似乎沒有回應，請嘗試移動 Visual Studio 視窗。

## <a name="see-also"></a>另請參閱
- [偵錯機器碼](../debugger/debugging-native-code.md)
- [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)
- [準備 debug c + + 專案](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#、F# 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [C + + 偵錯工具設定的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [偵錯工具安全性](../debugger/debugger-security.md)