---
title: MS 生成特定于C++的任務 |微軟文檔
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 6393e771f9e9ed862d21397dabacdb3f3808c386
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633144"
---
# <a name="msbuild-tasks-specific-to-c"></a>MS 生成特定于C++的任務

提供在建置流程期間執行之程式碼的工作。 安裝C++後，除了 MSBuild 安裝的任務外，還提供以下任務。 有關詳細資訊，請參閱[MSBuild （C++） 概述](/cpp/build/msbuild-visual-cpp-overview)。

 除了適用於每個工作的參數之外，每個工作也會有下列參數。

| 參數 | 描述 |
|-------------------| - |
| `Condition` | 選擇性的 `String` 參數。<br /><br /> MSBuild 引擎用來確定是否執行此任務的`Boolean`運算式。 有關 MSBuild 支援的條件的資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。 |
| `ContinueOnError` | 選擇性參數。 可包含一或多個下列值：<br /><br /> -   **警告並繼續**或**真實**。 當工作失敗時，[Target](../msbuild/target-element-msbuild.md) 項目中的後續工作與組建都會繼續執行，並將來自工作的所有錯誤視為警告。<br />-   **錯誤並繼續**。 當工作失敗時，`Target` 項目中的後續工作與組建都會繼續執行，並將來自工作的所有錯誤視為錯誤。<br />-   **錯誤和停止**或**錯誤**（預設值）。 當工作失敗時，就不會執行 `Target` 項目中的其餘工作和組建，並將整個 `Target` 項目與組建視為失敗。<br /><br /> 只有 4.5 版之前的 .NET Framework 版本支援 `true` 和 `false` 值。<br /><br /> 如需詳細資訊，請參閱[如何：忽略工作中的錯誤](../msbuild/how-to-ignore-errors-in-tasks.md)。 |

### <a name="related-topics"></a>相關主題

|Title|描述|
|-----------|-----------------|
|[BscMake 工作](../msbuild/bscmake-task.md)|包裝 Microsoft Browse Information Maintenance Utility 工具 (*bscmake.exe*)。|
|[CL 任務](../msbuild/cl-task.md)|包裝C++編譯器工具 *（cl.exe*）。|
|[CPP清除任務](../msbuild/cppclean-task.md)|刪除 MSBuild 在生成C++專案時創建的暫存檔案。|
|[ClangCompile 工作](../msbuild/clangcompile-task.md)|包裝C++編譯器工具 *（clang.exe*）。|
|[CustomBuild 工作](../msbuild/custombuild-task.md)|包裝C++編譯器工具 *（cmd.exe*）。|
|[FXC 工作](../msbuild/fxc-task.md)|在建置流程中使用 HLSL 著色器編譯器。|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|讀取舊的 tlog、寫入新的 tlog，並傳回一組不是最新狀態的項目。 (協助程式工作)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|取得 cl 和其他工具的輸出檔案名稱，其允許只指定輸出目錄、指定完整檔案名稱，或不指定任何項目。 (協助程式工作)|
|[LIB 任務](../msbuild/lib-task.md)|包裝微軟32位庫管理器工具 *（lib.exe*）。|
|[連結任務](../msbuild/link-task.md)|包裝C++連結器工具 *（link.exe*）。|
|[MIDL 任務](../msbuild/midl-task.md)|包裝微軟介面定義語言 （MIDL） 編譯器工具 *（midl.exe*）。|
|[MT 任務](../msbuild/mt-task.md)|包裝微軟清單工具 *（mt.exe*）。|
|[MultiToolTask 工作](../msbuild/multitooltask-task.md)|沒有描述。|
|[ParallelCustomBuild 工作](../msbuild/parallelcustombuild-task.md)|執行 [CustomBuild 工作](../msbuild/custombuild-task.md)的平行執行個體。|
|[RC 任務](../msbuild/rc-task.md)|包裝微軟 Windows 資源編譯器工具 *（rc.exe*）。|
|[設置Env任務](../msbuild/setenv-task.md)|設定或刪除指定環境變數的值。|
|[TrackedVCToolTask 基底類別](../msbuild/trackedvctooltask-base-class.md)|繼承自 [VCToolTask](../msbuild/vctooltask-base-class.md)。|
|[VCMessage 任務](../msbuild/vcmessage-task.md)|在建置期間記錄警告訊息和錯誤訊息。 (不可擴充。 僅供內部使用。)|
|[VCToolTask 基底類別](../msbuild/vctooltask-base-class.md)|繼承自 [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask)。|
|[XDCMake 工作](../msbuild/xdcmake-task.md)|包裝 XML 文檔工具 *（xdcmake.exe），* 該工具將 XML 文檔注釋 *（.xdc*） 檔合併到 *.xml*檔中。|
|[XSD 任務](../msbuild/xsd-task.md)|包裝 XML 架構定義工具 *（xsd.exe），* 該工具從源生成架構或類檔。 *請參閱下面的注釋。*|
|[MSBuild 參考](../msbuild/msbuild-reference.md)|描述 MSBuild 系統的項目。|
|[工作](../msbuild/msbuild-tasks.md)|描述工作，也就是可結合以產生組建的程式碼單位。|
|[任務編寫](../msbuild/task-writing.md)|描述如何建立工作。|

> [!NOTE]
> 從 Visual Studio 2017 開始，*xsd.exe* 的 C++ 專案支援已過時。 您仍然可以將 *CppCodeProvider.dll* 手動新增至 GAC 來使用**Microsoft.VisualC.CppCodeProvider** API。
