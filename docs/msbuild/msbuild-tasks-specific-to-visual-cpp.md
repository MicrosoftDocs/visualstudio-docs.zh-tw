---
title: C + + 特有的 MSBuild 工作 |Microsoft Docs
description: 查看在安裝 c + + 時可用的 MSBuild 工作，MSBuild 會在建立 c + + 程式碼時使用。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 82ba5ad3beb8a676df23cc69184c8766bca72f77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878262"
---
# <a name="msbuild-tasks-specific-to-c"></a>C + + 特有的 MSBuild 工作

提供在建置流程期間執行之程式碼的工作。 安裝 c + + 時，除了使用 MSBuild 安裝的工作之外，還提供下列工作。 如需詳細資訊，請參閱 [MSBuild (c + +) 總覽](/cpp/build/msbuild-visual-cpp-overview)。

 除了適用於每個工作的參數之外，每個工作也會有下列參數。

| 參數 | Description |
|-------------------| - |
| `Condition` | 選擇性的 `String` 參數。<br /><br /> `Boolean`MSBuild 引擎用來判斷是否會執行此工作的運算式。 如需 MSBuild 所支援條件的詳細資訊，請參閱 [條件](../msbuild/msbuild-conditions.md)。 |
| `ContinueOnError` | 選擇性參數。 可包含一或多個下列值：<br /><br /> -   **WarnAndContinue** 或 **true**。 當工作失敗時，[Target](../msbuild/target-element-msbuild.md) 項目中的後續工作與組建都會繼續執行，並將來自工作的所有錯誤視為警告。<br />-   **ErrorAndContinue**。 當工作失敗時，`Target` 項目中的後續工作與組建都會繼續執行，並將來自工作的所有錯誤視為錯誤。<br />-   **ErrorAndStop** 或 **false** (預設) 。 當工作失敗時，就不會執行 `Target` 項目中的其餘工作和組建，並將整個 `Target` 項目與組建視為失敗。<br /><br /> 只有 4.5 版之前的 .NET Framework 版本支援 `true` 和 `false` 值。<br /><br /> 如需詳細資訊，請參閱[如何：忽略工作中的錯誤](../msbuild/how-to-ignore-errors-in-tasks.md)。 |

### <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[BscMake 工作](../msbuild/bscmake-task.md)|包裝 Microsoft Browse Information Maintenance Utility 工具 (*bscmake.exe*)。|
|[CL 工作](../msbuild/cl-task.md)|包裝 c + + 編譯器工具 (*cl.exe*) 。|
|[CPPClean 工作](../msbuild/cppclean-task.md)|刪除建立 c + + 專案時 MSBuild 所建立的暫存檔案。|
|[ClangCompile 工作](../msbuild/clangcompile-task.md)|包裝 c + + 編譯器工具 (*clang.exe*) 。|
|[CustomBuild 工作](../msbuild/custombuild-task.md)|包裝 c + + 編譯器工具 (*cmd.exe*) 。|
|[FXC 工作](../msbuild/fxc-task.md)|在建置流程中使用 HLSL 著色器編譯器。|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|讀取舊的 tlog、寫入新的 tlog，並傳回一組不是最新狀態的項目。 (協助程式工作)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|取得 cl 和其他工具的輸出檔案名稱，其允許只指定輸出目錄、指定完整檔案名稱，或不指定任何項目。 (協助程式工作)|
|[LIB 工作](../msbuild/lib-task.md)|包裝 Microsoft 32 位程式庫管理員工具 (*lib.exe*) 。|
|[Link 工作](../msbuild/link-task.md)|包裝 c + + 連結器工具 (*link.exe*) 。|
|[MIDL 工作](../msbuild/midl-task.md)|包裝 Microsoft 介面定義語言 (MIDL) 編譯器工具 (*midl.exe*) 。|
|[MT 工作](../msbuild/mt-task.md)|包裝 Microsoft 資訊清單工具 (*mt.exe*) 。|
|[MultiToolTask 工作](../msbuild/multitooltask-task.md)|沒有描述。|
|[ParallelCustomBuild 工作](../msbuild/parallelcustombuild-task.md)|執行 [CustomBuild 工作](../msbuild/custombuild-task.md)的平行執行個體。|
|[RC 工作](../msbuild/rc-task.md)|包裝 Microsoft Windows 資源編譯器工具 (*rc.exe*) 。|
|[SetEnv 工作](../msbuild/setenv-task.md)|設定或刪除指定環境變數的值。|
|[TrackedVCToolTask 基底類別](../msbuild/trackedvctooltask-base-class.md)|繼承自 [VCToolTask](../msbuild/vctooltask-base-class.md)。|
|[VCMessage 工作](../msbuild/vcmessage-task.md)|在建置期間記錄警告訊息和錯誤訊息。 (不可擴充。 僅供內部使用。)|
|[VCToolTask 基底類別](../msbuild/vctooltask-base-class.md)|繼承自 [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask)。|
|[XDCMake 工作](../msbuild/xdcmake-task.md)|包裝 XML 檔工具 (*xdcmake.exe*) ，它會將 xml 檔批註 (*.xdc*) 檔合併成 *.xml* 檔案。|
|[XSD 工作](../msbuild/xsd-task.md)|包裝 XML 架構定義工具 (*xsd.exe*) ，它會從來源產生架構或類別檔案。 *請參閱下方注意事項。*|
|[MSBuild 參考](../msbuild/msbuild-reference.md)|描述 MSBuild 系統的項目。|
|[工作](../msbuild/msbuild-tasks.md)|描述工作，也就是可結合以產生組建的程式碼單位。|
|[工作撰寫](../msbuild/task-writing.md)|描述如何建立工作。|

> [!NOTE]
> 從 Visual Studio 2017 開始，*xsd.exe* 的 C++ 專案支援已過時。 您仍然可以將 *CppCodeProvider.dll* 手動新增至 GAC 來使用 **Microsoft.VisualC.CppCodeProvider** API。
