---
title: XDCMake 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 Xdcmake.exe 工作包裝 XML 檔工具 xdcmake.exe，這會將 XML 檔批註檔案合併至 .xml 檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (C++))
- MSBuild (C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a867146d48b5ba6c4bfb2ac33b45c505b6f6c37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971046"
---
# <a name="xdcmake-task"></a>XDCMake 工作

包裝 XML 檔工具 (*xdcmake.exe*) ，它會將 xml 檔批註 (*.xdc*) 檔合併成 *.xml* 檔案。

 當您在 c + + 原始程式碼中提供檔批註，並使用 [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp)編譯器選項進行編譯時，就會建立一個 *.xdc 檔案。* 如需詳細資訊，請參閱 *xdcmake.exe* 的 [Xdcmake.exe 參考](/cpp/build/reference/xdcmake-reference)、 [XML 檔產生器工具屬性頁](/cpp/build/reference/xml-document-generator-tool-property-pages)和命令列說明選項 (**/？**) 。

## <a name="remarks"></a>備註

 根據預設， *xdcmake.exe* 工具支援一些命令列選項。 當您指定 **/old** 命令列選項時，可支援額外的選項。

## <a name="parameters"></a>參數

 下表說明 **XDCMake** 工作的參數。

|參數|Description|
|---------------|-----------------|
|**AdditionalDocumentFile**|選擇性的 **String []** 參數。<br /><br /> 指定要合併的一或多個其他 *.xdc* 檔案。<br /><br /> 如需詳細資訊，請參閱 XML 檔產生器 [工具屬性頁](/cpp/build/reference/xml-document-generator-tool-property-pages)中的 **其他檔** 檔描述。 另請參閱 *xdcmake.exe* 的 **/old** 和 **/Fs** 命令列選項。|
|**AdditionalOptions**|選擇性的 **字串** 參數。<br /><br /> 選項的清單，如命令列上所指定。 例如，/ \<option1>  / \<option2>  / \<option#> 。 使用這個參數來指定任何其他 **XDCMake** 工作參數未表示的選項。<br /><br /> 如需詳細資訊，請參閱 [XDCMake 參考](/cpp/build/reference/xdcmake-reference)、[XML 文件產生器工具屬性頁](/cpp/build/reference/xml-document-generator-tool-property-pages)，以及 *xdcmake.exe* 的命令列說明 (**/?**)。|
|**DocumentLibraryDependencies**|選擇性的 **布林值** 參數。<br /><br /> 如果 `true` 和目前的專案相依于方案中的靜態程式庫 (*.Lib*) 專案，則該程式庫專案的 *.xdc* 檔會包含在目前專案的 *.xml* 檔案輸出中。<br /><br /> 如需詳細資訊，請參閱 XML 檔產生器 [工具屬性頁](/cpp/build/reference/xml-document-generator-tool-property-pages)中的 **文件庫** 相依性描述。|
|**OutputFile**|選擇性的 **字串** 參數。<br /><br /> 覆寫預設輸出檔案名稱。 預設名稱衍生自所處理的第一個 *.xdc* 檔案的名稱。<br /><br /> 如需詳細資訊，請參閱 [xdcmake.exe 參考](/cpp/build/reference/xdcmake-reference)中的 **/out： \<filename>** 選項。 另請參閱 *xdcmake.exe* 的 **/old** 和 **/fo** 命令列選項。|
|**ProjectName**|選擇性的 **字串** 參數。<br /><br /> 目前專案的名稱。|
|**SlashOld**|選擇性的 **布林值** 參數。<br /><br /> 如果為，則會 `true` 啟用其他 *xdcmake.exe* 選項。<br /><br /> 如需詳細資訊，請參閱 *xdcmake.exe* 的 **/old** 命令列選項。|
|**來源**|必要的 `ITaskItem[]` 參數。<br /><br /> 定義工作可以耗用和發出的 MSBuild 來源檔案項目的陣列。|
|**SuppressStartupBanner**|選擇性的 **布林值** 參數。<br /><br /> 如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。<br /><br /> 如需詳細資訊，請參閱 [xdcmake.exe 參考](/cpp/build/reference/xdcmake-reference)中的 **/nologo** 選項。|
|**TrackerLogDirectory**|選擇性的 **字串** 參數。<br /><br /> 指定追蹤器記錄檔的目錄。|

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)