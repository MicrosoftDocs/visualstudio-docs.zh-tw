---
title: 設定 C++ IntelliSense 專案
description: 瞭解如何使用 Visual Studio IDE 來手動設定 c + + 專案，使 IntelliSense 可以正常運作，以協助您找出並修正 IntelliSense 問題。
ms.custom: SEO-VS-2020
ms.date: 10/08/2018
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 34be73203f5c1d01e4674e7892e0f89d4aae4816
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96478792"
---
# <a name="configure-a-c-project-for-intellisense"></a>設定 C++ IntelliSense 專案

在某些情況下，您可能需要手動設定 C++ 專案來使 IntelliSense 能夠正常運作。 針對 MSBuild 專案 (以 .vcxproj 檔案為基礎)，您可以調整專案屬性中的設定。 針對非 MSBuild 的專案，您需要調整專案根目錄中的 CppProperties.json 檔案中的設定。 在某些情況下，您可能需要建立提示檔案以協助 IntelliSense 了解巨集定義。 Visual Studio IDE 可協助您識別並修正 IntelliSense 問題。

## <a name="single-file-intellisense"></a>單一檔案 IntelliSense

當您開啟沒有包含在專案中的檔案時，Visual Studio 雖然能提供一些 IntelliSense 支援，但預設不會顯示任何錯誤波浪線。 如果 [瀏覽列] 顯示 [其他檔案]，那大概便能說明為何您無法在錯誤的程式碼底下看見錯誤波浪線，或是為何沒有定義前置處理器巨集。

## <a name="check-the-error-list"></a>檢查錯誤清單

如果檔案沒有以單一檔案模式開啟，且 IntelliSense 無法正常運作，您應該先檢查 [錯誤清單] 視窗。 若要查看目前來源檔案的所有 IntelliSense 錯誤，並搭配所有包含的標頭檔案，請選擇下拉式清單中的 [組建 + IntelliSense]：

![[錯誤清單] 中的 VC++ IntelliSense](media/vcpp-intellisense-error-list.png)

IntelliSense 能產生最多 1000 個錯誤。 如果來源檔案所包含的標頭檔案中有超過 1000 個錯誤，則來源檔案只會在檔案的最前方顯示單一錯誤波浪線。

## <a name="ensure-include-paths-are-correct"></a>確定 #include 路徑正確無誤

### <a name="msbuild-projects"></a>MSBuild 專案

如果您是在 Visual Studio IDE 之外執行組建，且該組建能成功執行，但 IntelliSense 不正確，則您的命令列與專案設定之間可能有一或多個設定沒有正確同步。 請在 [方案總管] 中以滑鼠右鍵按一下專案節點，然後確定所有 **#include** 路徑針對目前設定和平台皆正確無誤。 如果路徑在所有設定和平台中皆完全相同，您可以選取 [所有組態] 和 [所有平台]，然後確認路徑皆正確無誤。

![VC++ [Include 目錄]](media/vcpp-intellisense-include-paths.png)

若要查看組建巨集 (例如 **VC_IncludePath**) 目前的值，請選取 [Include 目錄] 行，然後按一下右側的下拉式清單。 然後 **\<Edit>** ，選擇並按一下 [ **宏** ] 按鈕。

### <a name="makefile-projects"></a>Makefile 專案

針對以 NMake 專案範本為基礎的 Makefile 專案，請選擇左側窗格中的 [NMake]，然後選擇 [IntelliSense] 類別下的 [包含搜尋路徑]：

![Makefile 專案包含路徑](media/vcpp-intellisense-makefile-include-paths.png)

### <a name="open-folder-projects"></a>「開啟資料夾」專案

針對 CMake 專案，請確定已針對 CMakeLists.txt 中的所有設定正確指定 #include 路徑。 其他專案類型可能會需要 CppProperties.json 檔案。 如需詳細資訊，請參閱[使用 CppProperties.json 設定 IntelliSense](/cpp/build/open-folder-projects-cpp#configure-code-navigation-with-cpppropertiesjson)。 確定定義於檔案中之每個設定的路徑皆正確無誤。

如果 CppProperties.json 檔案中有語法錯誤，受影響檔案中的 IntelliSense 將會不正確。 Visual Studio 將會在 [輸出視窗] 中顯示該錯誤。

## <a name="tag-parser-issues"></a>標記剖析器問題

標記剖析器是「模糊」的 C++ 剖析器，能用來進行瀏覽和巡覽。 它的速度很快，但不會嘗試完全理解每個程式碼建構。

例如，它不會評估前置處理器巨集，因此它可能會錯誤地剖析會大量使用那些巨集的程式碼。 當標記剖析器遇到不熟悉的程式碼建構時，它可能會略過該程式碼的整個區域。

在 Visual Studio 中，有兩種常見的方式會產生此問題：

1. 如果 [導覽列] 顯示的是最內層的巨集，便代表已略過目前的函式定義：

   ![標記剖析器略過函式定義](media/vcpp-intellisense-tag-parser-macro.png)

1. IDE 針對已經定義的函式向您建議建立函式定義：

   ![標記剖析器建議定義現有函式](media/vcpp-intellisense-tag-parser-function.png)

若要修正此類問題，請將名為 **cpp.hint** 的檔案新增到您方案目錄的根目錄。 如需詳細資訊，請參閱[提示檔案](/cpp/build/reference/hint-files)。

[錯誤清單] 視窗中出現標記剖析器錯誤。

## <a name="validate-project-settings-with-diagnostic-logging"></a>搭配診斷記錄驗證專案設定

若要檢查 IntelliSense 編譯器是否使用正確的編譯器選項 (包括 Include 路徑和前置處理器巨集)，請在 [工具] > [選項] > [文字編輯器] > [C/C++] > [進階] > [診斷記錄] 中開啟對 IntelliSense 命令列的診斷記錄。 將 [啟用記錄] 設定為 True、將 [記錄層次] 設定為 5 (最詳細)，以及將 [記錄篩選器] 設定為 8 (IntelliSense 記錄)。

[輸出視窗] 現在將會顯示傳遞至 IntelliSense 編譯器的命令列。 以下是範例輸出：

```output
[IntelliSense] Configuration Name: Debug|Win32
[IntelliSense] Toolset IntelliSense Identifier:
[IntelliSense] command line options:
/c
/I.
/IC:\Repo\Includes
/DWIN32
/DDEBUG
/D_DEBUG
/Zc:wchar_t-
/Zc:forScope
/Yustdafx.h
```

此資訊可能可以協助您了解 IntelliSense 提供不正確資訊的原因。 例如，如果您專案的 Include 目錄包含 **$(MyVariable)\Include**，而診斷記錄顯示 **/I\Include** 為 Include 路徑，這代表系統沒有評估 **$(MyVariable)**，並已將它從最終的 Include 路徑中移除。

## <a name="about-the-intellisense-build"></a>關於 IntelliSense 組建

Visual Studio 使用專用的 C++ 編譯器來建立並維護提供所有 IntelliSense 功能的資料庫。 為了使 IntelliSense 資料庫與程式碼保持同步，Visual Studio 會自動啟動僅限 IntelliSense 的組建作為背景工作，以回應在專案設定或來源檔案中所做的某些變更。

不過，在某些情況下，Visual Studio 可能會無法及時更新 IntelliSense 資料庫。 例如，當您執行 **git pull** 或 **git checkout** 命令時，Visual Studio 可能需要最多一小時的時間才能偵測到檔案中的變更。 您可以在 [方案總管] 中以滑鼠右鍵按一下專案節點，然後選擇 [重新掃描方案]，來強制重新掃描方案中的所有檔案。

## <a name="troubleshooting-intellisense-build-failures"></a>對 IntelliSense 組建失敗進行疑難排解

IntelliSense 組建並不會產生二進位檔，但它仍可能會失敗。 其中一個可能的失敗原因是自訂的 .props 或 .targets 檔案。 在 Visual Studio 2017 15.6 版和更新版本中，會將僅限 IntelliSense 的組建錯誤記錄至 [輸出] 視窗。 若要查看它們，請將 [顯輸出來源] 設定為 [方案]：

![顯示 [方案] 錯誤的 [輸出] 視窗](media/vcpp-intellisense-output-window.png)

錯誤訊息可能會指示您啟用設計階段追蹤：

```output
error: Designtime build failed for project 'E:\src\MyProject\MyProject.vcxproj',
configuration 'Debug|x64'. IntelliSense might be unavailable.
Set environment variable TRACEDESIGNTIME=true and restart
Visual Studio to investigate.
```

如果您將環境變數 TRACEDESIGNTIME 設定為 true，然後重新啟動 Visual Studio，您將會在 %TEMP% 目錄中看見記錄檔，它可能可以協助診斷組建失敗。

若要深入了解 TRACEDESIGNTIME 環境變數，請參閱 [Roslyn](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Diagnosing-Project-System-Build-Errors.md) \(英文\) 與[常見專案系統](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md) \(英文\)。 這些文章中的資訊皆與 C++ 專案相關。

## <a name="see-also"></a>另請參閱

- [Visual C++ IntelliSense](visual-cpp-intellisense.md)
