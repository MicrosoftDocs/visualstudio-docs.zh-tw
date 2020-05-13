---
title: 調試 DLL 專案 |微軟文檔
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302200"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>在視覺化工作室中調試 DLL（C、C++、視覺基礎、F#）

DLL（動態連結程式庫）是一個庫，其中包含代碼和資料，可以由多個應用使用。 您可以使用 Visual Studio 創建、構建、配置和調試 DLL。

## <a name="create-a-dll"></a>創建 DLL

以下視覺化工作室專案範本可以創建 DLL：

- C#、可視基本或 F# 類庫
- C# 或可視基本視窗表單控制項 （WCF） 庫
- C++動態連結程式庫 （DLL）

有關詳細資訊，請參閱[MFC 調試技術](../debugger/mfc-debugging-techniques.md)。

調試 WCF 庫類似于調試類庫。 有關詳細資訊，請參閱[Windows 表單控制項](/dotnet/framework/winforms/controls/index)。

您通常從另一個專案調用 DLL。 調試調用專案時，根據 DLL 配置，可以單一步驟和調試 DLL 代碼。

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a>DLL 調試配置

當您使用 Visual Studio 專案範本創建應用時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]將自動為調試和發佈組建組態創建所需的設置。 如有必要，可以更改這些設置。 如需詳細資訊，請參閱下列文章：

- [C++調試配置的專案設置](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [C# 調試配置的專案設置](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 偵錯設定的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [操作方式：設置調試和發佈配置](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>設置C++可調試屬性

要將調試器附加到C++ DLL，C++代碼必須發出`DebuggableAttribute`。

**要設置`DebuggableAttribute`：**

1. 在**解決方案資源管理器**中選擇C++ DLL 專案，然後選擇 **"屬性**"圖示，或按右鍵專案並選擇 **"屬性**"。

1. 在 **"屬性**"窗格中，在 **"連結器** > **調試"** 下，選擇"**是"（/會議）** 以進行**偵錯工具集**。

有關詳細資訊，請參閱[/會議調試](/cpp/build/reference/assemblydebug-add-debuggableattribute)。

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a>設置 C/C++ DLL 檔位置

要調試外部 DLL，調用專案必須能夠找到 DLL、其[.pdb 檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)以及 DLL 所需的任何其他檔。 您可以創建自訂生成任務，將這些檔案複製到*\<專案資料夾>_Debug*輸出檔案夾，也可以手動複製其中的檔。

對於 C/C++專案，您可以在專案屬性頁中設置標頭和 LIB 檔位置，而不是將它們複製到輸出檔案夾。

**要設置 C/C++標頭和 LIB 檔位置：**

1. 在**解決方案資源管理器**中選擇 C/C++ DLL 專案，然後選擇 **"屬性"** 圖示，或按右鍵專案並選擇 **"屬性**"。

1. 在 **"屬性"** 窗格的頂部，在 **"配置**"下，選擇 **"所有配置**"。

1. 在**C/C++** > **常規** > **附加包含目錄**下，指定具有標標頭檔的資料夾。

1. 在**連結器** > **常規** > **附加庫目錄**下，指定具有 LIB 檔的資料夾。

1. 在**連結器** > **輸入** > **附加依賴項**下 ，指定 LIB 檔的完整路徑和檔案名。

1. 選取 [確定]****。

有關C++專案設置的詳細資訊，請參閱[Windows C++屬性頁引用](/cpp/build/reference/property-pages-visual-cpp)。

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a>構建調試版本

在開始調試之前，請確保生成 DLL 的調試版本。 要調試 DLL，調用應用必須能夠找到其[.pdb 檔和](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)DLL 所需的任何其他檔。

您可以創建自訂生成任務，將 DLL 檔案複製到*\<調用專案資料夾>_Debug*輸出檔案夾，也可以手動複製其中的檔。

請確保在正確的位置調用 DLL。 這似乎是顯而易見的，但如果調用應用發現並載入 DLL 的不同副本，調試器將永遠不會擊中您設置的中斷點。

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a>調試 DLL

不能直接運行 DLL。 它必須由應用程式調用，通常是 *.exe*檔。 有關詳細資訊，請參閱[視覺化工作室專案 - C++](/cpp/ide/creating-and-managing-visual-cpp-projects)。

要調試 DLL，可以從[調用應用開始調試](#vxtskdebuggingdllprojectsthecallingapplication)，也可以通過指定其調用應用[從 DLL 專案調試](how-to-debug-from-a-dll-project.md)。 您還可以使用調試器["立即"視窗](#vxtskdebuggingdllprojectstheimmediatewindow)在設計時評估 DLL 函數或方法，而無需使用調用應用。

有關詳細資訊，請參閱[首先查看調試器](../debugger/debugger-feature-tour.md)。

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a>從調用應用開始調試

調用 DLL 的應用可以是：

- 來自[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案的應用，與 DLL 相同或不同的解決方案。
- 已在測試或生產電腦上部署和運行的現有應用。
- 位於 Web 上並經由 URL 存取。
- 包含嵌入 DLL 的網頁的 Web 應用。

要調試來自調用應用的 DLL，可以：

- 打開調用應用的專案，並通過選擇**調試** > **啟動調試**或按**F5**開始調試。

  或

- 附加到已在測試或生產電腦上部署和運行的應用。 對網站或 Web 應用中的 DLL 使用此方法。 有關詳細資訊，請參閱[如何：附加到正在運行的進程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。

在開始調試調用應用之前，在 DLL 中設置中斷點。 請參閱[使用中斷點](../debugger/using-breakpoints.md)。 當 DLL 中斷點命中時，您可以單一步驟代碼，觀察每行的操作。 有關詳細資訊，請參閱[調試器中的導航代碼](../debugger/navigating-through-code-with-the-debugger.md)。

在調試期間，可以使用 **"模組"** 視窗驗證應用載入的 DLL 和 *.exe*檔。 要打開 **"模組"** 視窗，請在調試時**選擇"調試** > **Windows** > **模組**"。 有關詳細資訊，請參閱[如何：使用模組視窗](../debugger/how-to-use-the-modules-window.md)。

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a>使用"立即"視窗

您可以使用 **"立即"** 視窗在設計時評估 DLL 函數或方法。 **"立即"** 視窗將扮演調用應用的角色。

>[!NOTE]
>您可以在設計時對大多數專案類型使用 **"立即"** 視窗。 SQL、Web 專案或腳本不支援它。

例如，要測試類`Test``Class1`中名為 的方法：

1. 打開 DLL 專案後，通過選擇 **"立即調試** > **視窗** > **"** 或按**Ctrl**+**Alt**+**I**打開 **"立即**"視窗。

1. 通過在 **"立即"** 視窗中鍵入以下`Class1`C# 代碼並按**Enter**， 具現化類型物件。 此託管代碼適用于 C# 和 Visual Basic，並進行了適當的語法更改：

   ```csharp
   Class1 obj = new Class1();
   ```

   在 C# 中，所有名稱都必須是完整名稱。 當語言服務嘗試計算運算式時，任何方法或變數都必須位於當前範圍和上下文中。

1. 假設 `Test` 使用了一個 `int` 參數，並使用 [即時運算] `Test`**視窗評估** ：

   ```csharp
   ?obj.Test(10);
   ```

   結果列印在 **"立即"** 視窗中。

1. 您可以將中斷點放置在 `Test` 內繼續對其進行偵錯，然後再次評估該函式。

   中斷點將被命中，您可以單一步驟`Test`。 當執行離開 `Test` 之後，偵錯工具會返回設計模式。

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a>混合模式調試

您可以在託管代碼或本機代碼中為 DLL 編寫調用應用。 如果本機應用調用託管 DLL 並且希望同時調試這兩個，則可以在專案屬性中同時啟用託管調試器和本機調試器。 確切的過程取決於您是想從 DLL 專案還是調用應用專案開始調試。 有關詳細資訊，請參閱[操作操作：混合模式下的調試](../debugger/how-to-debug-in-mixed-mode.md)。

您還可以從託管調用專案中調試本機 DLL。 有關詳細資訊，請參閱[如何調試託管和本機代碼](how-to-debug-managed-and-native-code.md)。

## <a name="see-also"></a>另請參閱
- [對 Managed 程式碼進行偵錯](../debugger/debugging-managed-code.md)
- [準備調試C++專案](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#、F# 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [C++調試配置的專案設置](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [C# 調試配置的專案設置](../debugger/project-settings-for-csharp-debug-configurations.md)
- [視覺化基本調試配置的專案設置](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [偵錯工具安全性](../debugger/debugger-security.md)
