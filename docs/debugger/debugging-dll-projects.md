---
title: Debug DLL 專案 |Microsoft Docs
ms.date: 11/06/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 898eb0eb1489d83e97ec9f0a5b38b475bda0199d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72450420"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Visual Studio 中的調試 dllC#（ C++、、Visual Basic F#、）

DLL （動態連結程式庫）是一種程式庫，其中包含可供多個應用程式使用的程式碼和資料。 您可以使用 Visual Studio 來建立、建立、設定和調試 Dll。

## <a name="create-a-dll"></a>建立 DLL

下列 Visual Studio 專案範本可以建立 Dll：

- C#、Visual Basic 或F#類別庫
- C#或 Visual Basic Windows Forms 控制項（WCF）程式庫
- C++動態連結程式庫（DLL）

如需詳細資訊，請參閱 [MFC 偵錯技術](../debugger/mfc-debugging-techniques.md)。

WCF 程式庫的調試與調試類別庫類似。 如需詳細資訊，請參閱[Windows Forms 控制項](/dotnet/framework/winforms/controls/index)。

您通常會從另一個專案呼叫 DLL。 當您根據 DLL 設定來進行呼叫專案的偵錯工具時，您可以逐步執行並對 DLL 程式碼進行偵錯工具。

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a>DLL 的 debug 設定

當您使用 Visual Studio 專案範本建立應用程式時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會自動為 [Debug] 和 [發行] 組建設定建立必要的設定。 您可以視需要變更這些設定。 如需詳細資訊，請參閱下列文章：

- [C++ 偵錯設定的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [C# 偵錯設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 偵錯設定的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [如何：設定偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>設定C++ DebuggableAttribute

若要將偵錯工具附加至C++ DLL，程式C++代碼必須發出 `DebuggableAttribute`。

**若要設定 `DebuggableAttribute`：**

1. 在方案總管C++中選取 DLL專案，並選取 [**屬性**] 圖示，或以滑鼠右鍵按一下專案，然後選取 [**屬性**]。

1. 在 [**屬性**] 窗格的 [**連結器**@no__t **-2] 下，針對**[可**調試元件**] 選取 **[是（/ASSEMBLYDEBUG）]** 。

如需詳細資訊，請參閱[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)。

### <a name="vxtskdebuggingdllprojectsexternal"></a>設定 C/C++ DLL 檔案位置

若要對外部 DLL 進行偵錯工具，呼叫專案必須能夠找到 DLL、其[.pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)檔，以及 dll 所需的任何其他檔案。 您可以建立自訂群組建工作，將這些檔案複製到您*的 @no__t 1project 資料夾 > \Debug*輸出檔案夾，也可以手動複製檔案。

針對 C/C++ projects，您可以在專案屬性頁中設定標頭和 LIB 檔案位置，而不是將它們複製到輸出檔案夾。

**若要設定 CC++ /標頭和 LIB 檔案位置：**

1. 在方案總管中選取C++ [C/ DLL] 專案，並選取 [**屬性**] 圖示，或以滑鼠右鍵按一下專案，然後選取 [**屬性**]。

1. 在 [**屬性**] 窗格頂端的 [設定]**底下，選取**[**所有**設定]。

1. 在 [ **CC++/**  > **一般** >  個**額外的 Include 目錄**] 底下，指定具有標頭檔的資料夾。

1. 在 **[** **連結器** >  一般  >  個**其他程式庫目錄**] 中，指定具有 LIB 檔案的資料夾。

1. 在 [**連結器** > **輸入** >  個其他相依性 **]** 底下，指定 LIB 檔案的完整路徑和檔案名。

1. 選取 [確定]。

如需C++專案設定的詳細資訊，請參閱[Windows C++屬性頁參考](/cpp/build/reference/property-pages-visual-cpp)。

## <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a>建立 Debug 版本

開始進行調試之前，請務必先建立 DLL 的調試版本。 若要對 DLL 進行 debug 錯，呼叫應用程式必須能夠找到其[.pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)檔案和 DLL 所需的任何其他檔案。

您可以建立自訂群組建工作，將 DLL 檔案複製到您的 *@no__t 1calling 專案資料夾 > \Debug*輸出檔案夾，也可以手動複製檔案。

請務必在正確的位置呼叫 DLL。 這看起來似乎很明顯，但如果呼叫應用程式找到並載入不同的 DLL 複本，偵錯工具將永遠不會叫用您所設定的中斷點。

## <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a>調試 DLL

您無法直接執行 DLL。 它必須由應用程式呼叫，通常是 *.exe*檔案。 如需詳細資訊，請參閱[Visual Studio C++專案- ](/cpp/ide/creating-and-managing-visual-cpp-projects)。

若要對 DLL 進行偵錯工具，您可以藉由指定呼叫的應用程式，從[呼叫應用程式開始進行偵錯工具](#vxtskdebuggingdllprojectsthecallingapplication)，或[從 dll 專案進行 debug](how-to-debug-from-a-dll-project.md) 。 您也可以在設計階段使用偵錯工具的 [即時運算[] 視窗](#vxtskdebuggingdllprojectstheimmediatewindow)來評估 DLL 函式或方法，而不需要使用呼叫應用程式。

如需詳細資訊，請參閱[偵錯工具的第一次](../debugger/debugger-feature-tour.md)查看。

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a>從呼叫應用程式開始進行偵錯工具

呼叫 DLL 的應用程式可以是：

- 從 DLL 的相同或不同方案中的 @no__t 0 專案所產生的應用程式。
- 已在測試或實際執行電腦上部署並執行的現有應用程式。
- 位於 Web 上並經由 URL 存取。
- 具有內嵌 DLL 之網頁的 web 應用程式。

若要從呼叫應用程式中進行 DLL 的偵錯工具，您可以：

- 開啟呼叫應用程式的專案，然後選取 [ **Debug** > ] [**開始**進行偵錯工具] 或按**F5**開始進行調試。

  或

- 附加至已在測試或實際執行電腦上部署並執行的應用程式。 針對網站或 web 應用程式中的 Dll 使用此方法。 如需詳細資訊，請參閱[如何：附加至執行中處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。

開始偵測呼叫應用程式之前，請先在 DLL 中設定中斷點。 請參閱[使用中斷點](../debugger/using-breakpoints.md)。 當到達 DLL 中斷點時，您可以逐步執行程式碼，觀察每一行的動作。 如需詳細資訊，請參閱在[偵錯工具中流覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)。

在調試過程中，您可以使用 [**模組**] 視窗來驗證應用程式所載入的 dll 和 *.exe*檔案。 若要開啟 [**模組**] 視窗，請在 [調試] 時，選取 [ **Debug** > **Windows** > **模組**]。 如需詳細資訊，請參閱[如何：使用模組視窗](../debugger/how-to-use-the-modules-window.md)。

### <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a>使用即時運算視窗

在設計**時間，您可以使用 [即時**運算] 視窗來評估 DLL 函式或方法。 [即時**運算] 視窗**扮演呼叫應用程式的角色。

>[!NOTE]
>您**可以在設計階段使用 [即時**運算] 視窗，並搭配大部分的專案類型。 SQL、Web 專案或腳本不支援。

例如，若要在類別 `Class1` 中測試名為 `Test` 的方法：

1. 開啟 DLL 專案後，選取 [Debug **] @no__t** -2 **Windows** >  [**立即**] 或按**Ctrl**+**Alt**+**I**，開啟 [即時運算] 視窗。

1. 在 [即時運算] 視窗中輸入下列C#程式碼，然後按**enter**，將類型 `Class1` 的物件具現化。 此 managed 程式碼適用C#于和 Visual Basic，並具有適當的語法變更：

   ```csharp
   Class1 obj = new Class1();
   ```

   在 C# 中，所有名稱都必須是完整名稱。 當語言服務嘗試評估運算式時，任何方法或變數都必須位於目前的範圍和內容中。

1. 假設 `Test` 使用了一個 `int` 參數，並使用 [即時運算] `Test`**視窗評估** ：

   ```csharp
   ?obj.Test(10);
   ```

   結果會在 [即時**運算] 視窗**中列印出來。

1. 您可以將中斷點放置在 `Test` 內繼續對其進行偵錯，然後再次評估該函式。

   將會叫用中斷點，您可以逐步執行 `Test`。 當執行離開 `Test` 之後，偵錯工具會返回設計模式。

## <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> 混合模式偵錯

您可以使用 managed 或機器碼撰寫 DLL 的呼叫應用程式。 如果您的原生應用程式呼叫 managed DLL，而您想要同時進行這兩項工作，您可以在專案屬性中同時啟用 managed 和原生偵錯工具。 確切的程式取決於您是否想要從 DLL 專案或呼叫應用程式專案開始進行偵錯工具。 如需詳細資訊，請參閱[如何：在混合模式中偵錯](../debugger/how-to-debug-in-mixed-mode.md)。

您也可以從 managed 呼叫專案中，對原生 DLL 進行調試。 如需詳細資訊，請參閱[如何對 managed 和機器碼進行調試](how-to-debug-managed-and-native-code.md)程式。

## <a name="see-also"></a>請參閱
- [對 Managed 程式碼進行偵錯](../debugger/debugging-managed-code.md)
- [準備 debug C++專案](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#, F#, and Visual Basic project types](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md) (C#、F# 和 Visual Basic 專案類型)
- [Project settings for a C++ Debug configuration](../debugger/project-settings-for-a-cpp-debug-configuration.md) (C++ 偵錯組態的專案設定)
- [Project settings for  C# Debug configurations](../debugger/project-settings-for-csharp-debug-configurations.md) (C# 偵錯組態的專案設定)
- [Project settings for a Visual Basic Debug configuration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) (Visual Basic 偵錯組態的專案設定)
- [偵錯工具安全性](../debugger/debugger-security.md)
