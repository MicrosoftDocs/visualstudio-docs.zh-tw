---
title: 如何： 從 DLL 專案進行偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 61ccfc1fbf97dc36ed0625f95f998f9b154fd68c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796255"
---
# <a name="how-to-debug-from-a-dll-project"></a>How to: Debug from a DLL Project
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要啟動 DLL 專案的偵錯，必須在專案屬性中指定呼叫應用程式。 C++ 屬性頁面在配置與內容方面和 C# 及 Visual Basic 的屬性頁面不同。  
  
 如果機器碼呼叫了 Managed DLL，且您想要對兩者進行偵錯，可以在專案屬性中指定此項目。 如需詳細資訊，請參閱 [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md)。  
  
> [!NOTE]
>  您無法在 Visual Studio 的 Express 版中指定外部呼叫應用程式。 而是需要將可執行的專案加入方案中，並將其設定為啟動專案，並從可執行的專案之 DLL 中呼叫方法。  
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>在 C++ 專案中指定呼叫應用程式  
  
1.  以滑鼠右鍵按一下專案節點，在**方案總管**，然後選取**屬性**。 移至**偵錯** 索引標籤。  
  
2.  請確定**組態**頂端的視窗 欄位設為**偵錯**。  
  
3.  移至**組態屬性 / 偵錯**。  
  
4.  在 **偵錯工具來啟動**清單中，選擇**本機 Windows 偵錯工具**或是**遠端 Windows 偵錯工具**。  
  
5.  在 **命令**或是**遠端命令**方塊中，加入應用程式的完整路徑名稱。  
  
6.  加入任何必要的程式引數**命令列引數** 方塊中。  
  
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
 [偵錯 DLL 專案](../debugger/debugging-dll-projects.md)   
 [C# 偵錯設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 偵錯設定的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [C++ 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)



