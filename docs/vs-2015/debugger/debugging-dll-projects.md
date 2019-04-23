---
title: 偵錯 DLL 專案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 270f25640e5804944440192ee787f92f1597c58c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108746"
---
# <a name="debugging-dll-projects"></a>偵錯 DLL 專案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

下列範本會建立 DLL：  
  
- (C++、C# 和 Visual Basic) 類別庫  
  
- (C++， C#，和 Visual Basic):Windows Form 控制項程式庫  
  
   Windows 控制項程式庫的偵錯方式與偵錯類別庫專案的方式相似。 在大多數的情況，您會從另一個專案呼叫 Windows 控制項。 當您偵錯呼叫專案時，您可以逐步執行您的 Windows 控制項的程式碼、設定中斷點，和執行其他偵錯工作。 如需詳細資訊，請參閱 [Windows Form 控制項](http://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)。  
  
- (C#和 Visual Basic):Web 控制項程式庫  
  
   如需詳細資訊，請參閱 [Web Control Library (Managed Code)](../debugger/web-control-library-managed-code.md)。  
  
- (C++):MFC ActiveX 控制項和 MFC 智慧型裝置 ActiveX 控制項  
  
   ActiveX 控制項是一種可以透過網際網路下載至用戶端電腦的控制項，並可在網頁上顯示和啟動。  
  
   偵錯 ActiveX 控制項與偵錯其他種類的控制項相似，因為它們都無法獨立執行，必須嵌入 HTML 網頁中才能執行。 如需詳細資訊，請參閱[如何：偵錯 ActiveX 控制項](../debugger/how-to-debug-an-activex-control.md)。  
  
- (C++):MFC 智慧型裝置 DLL  
  
   如需詳細資訊，請參閱 [MFC Debugging Techniques](../debugger/mfc-debugging-techniques.md)。  
  
  本章節也包含下列主題的相關資訊：  
  
- [如何：從 DLL 專案進行偵錯](../debugger/how-to-debug-from-a-dll-project.md)  
  
- [如何：在混合模式中進行偵錯](../debugger/how-to-debug-in-mixed-mode.md)  
  
  本主題包含下列章節，其中提供有關如何準備偵錯類別庫的注意事項：  
  
- [Building a Debug Version](#vxtskdebuggingdllprojectsbuildingadebugversion)  
  
- [Mixed-Mode Debugging](#vxtskdebuggingdllprojectsmixedmodedebugging)  
  
- [Changing Default Configurations](#vxtskdebuggingdllprojectschangingdefaultconfigurations)  
  
- [Ways to Debug the DLL](#vxtskdebuggingdllprojectswaystodebugthedll)  
  
- [The Calling Application](#vxtskdebuggingdllprojectsthecallingapplication)  
  
- [Controls on a Web Page](#vxtskdebuggingdllprojectscontrolsonawebpage)  
  
- [The Immediate Window](#vxtskdebuggingdllprojectstheimmediatewindow)  
  
## <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Building a Debug Version  
 無論您如何啟動偵錯，確定要先建置 DLL 的偵錯版本，並且確定該偵錯版本是位於應用程式預期可找到的位置。 這似乎是顯而易見的事情，但是如果您忘記這個步驟，應用程式可能會尋找到 DLL 的其他版本並且載入。 程式將會繼續執行，而您會懷疑為何一直沒遇到中斷點。 您可以在偵錯時開啟偵錯工具的 [ **模組** ] 視窗，驗證您的程式載入了哪些 DLL。 [ **模組** ] 視窗會列出正在偵錯的處理序中所載入的每個 DLL 或 EXE。 如需詳細資訊，請參閱[如何：使用模組視窗](../debugger/how-to-use-the-modules-window.md)。  
  
 若要將偵錯工具附加至以 C++ 撰寫的程式碼，該程式碼必須發出 `DebuggableAttribute`。 您可以使用 [/ASSEMBLYDEBUG](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) 連結器選項連結，將其自動加入程式碼。  
  
## <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Mixed-Mode Debugging  
 呼叫 DLL 的呼叫應用程式可以用 Managed 程式碼或機器碼撰寫。 如果您的 Managed DLL 是由機器碼呼叫，而您要偵錯 Managed 程式碼和機器碼，則 Managed 偵錯工具和原生偵錯工具皆必須啟用。 您可以選取這**\<專案 > 屬性頁**對話方塊或視窗。 不同的做法是取決於您是由 DLL 專案啟動偵錯，或者由呼叫應用程式專案啟動偵錯。 如需詳細資訊，請參閱[如何：在混合模式偵錯](../debugger/how-to-debug-in-mixed-mode.md)。  
  
## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Changing Default Configurations  
 當您以專案範本建立主控台應用程式專案時， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會自動建立偵錯和發行組態所需要的設定。 若有需要，您可以變更這些設定。 如需詳細資訊，請參閱 <<c0> [ 的專案設定C++偵錯組態](../debugger/project-settings-for-a-cpp-debug-configuration.md)，[的專案設定C#偵錯組態](../debugger/project-settings-for-csharp-debug-configurations.md)， [Visual Basic 偵錯的專案設定組態](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)，和[How to:</c0>設定偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)。  
  
## <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Ways to Debug the DLL  
 本節中的每一個專案都會建立 DLL。 您無法直接執行 DLL，它必須由應用程式進行呼叫 (通常是 EXE)。 如需詳細資訊，請參閱 [Creating and Managing Visual C++ Projects](http://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)。 呼叫的應用程式可能符合下列其中一項準則：  
  
- 一個應用程式，在相同的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 方案中建置於另一個包含該類別庫的專案。  
  
- 已部署在測試或實際執行電腦上的現有應用程式。  
  
- 位於 Web 上並且經由 URL 存取。  
  
- 包含嵌入該 DLL 的網頁之 Web 應用程式。  
  
### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> 偵錯呼叫的應用程式  
 若要偵錯 DLL，請由偵錯呼叫的應用程式開炲，通常是 EXE 或 Web 應用程式。 您可以使用幾種方式進行偵錯。  
  
- 如果您有呼叫應用程式的專案，就可以開啟該專案，並且從 [ **偵錯** ] 功能表啟動執行。 如需詳細資訊，請參閱[如何：開始執行](http://msdn.microsoft.com/b0fe0ce5-900e-421f-a4c6-aa44ddae453c)。  
  
- 如果該呼叫應用程式是已部署在測試或實際執行電腦上的現有程式，而且已經在執行，您可以附加至這個應用程式。 如果該 DLL 是 Internet Explorer 所裝載的控制項，或網頁上的控制項，請使用這個方法。 如需詳細資訊，請參閱[如何：附加至執行中處理序](http://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)。  
  
- 您可以從 DLL 專案對呼叫的應用程式進行偵錯。 如需詳細資訊，請參閱[如何：從 DLL 專案進行偵錯](../debugger/how-to-debug-from-a-dll-project.md)。  
  
- 您可以從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Immediate** window. 在這個情況下，[ **即時運算** ] 視窗扮演應用程式的角色。  
  
  在您啟動偵錯呼叫的應用程式之前，您通常要在類別庫裡設定中斷點。 如需詳細資訊，請參閱 [Breakpoints and Tracepoints](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)。 遇到中斷點時，您可以逐步執行程式碼，觀察每行的動作，直到您分辨出問題的所在。 如需詳細資訊，請參閱 [Code Stepping Overview](http://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9)。  
  
### <a name="vxtskdebuggingdllprojectscontrolsonawebpage"></a> Controls on a Web Page  
 若要偵錯網頁的控制項，請建立嵌入該控制項的 [ [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ] 頁面 (如果這樣的頁面不存在)。 然後您可以在這個網頁和控制項程式碼中放置中斷點。 接下來由 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]叫用這個網頁。  
  
 在呼叫的應用程式啟動偵錯之前，您通常要在 DLL 裡設定中斷點。 遇到中斷點時，您可以逐步執行程式碼，觀察每行的動作，直到您分辨出問題的所在。 如需詳細資訊，請參閱 [Breakpoints and Tracepoints](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)。  
  
### <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> The Immediate Window  
 您不需呼叫應用程式，即可評估 DLL 中的函式或方法。 您可以執行設計階段偵錯，並使用 [ **即時運算** ] 視窗。 若要使用這種方法偵錯，請在開啟 DLL 專案時進行下列步驟：  
  
1. 開啟偵錯工具 [ **即時運算** ] 視窗。  
  
2. 若要在測試 `Test` 類別中名為 `Class1`的方法，請透過在 [即時運算] 視窗中輸入下列 C# 程式碼產生 `Class1` 類別的物件。 這個 managed 程式碼適用於 Visual Basic 和 C++，加以適當的語法改變：  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     在 C# 中，所有名稱都必須是完整名稱。 此外，任何方法或變數都必須位於偵錯工作階段目前的範圍和內容中。  
  
3. 假設 `Test` 使用了一個 `int` 參數，並使用 [即時運算] `Test`**視窗評估** ：  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     結果會列印在 [ **即時運算** ] 視窗。  
  
4. 您可以將中斷點放置在 `Test` 內繼續對其偵錯，然後再次評估該函式：  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     這個中斷點會被叫用，而且您可以逐步執行 `Test`。 當執行離開 `Test`之後，偵錯工具會返回設計模式。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)   
 [Visual C++ 專案類型](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#、F# 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C++ 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C# 偵錯設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 偵錯設定的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)
