---
title: 偵錯準備： 主控台專案 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfaf36da772165a4f35e984dff117c6ec41ca60f
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39150947"
---
# <a name="debugging-preparation-console-projects"></a>偵錯準備：主控台專案
準備偵錯主控台專案與準備偵錯 Windows 專案類似，只需進行一些額外考量。 如需詳細資訊，請參閱 < [Windows Forms 應用程式](../debugger/debugging-preparation-windows-forms-applications.md)，並[偵錯準備： Windows Forms 應用程式 (.NET)](http://msdn.microsoft.com/en-us/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5)。 由於所有主控台應用程式都有相似性，這個主題的內容會涵蓋下列專案類型：  
  
-   C# 主控台應用程式  
  
-   Visual Basic 主控台應用程式  
  
-   C++ 主控台應用程式 (.NET)  
  
-   C++ 主控台應用程式 (Win32)  
  
 您可能需要為您的主控台應用程式指定命令列引數。 如需詳細資訊，請參閱 < [c + + 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)， [Visual Basic 偵錯組態的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)，或[C# 偵錯組態的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
 跟所有的專案屬性一樣，這些引數會持續保留於偵錯工作階段和 Visual Studio 工作階段之間。 因此，如果您先前已經偵錯的其中一個主控台應用程式，請記住，可能是從先前工作階段的引數**\<專案 > 屬性頁** 對話方塊。  
  
 主控台應用程式使用**主控台**視窗接受輸入，並顯示輸出訊息。 要寫入**主控台** 視窗中，您的應用程式必須使用**主控台**物件而不是偵錯物件。 要寫入**Visual Studio [輸出**] 視窗中，如往常般使用偵錯物件。 請您務必知道您的應用程式要寫於何處，否則您可能會在錯誤的地方尋找訊息。 如需詳細資訊，請參閱 < [Console 類別](/dotnet/api/system.console)，[偵錯類別](/dotnet/api/system.diagnostics.debug)，並[輸出視窗](../ide/reference/output-window.md)。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 某些主控台應用程式啟動時，會執行至完成，然後結束。 這種行為可能會讓您沒有足夠的時間中斷執行和進行偵錯。 若要對應用程式進行偵錯，請使用下列其中一項程序啟動應用程式：  
  
-   您的應用程式開始執行，並執行，直到它到達中斷點。  
  
-   應用程式會啟動，並且在原始程式碼的第一行立即中斷。  
  
-   在來源的程式碼視窗中，以滑鼠右鍵按一下線條，然後選取**執行至游標處**。  
  
     應用程式會啟動並執行至選取的程式行，或者至中斷點 (如果在該程式行之前遇到中斷點)。  
  
 對主控台應用程式進行偵錯時，您可能想要從命令提示字元，而不是從 Visual Studio 啟動應用程式。 在這種情況下，您可以從命令提示字元啟動應用程式並且將 Visual Studio 偵錯工具附加至其中。 如需詳細資訊，請參閱 <<c0> [ 附加至執行的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
 當您從 Visual Studio 啟動主控台應用程式時**主控台**視窗有時候會出現在 Visual Studio 視窗後面。 如果您嘗試從 Visual Studio 啟動主控台應用程式而且似乎沒有回應，請嘗試移動 Visual Studio 視窗。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯機器碼](../debugger/debugging-native-code.md)   
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)   
 [Visual C++ 專案類型](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#、F# 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C + + 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)