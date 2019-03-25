---
title: FXC 工作 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.fxc
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), FXC task
- FXC task (MSBuild (Visual C++))
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: a0854835c1562c0797394395f07708cd0eab710d
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070395"
---
# <a name="fxc-task"></a>FXC 工作

在建置流程中使用 HLSL 著色器編譯器。

## <a name="parameters"></a>參數

下表說明 **FXC** 工作的參數。

|參數|說明|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|選擇性的 **string[]** 參數。<br/><br/>指定一或多個要新增至 Include 路徑中的目錄；如有多個目錄，請使用分號加以分隔。<br/><br/>使用 `/I[path]`。|
|**AdditionalOptions**|選擇性的 **string** 參數。|
|**AllResourcesBound**|選擇性的 **bool** 參數。<br/><br/>編譯器將假設在著色器執行期間，著色器可能參考的所有資源都已繫結且處於良好狀態。 適用於著色器模型 5.1 (含) 以上版本。<br/><br/>使用 `/all_resources_bound`。|
|**AssemblerOutput**|選擇性的 **string** 參數。<br/><br/>指定組合語言輸出檔案的內容。<br/><br/>使用 `/Fc, /Fx`。<br/><br/>**NoListing**<br/>**AssemblyCode**，使用 `Fc`。<br/>**AssemblyCodeAndHex**，使用 `Fx`。|
|**AssemblerOutputFile**|選擇性的 **string** 參數。<br/><br/>指定組譯碼清單檔的檔案名稱。|
|**CompileD2DCustomEffect**|選擇性的 **bool** 參數。<br/><br/>編譯包含像素著色器的 Direct2D 自訂效果。 請勿用於頂點或計算自訂效果。|
|**ConsumeExportFile**|選擇性的 **string** 參數。|
|**DisableOptimizations**|選擇性的 **bool** 參數。<br/><br/>停用最佳化。<br/><br/>儘管輸出可能與 `/Od /Gfp` 不同，但 `/Od` 意指 `/Gfp`。|
|**EnableDebuggingInformation**|選擇性的 **bool** 參數。<br/><br/>啟用偵錯資訊。|
|**EnableUnboundedDescriptorTables**|選擇性的 **bool** 參數。<br/><br/>告知編譯器，著色器可能包含未繫結範圍的資源陣列宣告。 適用於著色器模型 5.1 (含) 以上版本。<br/><br/>使用 `/enable_unbounded_descriptor_tables`。|
|**EntryPointName**|選擇性的 **string** 參數。<br/><br/>指定著色器的進入點名稱。<br/><br/>使用 `/E[name]`。|
|**GenerateExportFile**|選擇性的 **string** 參數。|
|**GenerateExportShaderProfile**|選擇性的 **string** 參數。|
|**HeaderFileOutput**|選擇性的 **string** 參數。<br/><br/>指定包含目的碼的標頭檔名稱。<br/><br/>使用 `/Fh [name]`。|
|**ObjectFileOutput**|選擇性的 **string** 參數。<br/><br/>指定目的檔的名稱。<br/><br/>使用 `/Fo [name]`。|
|**PreprocessorDefinitions**|選擇性的 **string[]** 參數。<br/><br/>定義原始程式檔的前置處理符號。|
|**SetRootSignature**|選擇性的 **string** 參數。<br/><br/>將根簽章附加到著色器位元組程式碼。 適用於著色器模型 5.0 (含) 以上版本。<br/><br/>使用 `/setrootsignature`。|
|**ShaderModel**|選擇性的 **string** 參數。<br/><br/>指定著色器模型。 某些著色器類型只能搭配最新的著色器模型使用。<br/><br/>使用 `/T [type]_[model]`。|
|**ShaderType**|選擇性的 **string** 參數。<br/><br/>指定著色器類型。<br/><br/>使用 `/T [type]_[model]`。<br/><br/>**Effect**，使用 `fx`。<br/>**Vertex**，使用 `vs`。<br/>**Pixel**，使用 `ps`。<br/>**Geometry**，使用 `gs`。<br/>**Hull**，使用 `hs`。<br/>**Domain**，使用 `ds`。<br/>**Compute**，使用 `cs`。<br/>**Library**，使用 `lib`。<br/>**RootSignature**，產生根簽章物件。|
|**來源**|必要的 **ITaskItem** 參數。|
|**SuppressStartupBanner**|選擇性的 **bool** 參數。<br/><br/>隱藏程式啟始資訊及資訊訊息。<br/><br/>使用 `/nologo`。|
|**TrackerLogDirectory**|選擇性的 **string** 參數。|
|**TreatWarningAsError**|選擇性的 **bool** 參數。<br/><br/>將所有編譯器警告視為錯誤。<br/><br/>若是新專案，建議在所有編譯中使用 `/WX`；解決所有警告時，才能將難以找出的程式碼缺失降至最低。|
|**VariableName**|選擇性的 **string** 參數。<br/><br/>指定標頭檔中變數名稱的名稱。<br/><br/>使用 `/Vn [name]`。|

## <a name="see-also"></a>另請參閱

[工作參考](../msbuild/msbuild-task-reference.md)