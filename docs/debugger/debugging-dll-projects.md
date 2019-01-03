---
title: 偵錯 DLL 專案 |Microsoft Docs
ms.custom: ''
ms.date: 11/06/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f35a04620da94efca70fb33933f3940005996e29
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561690"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>偵錯在 Visual Studio 中的 Dll (C#，c + +、 Visual Basic 中， F#)

DLL （動態連結程式庫） 是包含程式碼和資料可供多個應用程式的程式庫。 您可以使用 Visual Studio 來建立、 建置、 設定和偵錯 Dll。 

## <a name="create-a-dll"></a>建立 DLL

下列 Visual Studio 專案範本可以建立 Dll:

- C#Visual Basic 中，或F#類別庫 
- C#Visual Basic Windows Form 控制項 (WCF) 程式庫或 
- C + + 動態連結程式庫 (DLL)

如需詳細資訊，請參閱 [MFC 偵錯技術](../debugger/mfc-debugging-techniques.md)。

偵錯 WCF 程式庫是類似於偵錯類別庫。 如需詳細資訊，請參閱 < [Windows Forms 控制項](/dotnet/framework/winforms/controls/index)。  

您通常會呼叫另一個專案中的 DLL。 當您偵錯呼叫專案中的，根據 DLL 組態中，您可以逐步執行和偵錯 DLL 程式碼。 

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> DLL 的偵錯組態

當您使用 Visual Studio 專案範本建立應用程式，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]偵錯和發行組建組態，便會自動建立必要的設定。 如有必要，您可以變更這些設定。 如需詳細資訊，請參閱下列文章：

- [C++ 偵錯設定的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [C# 偵錯設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 偵錯設定的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [如何：設定偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)  
  
### <a name="set-c-debuggableattribute"></a>設定 c + + DebuggableAttribute

偵錯工具附加至 c + + DLL，c + + 程式碼必須發出`DebuggableAttribute`。 

**若要設定`DebuggableAttribute`:**

1. 選取中的 c + + DLL 專案**方案總管**，然後選取**屬性**圖示，或以滑鼠右鍵按一下專案，然後選取**屬性**。 
   
1. 在**屬性**窗格下方**連結器** > **偵錯**，選取**是 (/ ASSEMBLYDEBUG)** 如**可偵錯的組件**。 

如需詳細資訊，請參閱 < [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)。  

### <a name="vxtskdebuggingdllprojectsexternal"></a> 設定 C/c + + DLL 檔案位置 

若要偵錯外部 DLL，呼叫的專案必須是能夠找出 DLL，其[.pdb 檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)，以及任何其他 DLL 需要的檔案。 您可以建立自訂建置工作來複製這些檔案，以您*\<專案資料夾 > \Debug*輸出資料夾，或者也可以手動將複製的檔案。

對於 C/c + + 專案，您可以設定專案屬性頁中，而不是將它們複製到輸出資料夾中的標頭和 LIB 檔案位置。 

**若要設定 C/c + + 標頭和 LIB 檔案位置：**

1. 中，選取 C/c + + DLL 專案**方案總管**，然後選取**屬性**圖示，或以滑鼠右鍵按一下專案，然後選取**屬性**。 
   
1. 在頂端**屬性**窗格下方**組態**，選取**所有組態**。
   
1. 底下**C/c + +** > **一般** > **其他 Include 目錄**，指定具有標頭檔的資料夾。
   
1. 底下**連結器** > **一般** > **其他程式庫目錄**，指定具有程式庫檔案的資料夾。 
   
1. 底下**連結器** > **輸入** > **其他相依性**，指定完整路徑和 LIB 檔案的檔名。

1. 選取 [確定]。

如需有關 c + + 專案設定的詳細資訊，請參閱 <<c0> [ 屬性頁 （Visual c + +）](/cpp/ide/property-pages-visual-cpp)。
  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> 建置偵錯版本  

請務必在您開始偵錯之前，請建置 DLL 的偵錯版本。 若要偵錯 DLL，呼叫端的應用程式必須能夠尋找其[.pdb 檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)以及 DLL 需要的任何其他檔案。 

您可以建立自訂建置工作來 DLL 將檔案複製到您*\<呼叫的專案資料夾 > \Debug*輸出資料夾，或者也可以手動將複製的檔案。

請確定在正確的位置中呼叫的 DLL。 這可能就很明顯，但如果呼叫端的應用程式會尋找並載入 DLL 的不同複本，偵錯工具會永遠不會達到您設定的中斷點。 

##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> 偵錯 DLL  

您無法直接執行 DLL。 它必須由呼叫應用程式，通常 *.exe*檔案。 如需詳細資訊，請參閱 <<c0> [ 建立及管理 Visual c + + 專案](/cpp/ide/creating-and-managing-visual-cpp-projects)。 

若要偵錯 DLL，您可以[從呼叫端的應用程式開始偵錯](#vxtskdebuggingdllprojectsthecallingapplication)，或[從 DLL 專案進行偵錯](how-to-debug-from-a-dll-project.md)藉由指定其呼叫端的應用程式。 您也可以使用偵錯工具[即時運算視窗](#vxtskdebuggingdllprojectstheimmediatewindow)在設計階段評估的 DLL 函式或方法，而不需使用呼叫端的應用程式。

如需詳細資訊，請參閱 <<c0> [ 第一次查看偵錯工具](../debugger/debugger-feature-tour.md)。

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> 從呼叫端的應用程式開始偵錯

呼叫 DLL 的應用程式可以是：  
  
- 將應用程式從[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中相同或不同的解決方案，從 DLL 專案。  
- 已部署的現有應用程式，並在測試或實際執行電腦上的執行。  
- 位於 Web 上並經由 URL 存取。  
- 嵌入該 DLL 的網頁與 web 應用程式。  
  
若要偵錯 DLL，以從呼叫端的應用程式，您可以：  
  
- 開啟的專案呼叫的應用程式，並開始偵錯選取**偵錯** > **開始偵錯**或按下**F5**。  

  或  

- 附加至已部署和執行測試或實際執行電腦上的應用程式。 在網站或 web 應用程式中，請使用這個方法的 Dll。 如需詳細資訊，請參閱[＜How to：附加至執行中的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
在開始偵錯呼叫的應用程式之前，請在 DLL 中設定中斷點。 請參閱[使用中斷點](../debugger/using-breakpoints.md)。 當 DLL 叫用中斷點時，您可以逐步執行程式碼中，觀察每一行程式碼的動作。 如需詳細資訊，請參閱 <<c0> [ 偵錯工具中巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)。
  
偵錯期間，您可以使用**模組**視窗以確認 Dll 和 *.exe*檔案在應用程式載入。 若要開啟 **模組**視窗中的，偵錯時，選取**偵錯** > **Windows** > **模組**。 如需詳細資訊，請參閱[＜How to：使用模組視窗](../debugger/how-to-use-the-modules-window.md)。 

###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> 使用即時運算視窗  

您可以使用**Immediate**視窗，以在設計階段評估的 DLL 函式或方法。 **Immediate**視窗扮演的角色的呼叫端的應用程式。 

>[!NOTE]
>您可以使用**Immediate**在設計階段與大部分的專案類型的視窗。 它不支援 SQL、 web 專案或指令碼。

例如，若要測試的方法命名為`Test`類別中`Class1`:

1. DLL 專案開啟時，開啟**Immediate**視窗中的選取**偵錯** > **Windows** > **即時運算**或按下**Ctrl**+**Alt**+**我**。  
   
1. 類型的物件具現化`Class1`中輸入下列C#中的程式碼**即時運算**視窗，並按下**Enter**。 此受管理的程式碼適用於C#和 Visual Basic，搭配適當的語法改變：  
   
   ```csharp
   Class1 obj = new Class1();  
   ```  
  
   在 C# 中，所有名稱都必須是完整名稱。 任何方法或變數必須位於目前的範圍及內容時的語言服務會嘗試評估運算式。  
   
1. 假設 `Test` 使用了一個 `int` 參數，並使用 [即時運算] `Test`**視窗評估** ：  
   
   ```csharp
   ?obj.Test(10);  
   ```  
   
   中的結果會列印**Immediate**視窗。  
   
1. 您可以將中斷點放置在 `Test` 內繼續對其進行偵錯，然後再次評估該函式。  
   
   會叫用中斷點，而且您可以透過`Test`。 當執行離開 `Test` 之後，偵錯工具會返回設計模式。

##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> 混合模式偵錯  

您可以在 managed 或原生程式碼 dll 撰寫呼叫端的應用程式。 如果原生應用程式呼叫的 managed 的 DLL，而且您想要偵錯，您可以啟用這兩個 managed 和原生偵錯工具在專案屬性中。 確切的程序取決於您是否想要開始偵錯 DLL 專案中或呼叫的應用程式專案。 如需詳細資訊，請參閱[＜How to：在混合模式中進行偵錯](../debugger/how-to-debug-in-mixed-mode.md)。 

您也可以偵錯原生 DLL 從受控呼叫的專案。 如需詳細資訊，請參閱 <<c0> [ 如何偵錯 managed 和原生程式碼](how-to-debug-managed-and-native-code.md)。 

## <a name="see-also"></a>另請參閱  
 [對受控碼進行偵錯](../debugger/debugging-managed-code.md)   
 [Visual C++ 專案類型](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#、F# 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C++ 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C# 偵錯組態的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 偵錯組態的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)
