---
title: ClangCompile 工作 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.clangcompile
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), ClangCompile task
- ClangCompile task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 218ef07fa3b086a2240362011067bf526088d1f4
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515307"
---
# <a name="clangcompile-task"></a>ClangCompile 工作

包裝 Visual C++ 編譯器工具 (clang.exe)。

## <a name="parameters"></a>參數

下表說明 **ClangCompile** 工作的參數。

|參數|說明|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|選擇性的 **string[]** 參數。<br/><br/>指定一或多個要新增至 Include 路徑中的目錄；如有多個目錄，請使用分號加以分隔。<br/><br/>使用 `-I[path]`。|
|**AdditionalOptions**|選擇性的 **string** 參數。|
|**BufferSecurityCheck**|選擇性的 **string** 參數。<br/><br/>安全性檢查可協助偵測是否發生堆疊緩衝區滿溢的情況，這是駭客經常嘗試攻擊的程式安全性漏洞。 <br/><br/>使用 `fstack-protector`。|
|**BuildingInIde**|選擇性的 **bool** 參數。|
|**CLanguageStandard**|選擇性的 **string** 參數。<br/><br/>決定 C 語言標準。<br/><br/>使用值為 **c89**、**c99**、**c11**、**gnu99** 或 **gnu11** 的 `std=[value]`。|
|**ClangVersion**|選擇性的 **string** 參數。|
|**CompileAs**|選擇性的 **string** 參數。<br/><br/>選取 .c 和 .cpp 檔的編譯語言選項。 預設將根據 .c 或 .cpp 副檔名進行偵測。<br/><br/>使用 `-x c`、`-x c++`。|
|**CppLanguageStandard**|選擇性的 **string** 參數。<br/><br/>決定 C++ 語言標準。<br/><br/>使用值為 **c++98**、**c++11**、**c++1y**、**gnu++98**、**gnu++11** 或 **gnu++1y** 的 `std=[value]`。|
|**DataLevelLinking**|選擇性的 **bool** 參數。<br/><br/>可讓連結器最佳化，透過在個別的區段中發出每個資料項目，來移除未使用的資料。|
|**DebugInformationFormat**|選擇性的 **string** 參數。<br/><br/>指定編譯器所產生的偵錯資訊類型。<br/><br/>**None**，不產生任何偵錯資訊，因此編譯速度可能比較快 (使用 `g0`)。<br/>**FullDebug**，產生 DWARF2 偵錯資訊 (使用 `g2 -gdwarf-2`)。<br/>**LineNumber**，僅產生行號資訊 (使用 `gline-tables-only`)。|
|**EnableNeonCodegen**|選擇性的 **bool** 參數。<br/><br/>可產生適用於 NEON 浮點硬體的程式碼。 這僅適用於 ARM 架構。|
|**ExceptionHandling**|選擇性的 **string** 參數。<br/><br/>指定編譯器所使用的例外狀況處理模型。<br/><br/>**Disabled**，停用例外狀況處理 (使用 `fno-exceptions`)。<br/>**Enabled**，啟用例外狀況處理 (使用 `fexceptions`)。<br/>**UnwindTables**，產生任何必要的靜態資料，但不會影響已產生的程式碼 (使用 `funwind-tables`)。|
|**FloatABI**|選擇性的 **string** 參數。<br/><br/>用於選擇浮點 ABI 的選項。<br/><br/>**soft**，導致編譯器產生輸出，其中包含浮點運算的程式庫呼叫 (使用 `mfloat-abi=soft`)。<br/>**softfp**，允許使用硬體浮點指示來產生程式碼，但仍使用軟浮點呼叫慣例 (使用 `mfloat-abi=softfp`)。<br/>**hard**，允許產生浮點指示，並使用 FPU 特定的呼叫慣例 (使用 `mfloat-abi=hard`)。|
|**ForcedIncludeFiles**|選擇性的 **string[]** 參數。<br/><br/>一或多個強制的 Include 檔案。<br/><br/>使用 `-include [name]`。|
|**FunctionLevelLinking**|選擇性的 **bool** 參數。<br/><br/>允許編譯器以封裝函式 (COMDAT) 的形式來封裝個別函式。 需要此項目才能使用編輯後繼續功能。<br/><br/>使用 `ffunction-sections`。|
|**GccToolChain**|選擇性的 **string** 參數。<br/><br/>Gcc 工具鏈的資料夾路徑。|
|**GNUMode**|選擇性的 **bool** 參數。<br/><br/>|
|**MSCompatibility**|選擇性的 **bool** 參數。<br/><br/>啟用完整 Microsoft Visual C++ 相容性。|
|**MSCompatibilityVersion**|選擇性的 **string** 參數。<br/><br/>以點分隔的值，代表要在 _MSC_VER 中回報的 Microsoft 編譯器版本號碼 (0 = 不要定義 (預設))。|
|**MSExtensions**|選擇性的 **bool** 參數。<br/><br/>接受 Microsoft 編譯器所支援的部分非標準建構。|
|**MSCompilerVersion**|選擇性的 **string** 參數。<br/><br/>要在 _MSC_VER 中回報的 Microsoft 編譯器版本號碼 (0 = 不要定義 (預設))。|
|**MSVCErrorReport**|選擇性的 **bool** 參數。<br/><br/>回報錯誤，讓 Visual Studio 可用以剖析檔案與行資訊。|
|**ObjectFileName**|選擇性的 **string** 參數。<br/><br/>指定要覆寫預設物件檔案名稱的名稱；可以是檔案或目錄名稱。<br/><br/>使用 `/Fo[name]`。|
|**OmitFramePointers**|選擇性的 **bool** 參數。<br/><br/>在呼叫堆疊上隱藏框架指標的建立。|
|**Optimization**|選擇性的 **string** 參數。<br/><br/>指定應用程式的最佳化層級。<br/><br/>**Custom**，自訂最佳化。<br/>**Disabled**，停用最佳化 (使用 `O0`)。<br/>**MinSize**，針對大小進行最佳化 (使用 `Os`)。<br/>**MaxSpeed**，針對速度進行最佳化 (使用 `O2`)。<br/>**Full**，最佳化相當耗時 (使用 `O3`)。|
|**PositionIndependentCode**|選擇性的 **bool** 參數。<br/><br/>產生位置獨立程式碼 (PIC) 以用於共用程式庫。|
|**PrecompiledHeader**|選擇性的 **string** 參數。<br/><br/>啟用在建置期間建立或使用先行編譯標頭檔。|
|**PrecompiledHeaderFile**|選擇性的 **string** 參數。<br/><br/>指定要用於先行編譯標頭檔的標頭檔名稱。 這個檔案也會在建置期間新增至**強制的 Include 檔案**。|
|**PrecompiledHeaderOutputFileDirectory**|選擇性的 **string** 參數。<br/><br/>指定所產生的先行編譯標頭檔目錄。 這個目錄也會在建置期間新增至**其他 Include 目錄**。|
|**PrecompiledHeaderCompileAs**|選擇性的 **string** 參數。<br/><br/>選取適用於先行編譯標頭檔的編譯語言選項。<br/><br/>使用 `-x c-header`、`-x c++-header`。|
|**PreprocessorDefinitions**|選擇性的 **string[]** 參數。<br/><br/>定義來源檔案的前置處理符號。<br/><br/>使用 `-D`。|
|**RuntimeLibrary**|選擇性的 **string** 參數。<br/><br/>指定連結的執行階段程式庫。<br/><br/>使用 `MSVC /MT`、`/MTd`、`/MD`、`/MDd` 參數。<br/><br/>**MultiThreaded**，導致您的應用程式使用多執行緒、靜態版本的執行階段程式庫。<br/>**MultiThreadedDebug**，定義 _DEBUG 和 _MT。 這個選項也會讓編譯器將程式庫名稱 LIBCMTD.lib 放入 .obj 檔中，使連結器可以使用 LIBCMTD.lib 解析外部符號。<br/>**MultiThreadedDLL**，導致您的應用程式使用多執行緒與 DLL 特定版本的執行階段程式庫。 定義 _MT 和 _DLL，並導致編譯器將程式庫名稱 MSVCRT.lib 放入 .obj 檔。<br/>**MultiThreadedDLL**，定義 _DEBUG、_MT 及 _DLL，並導致您的應用程式使用偵錯多執行緒與 DLL 特定版本的執行階段程式庫。 它也會讓編譯器將程式庫名稱 MSVCRTD.lib 放入 .obj 檔中。|
|**RuntimeTypeInfo**|選擇性的 **bool** 參數。<br/><br/>新增在執行階段用於檢查 C++ 物件類型的程式碼 (執行階段類型資訊)。<br/><br/>使用 `frtti`、`fno-rtti`。|
|**ShowIncludes**|選擇性的 **bool** 參數。<br/><br/>產生 Include 檔清單以及編譯器輸出。<br/><br/>使用 `-H`。|
|**Sources**|必要的 **ITaskItem[]** 參數。|
|**StrictAliasing**|選擇性的 **bool** 參數。<br/><br/>採用最嚴格的別名規則。 一律不會將某種類型的物件與不同類型的物件視為位於相同位址上。|
|**Sysroot**|選擇性的 **string** 參數。<br/><br/>標頭與程式庫根目錄的資料夾路徑。|
|**TargetArch**|選擇性的 **string** 參數。<br/><br/>目標架構。|
|**ThumbMode**|選擇性的 **string** 參數。<br/><br/>產生為 Thumb 微架構所執行的程式碼。 這僅適用於 ARM 架構。<br/><br/>**Thumb**，產生 Thumb 程式碼 (使用 `mthumb`)。<br/>**ARM**，產生 Arm 程式碼 (使用 `marm`)。<br/>**Disabled**，選項不適用於所選平台。|
|**TrackerLogDirectory**|選擇性的 **string** 參數。<br/><br/>追蹤器記錄檔目錄。|
|**TreatWarningAsError**|選擇性的 **bool** 參數。<br/><br/>將所有編譯器警告視為錯誤。<br/><br/>若是新專案，建議在所有編譯中使用 `/WX`；解決所有警告時，才能將難以找出的程式碼缺失降至最低。|
|**UndefinePreprocessorDefinitions**|選擇性的 **string[]** 參數。<br/><br/>指定取消一或多個前置處理器的定義。<br/><br/>使用 `-U [macro]`。|
|**UndefineAllPreprocessorDefinitions**|選擇性的 **bool** 參數。<br/><br/>取消所有先前定義的前置處理器值。<br/><br/>使用 `-undef`。|
|**UseMultiToolTask**|選擇性的 **bool** 參數。<br/><br/>多處理器編譯。|
|**UseShortEnums**|選擇性的 **bool** 參數。<br/><br/>列舉類型只會使用可能值的輸入集所需的位元組數。|
|**Verbose**|選擇性的 **bool** 參數。<br/><br/>顯示要執行的命令，並使用詳細資訊輸出。|
|**WarningLevel**|選擇性的 **string** 參數。<br/><br/>選取您希望編譯器針對程式碼錯誤所產生的嚴謹度等級。 其他旗標應該直接新增到 [其他選項] (請參閱 `/w`、`/Weverything`)。<br/><br/>**TurnOffAllWarnings**，停用所有編譯器警告 (使用 `w`)。<br/>**EnableAllWarnings**，啟用所有警告，包括預設為停用的警告 (使用 `Wall`)。|

## <a name="see-also"></a>另請參閱

[工作參考](../msbuild/msbuild-task-reference.md)