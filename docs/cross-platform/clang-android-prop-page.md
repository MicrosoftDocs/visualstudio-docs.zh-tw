---
title: Clang 專案屬性 (Android C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 663140ea-a568-472b-a79a-dfea8818e06a
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.VCClangCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCClangCompilerTool.DebugInformationFormat
- VC.Project.VCClangCompilerTool.ObjectFile
- VC.Project.VCClangCompilerTool.WarningLevel
- VC.Project.VCClangCompilerTool.WarnAsError
- VC.Project.VCClangCompilerTool.Verbose
- VC.Project.VCClangCompilerTool.Optimization
- VC.Project.VCClangCompilerTool.StrictAliasing
- VC.Project.VCClangCompilerTool.OmitFramePointers
- VC.Project.VCClangCompilerTool.ExceptionHandling
- VC.Project.VCClangCompilerTool.EnableFunctionLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.FloatABI
- VC.Project.VCClangCompilerTool.BufferSecurityCheck
- VC.Project.VCClangCompilerTool.PIC
- VC.Project.VCClangCompilerTool.UseShortEnums
- VC.Project.VCClangCompilerTool.RuntimeTypeInfo
- VC.Project.VCClangCompilerTool.CLanguageStandard
- VC.Project.VCClangCompilerTool.CppLanguageStandard
- VC.Project.VCClangCompilerTool.PreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefineAllPreprocessorDefinitions
- VC.Project.VCClangCompilerTool.ShowIncludes
- VC.Project.VCClangCompilerTool.PrecompiledHeader
- VC.Project.VCClangCompilerTool.PrecompiledHeaderFile
- VC.Project.VCClangCompilerTool.PrecompiledHeaderOutputFileDirectory
- VC.Project.VCClangCompilerTool.PrecompiledHeaderCompileAs
- VC.Project.VCClangCompilerTool.CompileAs
- VC.Project.VCClangCompilerTool.ForcedIncludeFiles
- VC.Project.VCClangCompilerTool.MultiProcessorCompilation
- vc.project.AdditionalOptionsPage
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 8a1fd92a41f145e097615bea4434ea80fd592416
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31067528"
---
# <a name="clang-project-properties-android-c"></a>Clang 專案屬性 (Android C++)

屬性 | 描述 | 選擇
--- | ---| ---
其他 Include 目錄 | 指定一或多個要新增至 Include 路徑中的目錄；如有多個目錄，請使用分號加以分隔。 (-I[路徑])。
偵錯資訊格式 | 指定編譯器所產生的偵錯資訊類型。 | **無** - 因為不產生任何偵錯資訊，所以編譯速度會較快。<br>**完整偵錯資訊 (DWARF2)** - 產生 DWARF2 偵錯資訊。<br>**行號資訊** - 僅產生行號資訊。<br>
物件檔案名稱 | 指定要覆寫預設物件檔案名稱的名稱；可以是檔案或目錄名稱。 (/Fo[名稱])。
警告層級 | 選取您希望編譯器針對程式碼錯誤所產生的嚴謹度等級。  其他旗標會直接新增到 [其他選項]。 (/w, /Weverything)。 | **關閉所有警告** - 停用所有編譯器警告。<br>**啟用所有警告** - 啟用所有警告，包括預設為停用的警告。<br>
將警告視為錯誤 | 將所有編譯器警告視為錯誤。 若是新專案，建議在所有編譯中使用 /WX；解決所有警告時，才能將難以找出的程式碼缺失降至最低。
啟用詳細資訊模式 | 顯示要執行的命令，並使用詳細資訊輸出。
最佳化 | 指定應用程式的最佳化層級。 | **自訂** - 自訂最佳化。<br>**停用** - 停用最佳化。<br>**最小化程式碼** - 大小最佳化。<br>**最快速度** - 速度最佳化。<br>**完整最佳化** - 最費時的最佳化。<br>
嚴格的別名 | 採用最嚴格的別名規則。  一律不會將某種類型的物件與不同類型的物件視為位於相同位址上。
省略框架指標 | 在呼叫堆疊上隱藏框架指標的建立。
啟用 C++ 例外狀況 | 指定編譯器所使用的例外狀況處理模型。 | **否** - 停用例外狀況處理。<br>**是** - 啟用例外狀況處理。<br>**回溯資料表** - 會產生任何必要的靜態資料，但不會影響已產生的程式碼。<br>
啟用函式階層連結 | 允許編譯器以封裝函式 (COMDAT) 的形式來封裝個別函式。 需要此項目才能使用編輯後繼續功能。     (ffunction-sections)。
啟用資料層級連結 | 可讓連結器最佳化，透過在個別的區段中發出每個資料項目，來移除未使用的資料。
啟用進階 SIMD (Neon) | 可產生適用於 NEON 浮點硬體的程式碼。 這僅適用於 ARM 架構。
浮點 ABI | 用於選擇浮點 ABI 的選項。 | **軟性** -「軟性」可使編譯器產生輸出，以包含浮點運算的程式庫呼叫。<br>**SoftFP** -「SoftFP」允許使用硬體浮點指示產生程式碼，但是仍然使用軟浮點呼叫慣例。<br>**硬性** -「硬性」允許產生浮點指示，並使用 FPU 特定的呼叫慣例。<br>
安全性檢查 | 安全性檢查可協助偵測是否發生堆疊緩衝區滿溢的情況，這是駭客經常嘗試攻擊的程式安全性漏洞。 (fstack-protector)。 | **停用安全性檢查** - 停用安全性檢查。<br>**啟用安全性檢查** - 啟用安全性檢查。 (fstack-protector)<br>
位置獨立程式碼 | 產生位置獨立程式碼 (PIC) 以用於共用程式庫。
使用短列舉 | 列舉類型只會使用可能值的輸入集所需的位元組數。
啟用執行階段類型資訊 | 新增在執行階段用於檢查 C++ 物件類型的程式碼 (執行階段類型資訊)。     (frtti、fno-rtti)
C 語言標準 | 決定 C 語言標準。 | **Default**<br>**C89** - C89 語言標準。<br>**C99** - C99 語言標準。<br>**C11** - C11 語言標準。<br>**C99 (GNU 方言)** - C99 (GNU 方言) 語言標準。<br>**C11 (GNU 方言)** - C11 (GNU 方言) 語言標準。<br>
C + + 語言標準 | 決定 C++ 語言標準。 | **Default**<br>**C++03** - C++03 語言標準。<br>**C++11** - C++11 語言標準。<br>**C++14** - C++14 語言標準。<br>**C++03 (GNU 方言)** - C++03 (GNU 方言) 語言標準。<br>**C++11 (GNU 方言)** - C++11 (GNU 方言) 語言標準。<br>**C++14 (GNU 方言)** - C++14 (GNU 方言) 語言標準。<br>
前置處理器定義 | 定義來源檔案的前置處理符號。 (-D)
取消前置處理器的定義 | 指定取消一或多個前置處理器的定義。  (-U [巨集])
取消所有前置處理器的定義 | 取消所有先前定義的前置處理器值。  (-undef)
顯示 Include | 產生 Include 檔清單以及編譯器輸出。  (-H)
先行編譯標頭 | 建立/使用先行編譯標頭：啟用在建置期間建立或使用先行編譯標頭。 | **使用** - 使用先行編譯標頭檔。<br>**不使用** - 不使用先行編譯標頭檔。<br>
先行編譯標頭檔 | 指定要用於先行編譯標頭檔的標頭檔名稱。 這個檔案也會在建置期間新增至「強制 Include 檔」
先行編譯標頭檔輸出檔案目錄 | 指定所產生的先行編譯標頭檔目錄。 這個目錄也會在建置期間新增至「其他 Include 目錄」
將先行編譯標頭檔編譯為 | 選取先行編譯標頭檔的編譯語言選項 (-x c-header、-x c++-header)。 | **編譯成 C 程式碼** - 編譯成 C 程式碼。<br>**編譯成 C++ 程式碼** - 編譯成 C++ 程式碼。<br>
編譯為 | 選取 .c 和 .cpp 檔的編譯語言選項。  'Default' 會根據 .c 或 .cpp 副檔名進行偵測。 (-x c、-x c++) | **預設** - 預設值。<br>**編譯成 C 程式碼** - 編譯成 C 程式碼。<br>**編譯成 C++ 程式碼** - 編譯成 C++ 程式碼。<br>
強制 Include 檔案 | 一或多個強制 Include 檔案。     (-include [名稱])
多處理器編譯 | 多處理器編譯。
其他選項 | 其他選項。
