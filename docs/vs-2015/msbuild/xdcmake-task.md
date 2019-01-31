---
title: XDCMake 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 58257921634e1afb89dfc0c012728523bc98a2ef
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54792885"
---
# <a name="xdcmake-task"></a>XDCMake 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
包裝 XML 文件工具 (xdcmake.exe)，此工具可將 XML 文件註解 (.xdc) 檔案合併至 .xml 檔案。  
  
 當您在 Visual C++ 原始程式碼中提供文件註解，並透過使用 [/doc](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63) 編譯器選項編譯時，會產生 .xdc 檔案。 如需詳細資訊，請參閱 [XDCMake 參考](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac)、[XML 文件產生器工具屬性頁](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)，以及 xdcmake.exe 的命令列說明選項 (**/?**)。  
  
## <a name="remarks"></a>備註  
 根據預設，xdcmake.exe 工具支援幾個命令列選項。 當您指定 **/old** 命令列選項時，可支援額外的選項。  
  
## <a name="parameters"></a>參數  
 下表說明 **XDCMake** 工作的參數。  
  
|參數|說明|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|選擇性的 **String[]** 參數。<br /><br /> 指定其他一或多個要合併的 .xdc 檔案。<br /><br /> 如需詳細資訊，請參閱 [XML 文件產生器工具屬性頁](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)中的**其他文件檔**描述。 另請參閱 xdcmake.exe 的 **/old** 和 **/Fs** 命令列選項。|  
|**AdditionalOptions**|選擇性的 **String** 參數。<br /><br /> 選項的清單，如命令列上所指定。 例如 "*/option1 /option2 /option#*"。 使用這個參數來指定任何其他 **XDCMake** 工作參數未表示的選項。<br /><br /> 如需詳細資訊，請參閱 [XDCMake 參考](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac)、[XML 文件產生器工具屬性頁](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)，以及 xdcmake.exe 的命令列說明 (**/?**)。|  
|**DocumentLibraryDependencies**|選擇性的 **Boolean** 參數。<br /><br /> 如果為 `true` 且目前的專案相依於方案中的靜態程式庫 (.lib) 專案，則程式庫專案的 .xdc 檔案會包含在目前專案的 .xml 檔案輸出中。<br /><br /> 如需詳細資訊，請參閱 [XML 文件產生器工具屬性頁](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)中的**文件庫相依性**描述。|  
|**OutputFile**|選擇性的 **String** 參數。<br /><br /> 覆寫預設輸出檔案名稱。 此預設名稱衍生自第一個處理之 .xdc 檔案的名稱。<br /><br /> 如需詳細資訊，請參閱 [XDCMake 參考](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac)中的 **/out:**`filename` 選項。 另請參閱 xdcmake.exe 的 **/old** 和 **/Fo** 命令列選項。|  
|**ProjectName**|選擇性的 **String** 參數。<br /><br /> 目前專案的名稱。|  
|**SlashOld**|選擇性的 **Boolean** 參數。<br /><br /> 如果為 `true`，則會啟用其他 xdcmake.exe 選項。<br /><br /> 如需詳細資訊，請參閱 xdcmake.exe 的 **/old** 命令列選項。|  
|**Sources**|必要的 `ITaskItem[]` 參數。<br /><br /> 定義工作可以耗用和發出的 MSBuild 來源檔案項目的陣列。|  
|**SuppressStartupBanner**|選擇性的 **Boolean** 參數。<br /><br /> 如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。<br /><br /> 如需詳細資訊，請參閱 [XDCMake 參考](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac)中的 **/nologo** 選項。|  
|**TrackerLogDirectory**|選擇性的 **String** 參數。<br /><br /> 指定追蹤器記錄檔的目錄。|  
  
## <a name="see-also"></a>請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)
