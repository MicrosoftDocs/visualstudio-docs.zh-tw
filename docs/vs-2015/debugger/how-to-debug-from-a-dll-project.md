---
title: HOW TO：從 DLL 專案進行偵錯 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4a9a3e7cd63e5a485063789d9f9eeaf1227d1b5d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943062"
---
# <a name="how-to-debug-from-a-dll-project"></a>HOW TO：從 DLL 專案進行偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要啟動 DLL 專案的偵錯，必須在專案屬性中指定呼叫應用程式。 C++ 屬性頁面在配置與內容方面和 C# 及 Visual Basic 的屬性頁面不同。  
  
 如果機器碼呼叫了 Managed DLL，且您想要對兩者進行偵錯，可以在專案屬性中指定此項目。 如需詳細資訊，請參閱[如何：在混合模式偵錯](../debugger/how-to-debug-in-mixed-mode.md)。  
  
> [!NOTE]
>  您無法在 Visual Studio 的 Express 版中指定外部呼叫應用程式。 而是需要將可執行的專案加入方案中，並將其設定為啟動專案，並從可執行的專案之 DLL 中呼叫方法。  
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>在 C++ 專案中指定呼叫應用程式  
  
1.  以滑鼠右鍵按一下專案節點，在**方案總管**，然後選取**屬性**。 移至**偵錯** 索引標籤。  
  
2.  請確定視窗頂端的 [組態] 欄位已設定為 [偵錯]。  
  
3.  移至**組態屬性 / 偵錯**。  
  
4.  在 **偵錯工具來啟動**清單中，選擇**本機 Windows 偵錯工具**或是**遠端 Windows 偵錯工具**。  
  
5.  在 **命令**或是**遠端命令**方塊中，加入應用程式的完整路徑名稱。  
  
6.  在 [命令引數] 方塊中，新增必要的程式引數。  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>在 C# 或 Visual Basic 專案中指定呼叫應用程式  
  
1.  以滑鼠右鍵按一下專案節點，在**方案總管**，然後選取**屬性**。 移至**偵錯** 索引標籤。  
  
     選取 **啟動外部程式**，並加入要執行的程式的完整路徑名稱。  
  
     如果您需要新增外部程式的命令列引數，將其加入**命令列引數**欄位。  
  
2.  您也可以將應用程式呼叫為 URL。 (若正在偵錯本機 ASP.NET 應用程式所使用之 Managed DLL，進行此動作可能相當有助益。)  
  
     底下**起始動作**，選取**瀏覽器起始 URL:** 選項按鈕並塡入 URL。  
  
### <a name="to-start-debugging-from-the-dll-project"></a>從 DLL 專案啟動偵錯  
  
1.  視需要設定中斷點。  
  
2.  開始偵錯 (按下 f5 鍵，按一下綠色箭號，或按一下**偵錯] / [開始偵錯**)。  
  
## <a name="see-also"></a>另請參閱  
 [對 DLL 專案進行偵錯](../debugger/debugging-dll-projects.md)   
 [C# 偵錯設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 偵錯設定的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [C++ 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)
