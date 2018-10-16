---
title: 如何： 從 DLL 專案進行偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2018
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
ms.openlocfilehash: b7b38ac26a07965dc5408c1da1c655a010b6a788
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266184"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio"></a>如何： 從 DLL 專案在 Visual Studio 中偵錯

偵錯 DLL 專案的一個方法是在 DLL 專案屬性中指定呼叫端的應用程式。 然後您可以從開始偵錯 DLL 專案本身。 此方法才能運作，應用程式必須在相同的位置，與您設定的一個呼叫相同 DLL。 如果應用程式會尋找並載入 DLL 的不同版本，該版本將不會包含您的中斷點。 偵錯 Dll 的其他方法，請參閱[偵錯 DLL 專案](../debugger/debugging-dll-projects.md)。
  
如果您受管理的應用程式呼叫原生 DLL，或您的原生應用程式呼叫的 managed 的 DLL，您可以偵錯 DLL 和呼叫端的應用程式。 如需詳細資訊，請參閱 <<c0> [ 如何： 在混合模式偵錯](../debugger/how-to-debug-in-mixed-mode.md)。   

原生和 managed DLL 專案會有不同的設定，來指定呼叫的應用程式。 

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>在原生 DLL 專案中指定呼叫端的應用程式  
  
1. 選取中的 c + + DLL 專案**方案總管 中**。 選取 **屬性**圖示，並按下**Alt**+**Enter**，或以滑鼠右鍵按一下並選擇 **屬性**。
   
1. 在  **\<專案 > 屬性頁**對話方塊方塊中，請確定**組態**在視窗頂端的欄位設定為**偵錯**。 
   
1. 選取 **組態屬性** > **偵錯**。  
   
1. 在 **偵錯工具啟動**清單中，選擇**本機 Windows 偵錯工具**或是**遠端 Windows 偵錯工具**。  
   
1. 在 **命令**或**遠端命令**方塊中，新增的完整的路徑和檔名呼叫端的應用程式，例如 *.exe*檔案。
   
   ![偵錯屬性 視窗](../debugger/media/dbg-debugging-properties-dll.png "偵錯屬性 視窗")  
   
1. 加入任何必要的程式引數**命令列引數** 方塊中。  
   
1. 選取 [確定]。

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>指定呼叫端的應用程式中的 managed DLL 專案  
  
1. 中，選取 C# 或 Visual Basic DLL 專案**方案總管 中**。 選取 **屬性**圖示，並按下**Alt**+**Enter**，或以滑鼠右鍵按一下並選擇 **屬性**。
   
1. 請確定**組態**頂端的視窗 欄位設為**偵錯**。
   
1. 底下**啟動動作**:
   
   - 適用於.NET Framework Dll，請選取**啟動外部程式**，並新增的完整的路徑和呼叫端的應用程式的名稱。
     
   - 或者，選取**瀏覽器起始 URL**並填入本機的 ASP.NET 應用程式的 URL。 
   
   - 適用於.NET Core 的 Dll，**偵錯**屬性頁面會不同。 選取 **可執行檔**從**啟動**下拉式清單中，然後新增 呼叫端的應用程式中的名稱與完整的路徑**可執行檔**欄位。 
   
1. 新增任何必要的命令列引數中**命令列引數**或是**應用程式引數**欄位。
   
   ![C# 偵錯屬性 視窗](../debugger/media/dbg-debugging-properties-dll-csharp.png "C# 偵錯屬性 視窗") 
   
1. 使用**檔案** > **儲存選取項目**或是**Ctrl**+**S**以儲存變更。

## <a name="debug-from-the-dll-project"></a>從 DLL 專案進行偵錯  
 
1. DLL 專案中設定中斷點。

1. DLL 專案上按一下滑鼠右鍵，然後選擇 **設定為啟始專案**。 

1. 請確定**解決方案組態**欄位設定為**偵錯**。 按下**F5**，按一下綠色**開始**箭號或選取**偵錯** > **開始偵錯**。

如果偵錯時，不會達到您的中斷點，請確定您的 DLL，輸出 (根據預設， *\<專案 > \Debug*資料夾) 是呼叫的應用程式會呼叫的位置。
  
## <a name="see-also"></a>另請參閱  
 [偵錯 DLL 專案](../debugger/debugging-dll-projects.md)   
 [C# 偵錯組態的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 偵錯組態的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [C++ 偵錯設定的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)