---
title: RC 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- vc.task.rc
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- RC task (MSBuild (C++))
- MSBuild (C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13ae844759cb73de6dc7bcce6c8898c21132f9d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632910"
---
# <a name="rc-task"></a>RC 工作

包裝 Microsoft Windows 資源編譯器工具 (*rc.exe*)。 **RC** 工作會將游標、圖示、點陣圖、對話方塊和字型等資源編譯為資源 (*.res*) 檔案。 如需詳細資訊，請參閱[資源編譯器](/windows/desktop/menurc/resource-compiler) \(英文\)。

## <a name="parameters"></a>參數

 下表說明 RC 工作的參數。 大部分的工作參數以及數組參數會對應到命令列選項。

|參數|描述|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|可選**字串*** 參數。<br /><br /> 將目錄加入至要搜尋 include 檔案的目錄清單。<br /><br /> 如需詳細資訊，請參閱[使用 RC (RC 命令列)](/windows/win32/menurc/using-rc-the-rc-command-line-) \(英文\) 中的 **/I** 選項。|
|**AdditionalOptions**|可選**字串**參數。<br /><br /> 命令列選項清單，例如 /\<option1> /\<option2> /\<option#>。 使用此參數，來指定任何其他 **RC** 工作參數未表示的命令列選項。<br /><br /> 如需詳細資訊，請參閱[使用 RC (RC 命令列)](/windows/win32/menurc/using-rc-the-rc-command-line-) \(英文\) 中的選項。|
|**文化特性**|可選**字串**參數。<br /><br /> 指定代表資源中所使用文化特性 (Culture) 的地區設定識別碼。<br /><br /> 如需詳細資訊，請參閱[使用 RC (RC 命令列)](/windows/win32/menurc/using-rc-the-rc-command-line-) \(英文\) 中的 **/l** 選項。|
|**IgnoreStandardIncludePath**|可選**布林參數**。<br /><br /> 如果 `true`，可防止資源編譯器在搜尋標題檔或資源檔時檢查 INCLUDE 環境變數。<br /><br /> 如需詳細資訊，請參閱[使用 RC (RC 命令列)](/windows/win32/menurc/using-rc-the-rc-command-line-) \(英文\) 中的 **/x** 選項。|
|**NullTerminateStrings**|可選**布林參數**。<br /><br /> 如果 `true`，null 會終止字串資料表中的所有字串。<br /><br /> 如需詳細資訊，請參閱[使用 RC (RC 命令列)](/windows/win32/menurc/using-rc-the-rc-command-line-) \(英文\) 中的 **/n** 選項。|
|**PreprocessorDefinitions**|可選**字串*** 參數。<br /><br /> 定義資源編譯器的一或多個前置處理器符號。 指定巨集符號清單。<br /><br /> 如需詳細資訊，請參閱[使用 RC (RC 命令列)](/windows/win32/menurc/using-rc-the-rc-command-line-) \(英文\) 中的 **/d** 選項。 另請參閱此表格中的 **UndefinePreprocessorDefinitions**。|
|**ResourceOutputFileName**|可選**字串**參數。<br /><br /> 指定資源檔的名稱。 指定資源檔名稱。<br /><br /> 如需詳細資訊，請參閱[使用 RC (RC 命令列)](/windows/win32/menurc/using-rc-the-rc-command-line-) \(英文\) 中的 **/fo** 選項。|
|**顯示進度**|可選**布林參數**。<br /><br /> 如果 `true`，則會顯示報告編譯器進度的訊息。<br /><br /> 如需詳細資訊，請參閱[使用 RC (RC 命令列)](/windows/win32/menurc/using-rc-the-rc-command-line-) \(英文\) 中的 **/v** 選項。|
|**來源**|必要的 `ITaskItem[]` 參數。<br /><br /> 定義工作可以耗用和發出的 MSBuild 來源檔案項目的陣列。|
|**SuppressStartupBanner**|可選**布林參數**。<br /><br /> 如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。<br /><br /> 如需詳細資訊，請鍵入 **/?** 命令列選項，然後參閱 **/nologo** 選項。|
|**TrackerLogDirectory**|可選**字串**參數。<br /><br /> 指定追蹤器記錄目錄。|
|**UndefinePreprocessorDefinitions**|取消定義前置處理器符號。<br /><br /> 如需詳細資訊，請參閱[使用 RC (RC 命令列)](/windows/win32/menurc/using-rc-the-rc-command-line-) \(英文\) 中的 **/u** 選項。 另請參閱此表格中的 **PreprocessorDefinitions**。|

## <a name="see-also"></a>另請參閱

- [任務引用](../msbuild/msbuild-task-reference.md)