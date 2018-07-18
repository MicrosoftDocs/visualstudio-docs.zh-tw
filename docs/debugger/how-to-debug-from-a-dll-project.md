---
title: 如何： 從 DLL 專案進行偵錯 |Microsoft 文件
ms.custom: ''
ms.date: 05/24/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63581cee8816e72492a67a0981a9077b9fec2935
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475807"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio"></a>如何： 從 Visual Studio 中的 DLL 專案進行偵錯
若要偵錯 DLL 專案的一種方式為在 DLL 專案的專案屬性中指定呼叫應用程式，然後您可以從開始偵錯 DLL 專案本身。 要執行這個方法，應用程式必須呼叫 DLL，DLL 必須位在應用程式預期可找到的位置和 （否則應用程式可能會找到不同版本的 dll 和載入，而是，它將不會叫用中斷點）。 其他的偵錯 Dll 的方法，請參閱[偵錯 DLL 專案](../debugger/debugging-dll-projects.md)。
  
如果機器碼呼叫了 Managed DLL，且您想要對兩者進行偵錯，可以在專案屬性中指定此項目。 如需詳細資訊，請參閱 [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md)。   

C++ 屬性頁面在配置與內容方面和 C# 及 Visual Basic 的屬性頁面不同。 
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>在 C++ 專案中指定呼叫應用程式  
  
1.  以滑鼠右鍵按一下專案節點中的**方案總管 中**選取**屬性**。  
  
2.  請確定**組態**視窗頂端的欄位設定為**偵錯**。 

    A**偵錯**設定，才能在這個方法。 
  
3.  移至**組態屬性 > 偵錯**。  
  
4.  在**偵錯工具啟動**清單中，選擇**本機 Windows 偵錯工具**或**遠端 Windows 偵錯工具**。  
  
5.  在**命令**或**遠端命令**方塊中，加入呼叫的應用程式 （例如.exe 檔） 的完整路徑名稱。

    ![偵錯屬性 視窗](../debugger/media/dbg-debugging-properties-dll.png "DebuggingPropertiesWindow")  
  
6.  加入任何必要的程式引數**命令引數**方塊。  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>在 C# 或 Visual Basic 專案中指定呼叫應用程式  
  
1.  以滑鼠右鍵按一下專案節點中的**方案總管 中**選取**屬性**，然後選取**偵錯** 索引標籤。

2.  請確定**組態**視窗頂端的欄位設定為**偵錯**。

3.  (.NET framework)選取**啟動外部程式**，並將呼叫的應用程式的完整路徑名稱。

4.  （.NET Core）選取**可執行檔**從**啟動**清單，然後再加入 呼叫的應用程式中的完整路徑名稱**可執行檔**欄位。 
  
     如果您需要加入外部程式的命令列引數，將其加入**命令列引數**(或**應用程式的引數**) 欄位。

    ![偵錯屬性 視窗](../debugger/media/dbg-debugging-properties-dll-csharp.png "DebuggingPropertiesWindow") 

5.  如果需要您也可以呼叫做為 URL 的應用程式。 (若正在偵錯本機 ASP.NET 應用程式所使用之 Managed DLL，進行此動作可能相當有助益。)  
  
     在下**起始動作**，選取**以 URL 啟動瀏覽器：** 選項按鈕並塡入 URL。
  
### <a name="to-start-debugging-from-the-dll-project"></a>從 DLL 專案啟動偵錯  
  
1.  在 DLL 專案中設定中斷點。 

2.  以滑鼠右鍵按一下 DLL 專案，然後選擇 **設定為啟始專案**。 

    (另外，請確定**方案組態**欄位仍會設為**偵錯**。)   
  
3.  開始偵錯 (按 f5 鍵，按一下綠色箭頭，或按一下**偵錯 > 開始偵錯**)。

    您會在 DLL 中達到的中斷點。 如果您不能叫用中斷點，請確定您的 DLL 輸出 (根據預設， **project\Debug**資料夾) 是在位置中呼叫的應用程式預期可找到。
  
## <a name="see-also"></a>另請參閱  
 [偵錯 DLL 專案](../debugger/debugging-dll-projects.md)   
 [C# 偵錯設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 偵錯設定的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [C++ 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)