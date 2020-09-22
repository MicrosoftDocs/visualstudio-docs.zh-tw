---
title: 如何：從 DLL 專案進行調試 |Microsoft Docs
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
ms.openlocfilehash: 6496d38e753d2338966916d1d7855abca77ace34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839104"
---
# <a name="how-to-debug-from-a-dll-project"></a>How to: Debug from a DLL Project
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要啟動 DLL 專案的偵錯，必須在專案屬性中指定呼叫應用程式。 C++ 屬性頁面在配置與內容方面和 C# 及 Visual Basic 的屬性頁面不同。  
  
 如果機器碼呼叫了 Managed DLL，且您想要對兩者進行偵錯，可以在專案屬性中指定此項目。 如需詳細資訊，請參閱 [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md)。  
  
> [!NOTE]
> 您無法在 Visual Studio 的 Express 版中指定外部呼叫應用程式。 而是需要將可執行的專案加入方案中，並將其設定為啟動專案，並從可執行的專案之 DLL 中呼叫方法。  
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>在 C++ 專案中指定呼叫應用程式  
  
1. 以滑鼠右鍵按一下 **方案總管** 中的專案節點，然後選取 [ **屬性**]。 移至 [ **調試** ] 索引標籤。  
  
2. 請確定視窗頂端的 [組態]**** 欄位已設定為 [偵錯]****。  
  
3. 移至設定 **屬性/調試**。  
  
4. 在 [ **要啟動的偵錯工具** ] 清單中選擇 [ **本機 windows 調試** 程式] 或 [ **遠端 windows 偵錯工具**]。  
  
5. 在 [ **命令** ] 或 [ **遠端命令** ] 方塊中，加入應用程式的完整路徑名稱。  
  
6. 在 [命令引數]**** 方塊中，新增必要的程式引數。  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>在 C# 或 Visual Basic 專案中指定呼叫應用程式  
  
1. 以滑鼠右鍵按一下 **方案總管** 中的專案節點，然後選取 [ **屬性**]。 移至 [ **調試** ] 索引標籤。  
  
     選取 [ **啟動外部程式**]，然後加入要執行之程式的完整路徑名稱。  
  
     如果您需要加入外部程式的命令列引數，請在 [ **命令列引數** ] 欄位中加入這些引數。  
  
2. 您也可以將應用程式呼叫為 URL。 (若正在偵錯本機 ASP.NET 應用程式所使用之 Managed DLL，進行此動作可能相當有助益。)  
  
     在 [ **起始動作**] 底下，選取 [ **在 url 中啟動瀏覽器：** ] 選項按鈕，然後填入 url。  
  
### <a name="to-start-debugging-from-the-dll-project"></a>從 DLL 專案啟動偵錯  
  
1. 視需要設定中斷點。  
  
2. 開始調試 (按下 F5 鍵，按一下綠色箭號，或按一下 [ **Debug/開始調試** ]) 。  
  
## <a name="see-also"></a>另請參閱  
 [調試 DLL 專案](../debugger/debugging-dll-projects.md)   
 [C # Debug 設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic Debug 設定的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [C++ 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)
