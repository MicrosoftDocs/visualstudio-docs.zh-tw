---
title: XDCMake 工作 | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c41bfc2015f29cbb73b33df3594b3a3430af3f3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630648"
---
# <a name="xdcmake-task"></a>XDCMake 工作

包裝 XML 文檔工具 *（xdcmake.exe），* 該工具將 XML 文檔注釋 *（.xdc*） 檔合併到 *.xml*檔中。

 當您在C++原始程式碼中提供文檔注釋並使用[/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp)編譯器選項進行編譯時，將創建 *.xdc*檔。 有關詳細資訊，請參閱[xDCMake 引用](/cpp/build/reference/xdcmake-reference) [、XML 文檔產生器工具屬性頁](/cpp/build/reference/xml-document-generator-tool-property-pages)和*xdcmake.exe*的命令列説明選項 **（/？**

## <a name="remarks"></a>備註

 預設情況下 *，xdcmake.exe*工具支援幾個命令列選項。 當您指定 **/old** 命令列選項時，可支援額外的選項。

## <a name="parameters"></a>參數

 下表說明 **XDCMake** 工作的參數。

|參數|描述|
|---------------|-----------------|
|**AdditionalDocumentFile**|可選**字串*** 參數。<br /><br /> 指定要合併的一個或多個附加 *.xdc*檔。<br /><br /> 有關詳細資訊，請參閱[XML 文檔產生器工具屬性頁](/cpp/build/reference/xml-document-generator-tool-property-pages)中**的其他文檔檔**說明。 另請參閱 *xdcmake.exe* 的 **/old** 和 **/Fs** 命令列選項。|
|**AdditionalOptions**|可選**字串**參數。<br /><br /> 選項的清單，如命令列上所指定。 例如，/\<option1> /\<option2> /\<option#>。 使用這個參數來指定任何其他 **XDCMake** 工作參數未表示的選項。<br /><br /> 如需詳細資訊，請參閱 [XDCMake 參考](/cpp/build/reference/xdcmake-reference)、[XML 文件產生器工具屬性頁](/cpp/build/reference/xml-document-generator-tool-property-pages)，以及 *xdcmake.exe* 的命令列說明 (**/?**)。|
|**DocumentLibraryDependencies**|可選**布林參數**。<br /><br /> 如果`true`當前專案依賴于解決方案中的靜態程式庫 *（.lib*） 專案，則該庫專案的 *.xdc*檔將包含在當前專案的 *.xml*檔輸出中。<br /><br /> 有關詳細資訊，請參閱[XML 文檔產生器工具屬性頁](/cpp/build/reference/xml-document-generator-tool-property-pages)中**的文件庫依賴項**描述。|
|**輸出檔案**|可選**字串**參數。<br /><br /> 覆寫預設輸出檔案名稱。 預設名稱派生自處理的第一個 *.xdc*檔的名稱。<br /><br /> 如需詳細資訊，請參閱 [XDCMake 參考](/cpp/build/reference/xdcmake-reference)中的 **/out:\<filename>** 選項。 另請參閱*xdcmake.exe*的 **/舊**和 **/Fo**命令列選項。|
|**專案名稱**|可選**字串**參數。<br /><br /> 目前專案的名稱。|
|**SlashOld**|可選**布林參數**。<br /><br /> 如果`true`啟用其他*xdcmake.exe*選項。<br /><br /> 有關詳細資訊，請參閱*xdcmake.exe*的 **/舊**命令列選項。|
|**來源**|必要的 `ITaskItem[]` 參數。<br /><br /> 定義工作可以耗用和發出的 MSBuild 來源檔案項目的陣列。|
|**SuppressStartupBanner**|可選**布林參數**。<br /><br /> 如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。<br /><br /> 有關詳細資訊，請參閱[XDCMake 參考](/cpp/build/reference/xdcmake-reference)中的 **/nologo**選項。|
|**TrackerLogDirectory**|可選**字串**參數。<br /><br /> 指定追蹤器記錄檔的目錄。|

## <a name="see-also"></a>另請參閱

- [任務引用](../msbuild/msbuild-task-reference.md)