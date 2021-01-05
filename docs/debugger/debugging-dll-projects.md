---
title: 調試 DLL 專案 |Microsoft Docs
description: 在 Visual Studio 中，將動態連結程式庫 (DLL) 檔案進行調試。 使用 Visual Studio 來建立、建立、設定和調試 Dll。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ec78e9a04062699ea699f45671e1210fc2306631
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728495"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Visual Studio 中的 Debug Dll (c #、c + +、Visual Basic、F # ) 

DLL (動態連結程式庫) 是一種程式庫，其中包含可供多個應用程式使用的程式碼和資料。 您可以使用 Visual Studio 來建立、建立、設定和調試 Dll。

## <a name="create-a-dll"></a>建立 DLL

下列 Visual Studio 專案範本可以建立 Dll：

- C #、Visual Basic 或 F # 類別庫
- C # 或 Visual Basic Windows Forms 控制項 (WCF) 程式庫
- C + + Dynamic-Link 程式庫 (DLL) 

如需詳細資訊，請參閱 [MFC 調試技術](../debugger/mfc-debugging-techniques.md)。

WCF 程式庫的偵錯工具類似于錯類別庫的偵錯工具。 如需詳細資訊，請參閱 [Windows Forms 控制項](/dotnet/framework/winforms/controls/index)。

您通常會從另一個專案呼叫 DLL。 當您在進行呼叫專案的偵錯工具時，您可以逐步執行和偵錯工具 DLL 程式碼。

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> DLL debug 設定

當您使用 Visual Studio 專案範本來建立應用程式時， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會自動為 Debug 和 Release 組建設定建立必要的設定。 如有必要，您可以變更這些設定。 如需詳細資訊，請參閱下列文章：

- [C++ 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [C # debug 設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 偵錯組態的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [How to：設定 Debug 和 Release 設定](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>設定 c + + DebuggableAttribute

若要讓偵錯工具附加至 c + + DLL，c + + 程式碼必須發出 `DebuggableAttribute` 。

**若要設定 `DebuggableAttribute` ：**

1. 在 **方案總管** 中選取 c + + DLL 專案，並選取 [ **屬性** ] 圖示，或以滑鼠右鍵按一下專案，然後選取 [ **屬性**]。

1. 在 [**屬性**] 窗格的 [**連結器**  >  **調試** 程式] 下，選取 **[是] (/ASSEMBLYDEBUG)** 來進行可 **調試元件**。

如需詳細資訊，請參閱 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)。

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a> 設定 C/c + + DLL 檔案位置

若要將外部 DLL 錯用，呼叫專案必須能夠找到 DLL、其 [.pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)檔案，以及 dll 所需的任何其他檔案。 您可以建立自訂群組建工作，將這些檔案複製到 *\<project folder> \Debug* 輸出檔案夾，也可以手動複製檔案。

針對 C/c + + 專案，您可以在專案屬性頁中設定標頭和 LIB 檔案位置，而不是將它們複製到輸出檔案夾。

**若要設定 C/c + + 標頭和 LIB 檔案位置：**

1. 在 **方案總管** 中選取 C/c + + DLL 專案，並選取 [ **屬性** ] 圖示，或以滑鼠右鍵按一下專案，然後選取 [ **屬性**]。

1. 在 [ **屬性** ] 窗格頂端的 [設定] **底下，選取**[ **所有** 設定]。

1. 在 [ **c/c + +**  >  **一般**  >  **其他 Include 目錄**] 底下，指定具有標頭檔的資料夾。

1. 在 [**連結器**  >  **一般**  >  **其他程式庫] 目錄** 下，指定具有 LIB 檔的資料夾。

1. 在 [**連結器**  >  **輸入**  >  **其他** 相依性] 底下，指定 LIB 檔案的完整路徑和檔案名。

1. 選取 [確定]。

如需 c + + 專案設定的詳細資訊，請參閱 [Windows c + + 屬性頁參考](/cpp/build/reference/property-pages-visual-cpp)。

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> 建立 Debug 版本

開始偵錯工具之前，請務必先建立 DLL 的偵錯工具版本。 若要對 DLL 進行偵錯工具，呼叫的應用程式必須能夠找到其 [.pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) 檔案和 DLL 所需的任何其他檔案。

您可以建立自訂群組建工作，將 DLL 檔案複製到 *\<calling project folder> \Debug* 輸出檔案夾，也可以手動複製檔案。

請務必在正確的位置呼叫 DLL。 這看起來似乎很明顯，但如果呼叫的應用程式找到並載入不同的 DLL 複本，偵錯工具將永遠不會叫用您設定的中斷點。

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> 調試 DLL

您無法直接執行 DLL。 它必須由應用程式呼叫，通常是 *.exe* 檔案。 如需詳細資訊，請參閱 [Visual Studio 專案-c + +](/cpp/ide/creating-and-managing-visual-cpp-projects)。

若要對 DLL 進行偵錯工具，您可以 [從呼叫應用程式開始進行偵錯工具](#vxtskdebuggingdllprojectsthecallingapplication)，或藉由指定其呼叫的應用程式， [從 DLL 專案進行調試](how-to-debug-from-a-dll-project.md) 程式。 您也可以使用偵錯工具 [即時運算 [] 視窗](#vxtskdebuggingdllprojectstheimmediatewindow) ，在設計階段評估 DLL 函式或方法，而不需要使用呼叫的應用程式。

如需詳細資訊，請參閱 [偵錯工具的第一次查看](../debugger/debugger-feature-tour.md)。

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a> 開始從呼叫應用程式進行偵錯工具

呼叫 DLL 的應用程式可以是：

- 從 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] DLL 中相同或不同方案中的專案所產生的應用程式。
- 已在測試或實際執行電腦上部署並執行的現有應用程式。
- 位於 Web 上並經由 URL 存取。
- Web 應用程式，其中包含內嵌 DLL 的網頁。

若要從呼叫應用程式進行 DLL 的偵錯工具，您可以：

- 開啟呼叫應用程式的專案，然後選取 [ **Debug**  >  **開始調試** 程式] 或按下 **F5** 來開始進行偵錯工具。

  或

- 附加至已在測試或實際執行電腦上部署並執行的應用程式。 針對網站或 web 應用程式中的 Dll，請使用此方法。 如需詳細資訊，請參閱 [如何：附加至正在執行的進程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。

開始對呼叫應用程式進行偵錯工具之前，請先在 DLL 中設定中斷點。 請參閱 [使用中斷點](../debugger/using-breakpoints.md)。 當遇到 DLL 中斷點時，您可以逐步執行程式碼，觀察每一行的動作。 如需詳細資訊，請參閱 [在偵錯工具中流覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)。

在偵錯工具中，您可以使用 [ **模組** ] 視窗來驗證應用程式載入的 dll 和 *.exe* 檔案。 若要開啟 [**模組**] 視窗，在進行調試時，請選取 [ **Debug**  >  **Windows**  >  **模組**]。 如需詳細資訊，請參閱 [如何：使用模組視窗](../debugger/how-to-use-the-modules-window.md)。

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> 使用即時運算視窗

您可以 **使用 [即時** 運算] 視窗，在設計階段評估 DLL 函式或方法。 [即時 **運算] 視窗** 扮演呼叫應用程式的角色。

>[!NOTE]
>您可以在設計階段使用大部分的專案類型來 **使用 [即時** 運算] 視窗。 它不支援 SQL、Web 專案或腳本。

例如，若要測試在類別中名為的方法 `Test` `Class1` ：

1. 開啟 DLL 專案時，選取 [立即 **調試****程式]**  >    >  或按 **Ctrl** + **Alt** + **I**，開啟 [即時運算] 視窗。

1. `Class1`在 [即時運算] 視窗中輸入下列 c # 程式碼 ，然後按 **enter**，以具現化類型的物件。 此 managed 程式碼適用于 c # 和 Visual Basic，並具有適當的語法變更：

   ```csharp
   Class1 obj = new Class1();
   ```

   在 C# 中，所有名稱都必須是完整名稱。 當語言服務嘗試評估運算式時，任何方法或變數都必須在目前的範圍和內容中。

1. 假設 `Test` 使用了一個 `int` 參數，並使用 [即時運算] `Test`**視窗評估** ：

   ```csharp
   ?obj.Test(10);
   ```

   結果會 **列印在 [即時運算] 視窗** 中。

1. 您可以將中斷點放置在 `Test` 內繼續對其進行偵錯，然後再次評估該函式。

   將會叫用中斷點，您可以逐步執行 `Test` 。 當執行離開 `Test` 之後，偵錯工具會返回設計模式。

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> 混合模式的調試

您可以使用 managed 或機器碼撰寫 DLL 的呼叫應用程式。 如果您的原生應用程式呼叫 managed DLL，而且您想要同時進行兩個偵錯工具，您可以在專案屬性中啟用 managed 和原生偵錯工具。 確切的程式取決於您是要從 DLL 專案或呼叫應用程式專案開始進行偵錯工具。 如需詳細資訊，請參閱 [如何：在混合模式中進行 Debug](../debugger/how-to-debug-in-mixed-mode.md)。

您也可以從 managed 呼叫專案中，對原生 DLL 進行錯。 如需詳細資訊，請參閱 [如何調試 managed 和機器碼](how-to-debug-managed-and-native-code.md)。

## <a name="see-also"></a>請參閱
- [對受控碼進行偵錯](../debugger/debugging-managed-code.md)
- [準備 debug c + + 專案](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C #、F # 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [C + + 偵錯工具設定的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [C # Debug 設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic Debug 設定的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [偵錯工具安全性](../debugger/debugger-security.md)
