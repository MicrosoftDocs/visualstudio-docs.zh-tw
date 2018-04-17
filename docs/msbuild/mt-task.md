---
title: MT 工作 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- vc.task.mt
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBUILD (Visual C++), MT task
- MT task (MSBuild (Visual C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
caps.latest.revision: 6
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8a9bdfcd391a6377abf1d750330bb1a0dbd8bf80
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="mt-task"></a>MT 工作
包裝 Microsoft 資訊清單工具 mt.exe。 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站的 "Mt.exe"。  
  
## <a name="parameters"></a>參數  
 下表說明 **MT** 工作的參數。 大部分的工作參數以及數組參數會對應到命令列選項。  
  
> [!NOTE]
>  mt.exe 文件使用連字號 (**-**) 做為命令列選項的前置詞，但本主題使用斜線 (**/**)。 任一前置詞都可接受。  
  
|參數|描述|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|選擇性的 **String[]** 參數。<br /><br /> 指定一或多個資訊清單檔案的名稱。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/manifest** 選項。|  
|**AdditionalOptions**|選擇性的 **String** 參數。<br /><br /> 命令列選項清單。 例如 "*/option1 /option2 /option#*"。 使用此參數，來指定任何其他 **MT** 工作參數未表示的命令列選項。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站的 "Mt.exe"。|  
|**AssemblyIdentity**|選擇性的 **String** 參數。<br /><br /> 指定資訊清單的 **assemblyIdentity** 元素屬性值。 指定以逗號分隔的清單，其中第一個元件是 `name` 屬性的值，後面接著一或多個有表單的名稱/值組 *\<屬性名稱>=<attribute_value>*。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/identity** 選項。|  
|**ComponentFileName**|選擇性的 **String** 參數。<br /><br /> 指定您想要從 .rgs 或 .tlb 檔組建的動態連結程式庫名稱。 如果指定 **RegistrarScriptFile** 或 **TypeLibraryFile** MT 工作參數，這個參數是必要的。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/dll** 選項。|  
|**DependencyInformationFile**|選擇性的 **String** 參數。<br /><br /> 指定 Visual Studio 用來追蹤資訊清單工具的組建相依性資訊的相依性資訊檔。|  
|**EmbedManifest**|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，則在組件中內嵌資訊清單檔案。 如果為 `false`，則建立為獨立的資訊清單檔案。|  
|**EnableDPIAwareness**|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，則新增至將應用程式標記為 DPI 感知的資訊清單資訊。 撰寫 DPI 感知應用程式，可讓使用者介面在各種不同的高 DPI 顯示器設定中看起來十分一致。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站的「高 DPI」。|  
|**GenerateCatalogFiles**|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，則產生目錄定義 (.cdf) 檔案。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/makecdfs** 選項。|  
|**GenerateCategoryTags**|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，會導致產生分類標記。 如果這個參數是 `true`，也必須指定 **ManifestFromManagedAssemblyMT** 工作參數。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/category** 選項。|  
|**InputResourceManifests**|選擇性的 **String** 參數。<br /><br /> 從已指定識別碼的 RT_MANIFEST 類型資源輸入資訊清單。 指定表單的資源：*\<檔案>[***;***[***#***]<resource_id>]*，其中選擇性的 `resource_id` 參數為非負數的 16 位元數字。<br /><br /> 如果不指定 `resource_id`，則會使用 CREATEPROCESS_MANIFEST_RESOURCE 預設值 (1)。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/inputresource** 選項。|  
|**ManifestFromManagedAssembly**|選擇性的 **String** 參數。<br /><br /> 從指定的受控組件中產生資訊清單。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/managedassemblyname** 選項。|  
|**ManifestToIgnore**|選擇性的 **String** 參數。<br /><br /> (未使用。)|  
|**OutputManifestFile**|選擇性的 **String** 參數。<br /><br /> 指定輸出資訊清單的名稱。 如果省略此參數，且只操作一份資訊清單，則就地修改該資訊清單。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/out** 選項。|  
|**OutputResourceManifests**|選擇性的 **String** 參數。<br /><br /> 將資訊清單輸出至已指定識別碼的 RT_MANIFEST 類型資源。 資源屬於表單：*\<檔案>[***;***[***#***]<resource_id>]*，其中選擇性的 `resource_id` 參數為非負數的 16 位元數字。<br /><br /> 如果不指定 `resource_id`，則會使用 CREATEPROCESS_MANIFEST_RESOURCE 預設值 (1)。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/outputresource** 選項。|  
|**RegistrarScriptFile**|選擇性的 **String** 參數。<br /><br /> 指定免註冊 COM 資訊清單支援所使用的登錄器指令碼檔 (.rgs) 名稱。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/rgs** 選項。|  
|**ReplacementsFile**|選擇性的 **String** 參數。<br /><br /> 指定包含登錄器指令碼檔 (.rgs) 中可取代字串值的檔案。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/replacements** 選項。|  
|**ResourceOutputFileName**|選擇性的 **String** 參數。<br /><br /> 指定用來將資訊清單嵌入專案輸出的輸出資源檔。|  
|**Sources**|選擇性的 `ITaskItem[]` 參數。<br /><br /> 指定以空格分隔的資訊清單原始程式檔清單。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/manifest** 選項。|  
|**SuppressDependencyElement**|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，會產生沒有相依性元素的資訊清單。 如果這個參數是 `true`，也要指定 **ManifestFromManagedAssemblyMT** 工作參數。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/nodependency** 選項。|  
|**SuppressStartupBanner**|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/nologo** 選項。|  
|**TrackerLogDirectory**|選擇性的 `String` 參數。<br /><br /> 指定儲存此工作之追蹤記錄檔的中繼目錄。|  
|**TypeLibraryFile**|選擇性的 **String** 參數。<br /><br /> 指定類型程式庫檔案 (.tlb) 的名稱。 如果指定這個參數，也要指定 **ComponentFileNameMT** 工作參數。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/tlb** 選項。|  
|**UpdateFileHashes**|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，請計算 **UpdateFileHashesSearchPathMT** 工作參數指定路徑上的檔案雜湊值，然後使用運算得出的值更新資訊清單 **file** 元素的 **hash** 屬性值。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/hashupdate** 選項。 另請參閱本表中的 **UpdateFileHashesSearchPath** 參數。|  
|**UpdateFileHashesSearchPath**|選擇性的 `String` 參數。<br /><br /> 指定更新檔案雜湊時要使用的搜尋路徑。 使用此參數與 **UpdateFileHashesMT** 工作參數。<br /><br /> 如需詳細資訊，請參閱本表中的 **UpdateFileHashes** 參數。|  
|**VerboseOutput**|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，則顯示偵錯詳細資訊。<br /><br /> 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站中 "Mt.exe" 的 **/verbose** 選項。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)