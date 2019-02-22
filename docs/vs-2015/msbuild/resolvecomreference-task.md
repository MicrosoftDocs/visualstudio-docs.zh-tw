---
title: ResolveComReference 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveCOMReference task
- ResolveCOMReference task [MSBuild]
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9f535c1d79b1a37a5a25ff3e6f6d424eb4bc631d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54801423"
---
# <a name="resolvecomreference-task"></a>ResolveComReference 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
取得一或多個類型程式庫名稱或 .tlb 檔案的清單，並將那些類型程式庫解析至磁碟上的位置。  
  
## <a name="parameters"></a>參數  
 下表說明 `ResolveCOMReference` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`DelaySign`|選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，則將公開金鑰放在組件中。 如為 `false`，則完整簽署組件。|  
|`EnvironmentVariables`|選擇性的 `String[]` 參數。<br /><br /> 環境變數組陣列，以等號分隔。 這些變數是在規則環境區塊以外傳遞至繁衍的 tlbimp.exe 和 aximp.exe，或選擇性地覆寫。|  
|`ExecuteAsTool`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，會從適當目標 Framework 跨處理序執行 tlbimp.exe 和 aximp.exe，以產生必要的包裝函式組件。 此參數會啟用多目標。|  
|`IncludeVersionInInteropName`|選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，則包裝函式名稱會包含 TypeLib 版本。 預設為 `false`。|  
|`KeyContainer`|選擇性的 `String` 參數。<br /><br /> 指定保留公開/私密金鑰組<br /><br /> 的項目。|  
|`KeyFile`|選擇性的 `String` 參數。<br /><br /> 指定包含公開/私密金鑰組<br /><br /> 的項目。|  
|`NoClassMembers`|選擇性的 `Boolean` 參數。|  
|`ResolvedAssemblyReferences`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定已解析的組件參考。|  
|`ResolvedFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定磁碟上的完整檔案，這個磁碟對應至已提供作為這項工作輸入之類型程式庫的實體位置。|  
|`ResolvedModules`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。|  
|`SdkToolsPath`|選擇性的 [String](<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) 參數。<br /><br /> 如果 `ExecuteAsTool` 是 `true`，則此參數必須設定為目標 Framework 版本的 SDK 工具路徑。|  
|`StateFile`|選擇性的 <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> 參數。<br /><br /> 指定 COM 元件時間戳記的快取檔案。 如果沒有，則每次執行都會重新產生所有的包裝函式。|  
|`TargetFrameworkVersion`|選擇性的 <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> 參數。<br /><br /> 指定專案目標 Framework 版本。<br /><br /> 預設為 `String.Empty`。 這表示不篩選以目標 Framework 為基礎的參考。|  
|`TargetProcessorArchitecture`|選擇性的 <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> 參數。<br /><br /> 指定慣用的目標處理器架構。 平移後，傳送至 tlbimp.exe /machine 旗標。<br /><br /> 參數值應該是 <xref:Microsoft.Build.Utilities.ProcessorArchitecture> 的成員。|  
|`TypeLibFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定 COM 參考的類型程式庫檔案路徑。 此參數中包含的項目可能包含項目中繼資料。 如需詳細資訊，請參閱下文的＜TypeLibFiles 項目中繼資料＞一節。|  
|`TypeLibNames`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要解析的類型程式庫名稱。 此參數中包含的項目必須包含某些項目中繼資料。 如需詳細資訊，請參閱下文的＜TypeLibNames 項目中繼資料＞一節。|  
|`WrapperOutputDirectory`|選擇性的 `String` 參數。<br /><br /> 產生的 interop 組件在磁碟上所在位置。 如未指定此項目中繼資料，工作會使用專案檔所在目錄的絕對路徑。|  
  
## <a name="remarks"></a>備註  
  
## <a name="typelibnames-item-metadata"></a>TypeLibNames 項目中繼資料  
 下表描述將項目傳遞給 `TypeLibNames` 參數的可用項目中繼資料。  
  
|中繼資料|描述|  
|--------------|-----------------|  
|`GUID`|必要的項目中繼資料。<br /><br /> 類型程式庫的 GUID。 如未指定此項目中繼資料，則工作會失敗。|  
|`VersionMajor`|必要的項目中繼資料。<br /><br /> 類型程式庫的主要版本。 如未指定此項目中繼資料，則工作會失敗。|  
|`VersionMinor`|必要的項目中繼資料。<br /><br /> 類型程式庫的次要版本。 如未指定此項目中繼資料，則工作會失敗。|  
|`LocaleIdentifier`|選擇性項目中繼資料。<br /><br /> 類型程式庫的地區設定識別碼 (或 LCID)。 這會指定為 32 位元值，識別使用者、區域或應用程式慣用的人類語言。 如未指定此項目中繼資料，工作會使用預設的地區設定識別碼 "0"。|  
|`WrapperTool`|選擇性項目中繼資料。<br /><br /> 指定為此類型程式庫產生組件包裝函式使用的包裝函式工具。 如未指定此項目中繼資料，工作會使用預設的包裝函式工具 "tlbimp"。 可用且不區分大小寫的 TypeLib 選項有：<br /><br /> -   `Primary`：當您想要使用 COM 元件已產生的主要 Interop 組件時，請使用此包裝函式工具。 當您使用此包裝函式工具時，請勿指定包裝函式的輸出目錄，因為這會造成工作失敗。<br />-   `TLBImp`：當您想要產生 COM 元件的 Interop 組件時，請使用此包裝函式工具。<br />-   `AXImp`：當您想要產生 ActiveX 控制項的 Interop 組件時，請使用此包裝函式工具。|  
  
## <a name="typelibfiles-item-metadata"></a>TypeLibFiles 項目中繼資料  
 下表描述將項目傳遞給 `TypeLibFiles` 參數的可用項目中繼資料。  
  
|中繼資料|描述|  
|--------------|-----------------|  
|`WrapperTool`|選擇性項目中繼資料。<br /><br /> 指定為此類型程式庫產生組件包裝函式使用的包裝函式工具。 如未指定此項目中繼資料，工作會使用預設的包裝函式工具 "tlbimp"。 可用且不區分大小寫的 TypeLib 選項有：<br /><br /> -   `Primary`：當您想要使用 COM 元件已產生的主要 Interop 組件時，請使用此包裝函式工具。 當您使用此包裝函式工具時，請勿指定包裝函式的輸出目錄，因為這會造成工作失敗。<br />-   `TLBImp`：當您想要產生 COM 元件的 Interop 組件時，請使用此包裝函式工具。<br />-   `AXImp`：當您想要產生 ActiveX 控制項的 Interop 組件時，請使用此包裝函式工具。|  
  
> [!NOTE]
>  您為唯一識別類型程式庫所提供的資訊愈詳細，工作解析至正確磁碟檔案的可能性就愈大。  
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，這項工作也會從 <xref:Microsoft.Build.Utilities.Task> 類別繼承參數。 如需這些其他參數的清單及其說明，請參閱 [Task 基底類別](../msbuild/task-base-class.md)。  
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
