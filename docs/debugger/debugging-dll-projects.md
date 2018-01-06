---
title: "偵錯 DLL 專案 |Microsoft 文件"
ms.custom: 
ms.date: 05/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7b43d7c5fb8d66e758a44b86d4918f04599d6147
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-dll-projects-from-visual-studio"></a>從 Visual Studio 偵錯 DLL 專案
下列 Visual Studio 範本會建立 Dll:  
  
-   (C++、C# 和 Visual Basic) 類別庫   

-   （c + +）： Win32 主控台 DLL 專案
  
     如需詳細資訊，請參閱 [MFC Debugging Techniques](../debugger/mfc-debugging-techniques.md)。

-   (C++、C# 和 Visual Basic)：Windows Form 控制項程式庫
  
     類似於偵錯類別庫專案偵錯 Windows Form 控制項程式庫。 在大多數的情況，您會從另一個專案呼叫 Windows 控制項。 當您偵錯呼叫專案時，您可以逐步執行您的 Windows 控制項的程式碼、設定中斷點，和執行其他偵錯工作。 如需詳細資訊，請參閱 [Windows Form 控制項](/dotnet/framework/winforms/controls/index)。  

  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Building a debug version  
 無論您如何啟動偵錯，確定要先建置 DLL 的偵錯版本，並且確定該偵錯版本是位於應用程式預期可找到的位置。 這似乎是顯而易見的事情，但是如果您忘記這個步驟，應用程式可能會尋找到 DLL 的其他版本並且載入。 程式將會繼續執行，而您會懷疑為何一直沒遇到中斷點。 您可以在偵錯時開啟偵錯工具的 [ **模組** ] 視窗，驗證您的程式載入了哪些 DLL。 [ **模組** ] 視窗會列出正在偵錯的處理序中所載入的每個 DLL 或 EXE。 如需詳細資訊，請參閱 [How to: Use the Modules Window](../debugger/how-to-use-the-modules-window.md)。  
 若要將偵錯工具附加至以 C++ 撰寫的程式碼，該程式碼必須發出 `DebuggableAttribute`。 您可以使用 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) 連結器選項連結，將其自動加入程式碼。  
  
##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Mixed-Mode debugging  
 呼叫 DLL 的呼叫應用程式可以用 Managed 程式碼或機器碼撰寫。 如果您的 Managed DLL 是由機器碼呼叫，而您要偵錯 Managed 程式碼和機器碼，則 Managed 偵錯工具和原生偵錯工具皆必須啟用。 您可以選取此選項在**\<專案 > 屬性頁**對話方塊或視窗。 不同的做法是取決於您是由 DLL 專案啟動偵錯，或者由呼叫應用程式專案啟動偵錯。 如需詳細資訊，請參閱 [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md)。  
  
##  <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Changing default configurations  
 當您以專案範本建立主控台應用程式專案時， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會自動建立偵錯和發行組態所需要的設定。 若有需要，您可以變更這些設定。 如需詳細資訊，請參閱[c + + 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)， [C# 偵錯組態的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)， [Visual Basic 偵錯組態的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)，和[How to： 設定偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)。  
  
##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Ways to debug the DLL  
 本節中的每一個專案都會建立 DLL。 您無法直接執行 DLL，它必須由應用程式進行呼叫 (通常是 EXE)。 如需詳細資訊，請參閱 [Creating and Managing Visual C++ Projects](/cpp/ide/creating-and-managing-visual-cpp-projects)。 呼叫的應用程式可能符合下列其中一項準則：  
  
-   一個應用程式，在相同的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 方案中建置於另一個包含該類別庫的專案。  
  
-   已部署在測試或實際執行電腦上的現有應用程式。  
  
-   位於 Web 上並且經由 URL 存取。  
  
-   包含嵌入該 DLL 的網頁之 Web 應用程式。  
  
###  <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Debugging the calling application  
若要偵錯 DLL，請由偵錯呼叫的應用程式開炲，通常是 EXE 或 Web 應用程式。 您可以使用幾種方式進行偵錯。  
  
-   如果您有呼叫應用程式的專案，就可以開啟該專案，並且從 [ **偵錯** ] 功能表啟動執行。 如需詳細資訊，請參閱[偵錯工具使用者入門](../debugger/getting-started-with-the-debugger.md)。  
  
-   如果該呼叫應用程式是已部署在測試或實際執行電腦上的現有程式，而且已經在執行，您可以附加至這個應用程式。 如果該 DLL 是 Internet Explorer 所裝載的控制項，或網頁上的控制項，請使用這個方法。 如需詳細資訊，請參閱 [How to: Attach to a Running Process](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
-   您可以從 DLL 專案對呼叫的應用程式進行偵錯。 如需詳細資訊，請參閱 [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md)。  
  
-   您可以從偵錯[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)][即時運算視窗](#vxtskdebuggingdllprojectstheimmediatewindow)。 在這個情況下，[ **即時運算** ] 視窗扮演應用程式的角色。  
  
在您啟動偵錯呼叫的應用程式之前，您通常要在類別庫裡設定中斷點。 如需詳細資訊，請參閱 [Using Breakpoints](../debugger/using-breakpoints.md)。 遇到中斷點時，您可以逐步執行程式碼，觀察每行的動作，直到您分辨出問題的所在。 如需詳細資訊，請參閱[巡覽偵錯工具中的程式碼](../debugger/navigating-through-code-with-the-debugger.md)。
  
###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> 即時運算視窗  
 您不需呼叫應用程式，即可評估 DLL 中的函式或方法。 您可以執行設計階段偵錯，並使用 [ **即時運算** ] 視窗。 若要使用這種方法偵錯，請在開啟 DLL 專案時進行下列步驟：  
  
1.  開啟偵錯工具 [ **即時運算** ] 視窗。  
  
2.  若要在測試 `Test` 類別中名為 `Class1`的方法，請透過在 [即時運算] 視窗中輸入下列 C# 程式碼產生 `Class1` 類別的物件。 這個 managed 程式碼適用於 Visual Basic 和 C++，加以適當的語法改變：  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     在 C# 中，所有名稱都必須是完整名稱。 此外，任何方法或變數都必須位於偵錯工作階段目前的範圍和內容中。  
  
3.  假設 `Test` 使用了一個 `int` 參數，並使用 [即時運算] `Test`**視窗評估** ：  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     結果會列印在 [ **即時運算** ] 視窗。  
  
4.  您可以將中斷點放置在 `Test` 內繼續對其偵錯，然後再次評估該函式：  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     這個中斷點會被叫用，而且您可以逐步執行 `Test`。 當執行離開 `Test`之後，偵錯工具會返回設計模式。

## <a name="vxtskdebuggingdllprojectsexternal"></a>偵錯 c + + 專案外部 DLL

如果您在偵錯您的專案外部 DLL，偵錯功能 （例如逐步執行程式碼） 將取決於[DLL 的偵錯組態](#vxtskdebuggingdllprojectsbuildingadebugversion)以及其建置時是否[的.pdb檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)而提供其他所需的 DLL 檔案。

您的專案必須是找不到 DLL 和用來偵錯的.pdb 檔案。 您可以建立要複製這些檔案，以自訂建置工作**\<專案資料夾 > \Debug**輸出資料夾中，或者您可以將檔案複製到輸出資料夾中以手動方式。

您可以輕鬆設定的屬性頁中的標頭檔和 *.lib 檔案的位置 (c + + 專案上按一下滑鼠右鍵，然後選擇 **檢視內容**，然後選擇 **所有組態**) 而不需要複製其輸出資料夾：

- C/c + + 資料夾 （一般分類）-指定包含標頭檔中的資料夾**其他 Include 目錄**欄位。
- 連結器資料夾 （一般分類）-指定包含.lib 檔中的資料夾**其他程式庫目錄**欄位。 
- 連結器資料夾 （[輸入] 分類）-指定的完整路徑和檔案名稱中的.lib 檔案**其他相依性**欄位。

正確設定時，您可以偵錯開始執行從**偵錯**功能表。

如需有關專案設定的詳細資訊，請參閱[屬性頁 （Visual c + +）](/cpp/ide/property-pages-visual-cpp)。
  
## <a name="see-also"></a>請參閱  
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)   
 [Visual c + + 專案類型](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#、F# 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C + + 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C# 偵錯設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 偵錯設定的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)