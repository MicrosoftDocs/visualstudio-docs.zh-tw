---
title: 從 DLL 專案進行 Debug |Microsoft 檔
description: 您可以在專案屬性中指定呼叫應用程式，以開始從專案本身進行 DLL 專案的偵錯工具。 如需詳細資訊，請參閱本文。
ms.custom: SEO-VS-2020
ms.date: 10/10/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f6063c5a0343951bb098c6937ce13dac7100d4a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160430"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>如何：在 Visual Studio 中從 DLL 專案進行調試 (c #、c + +、Visual Basic、F # ) 

調試 DLL 專案的其中一種方式是在 DLL 專案屬性中指定呼叫應用程式。 然後，您可以從 DLL 專案本身開始進行調試。 若要讓此方法運作，應用程式必須在與您所設定相同的位置中呼叫相同的 DLL。 如果應用程式找到並載入不同版本的 DLL，該版本將不會包含您的中斷點。 如需偵錯工具 Dll 的其他方法，請參閱 [偵錯工具 dll 專案](../debugger/debugging-dll-projects.md)。

如果您的受控應用程式呼叫原生 DLL，或您的原生應用程式呼叫 managed DLL，您可以同時進行 DLL 和呼叫應用程式的偵錯工具。 如需詳細資訊，請參閱 [如何：在混合模式中進行 Debug](../debugger/how-to-debug-in-mixed-mode.md)。

原生和 managed DLL 專案具有不同的設定，可指定呼叫的應用程式。

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>在原生 DLL 專案中指定呼叫應用程式

1. 在 [ **方案瀏覽器**] 中選取 c + + DLL 專案。 選取 [**屬性**] 圖示，按下 **Alt** + **鍵**，或按一下滑鼠右鍵並選擇 [**屬性**]。

1. 在 [ **\<Project> 屬性頁**] 對話方塊中，請確定視窗頂端 **的 [設定**] 欄位設定為 [ **Debug**]。

1. 選取設定 **屬性**  >  的 **調試**。

1. 在 [ **要啟動的偵錯工具** ] 清單中，選擇 [ **本機 windows 偵錯工具** ] 或 [ **遠端 windows 偵錯工具**]。

1. 在 [ **命令** ] 或 [ **遠端命令** ] 方塊中，新增呼叫應用程式的完整路徑和檔案名，例如 *.exe* 檔。

   ![調試屬性視窗](../debugger/media/dbg-debugging-properties-dll.png "調試屬性視窗")

1. 在 [命令引數] 方塊中，新增必要的程式引數。

1. 選取 [確定]。

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>在 managed DLL 專案中指定呼叫應用程式

1. 在 [ **方案瀏覽器**] 中，選取 c # 或 VISUAL Basic DLL 專案。 選取 [**屬性**] 圖示，按下 **Alt** + **鍵**，或按一下滑鼠右鍵並選擇 [**屬性**]。

1. 請確定視窗頂端的 [組態] 欄位已設定為 [偵錯]。

1. 在 [ **起始動作**] 底下：

   - 針對 .NET Framework Dll，請選取 [ **啟動外部程式**]，然後新增呼叫應用程式的完整路徑和名稱。

   - 或者，選取 [ **使用 Url 啟動瀏覽器** ]，並填入本機 ASP.NET 應用程式的 url。

   - 若是 .NET Core Dll，[ **調試** 程式屬性] 頁面是不同的。 從 [**啟動**] 下拉式清單中選取 [**可執行檔**]，然後在 [**可執行檔**] 欄位中加入呼叫應用程式的完整路徑和名稱。

1. 在 [ **命令列引數** ] 或 [ **應用程式引數** ] 欄位中，新增任何必要的命令列引數。

   ![C # 調試屬性視窗](../debugger/media/dbg-debugging-properties-dll-csharp.png "C # 調試屬性視窗")

1. 使用 **[** 檔案  >  **儲存選取專案**] 或 [ **Ctrl** + **S** ] 儲存變更。

## <a name="debug-from-the-dll-project"></a>從 DLL 專案進行調試

1. 設定 DLL 專案中的中斷點。

1. 以滑鼠右鍵按一下 DLL 專案，然後選擇 [ **設定為啟始專案**]。

1. 請確定 [ **方案** 設定] 欄位設定為 [ **Debug**]。 按下 **F5** 鍵，按一下綠色的 [**開始**] 箭號，或選取 [ **Debug**  >  **開始調試**]。

如果偵錯工具未叫用中斷點，請確定您的 DLL 輸出 (預設， *\<project> \Debug* 資料夾) 是呼叫應用程式呼叫的位置。

## <a name="see-also"></a>另請參閱
- [調試 DLL 專案](../debugger/debugging-dll-projects.md)
- [C# 偵錯組態的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 偵錯組態的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [C++ 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)
