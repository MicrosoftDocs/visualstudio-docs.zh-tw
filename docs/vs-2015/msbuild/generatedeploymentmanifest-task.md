---
title: GenerateDeploymentManifest 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateDeploymentManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateDeploymentManifest task
- GenerateDeploymentManifest task [MSBuild]
ms.assetid: 0734ebda-734d-49c4-9642-8d9d919d45fd
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6f0c13e5ea8778ca91c30383287aaad6e965bb65
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149607"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

產生 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署資訊清單。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署資訊清單透過定義部署的唯一識別、識別例如安裝或線上模式的部署特性、指定應用程式更新設定和更新位置，以及指出對應的 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式資訊清單，來描述應用程式部署。  
  
## <a name="parameters"></a>參數  
 下表說明 `GenerateDeploymentManifest` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`AssemblyName`|選擇性的 `String` 參數。<br /><br /> 針對產生的資訊清單指定組件識別的 `Name` 欄位。 如果未指定此參數，會從 `EntryPoint` 或 `InputManifest` 參數來推斷名稱。 如果無法推斷名稱，工作就會擲回錯誤。|  
|`AssemblyVersion`|選擇性的 `String` 參數。<br /><br /> 針對產生的資訊清單指定組件識別的 `Version` 欄位。 如果未指定此參數，工作會使用 "1.0.0.0" 的值。|  
|`CreateDesktopShortcut`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 true，ClickOnce 應用程式安裝期間會在桌面上建立一個圖示。|  
|`DeploymentUrl`|選擇性的 `String` 參數。<br /><br /> 指定應用程式的更新位置。 如果未指定此參數，就不會為應用程式定義任何更新位置。 不過，如果 `UpdateEnabled` 參數是 `true`，則必須指定更新位置。 指定的值應該是完整的 URL 或 UNC 路徑。|  
|`Description`|選擇性的 `String` 參數。<br /><br /> 指定應用程式的選擇性描述。|  
|`DisallowUrlActivation`|選擇性的 `Boolean` 參數。<br /><br /> 指定當應用程式透過 URL 開啟時，是否應該自動執行。 如果此參數為 `true`，應用程式只能從 [開始] 功能表啟動。 此參數的預設值為 `false`。 只有當 `Install` 參數值為 `true` 時，此輸入才適用。|  
|`EntryPoint`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指出所產生資訊清單組件的進入點。 對於 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署資訊清單，此輸入會指定 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式資訊清單。<br /><br /> 在 [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] 中，[GenerateApplicationManifest 工作](../msbuild/generateapplicationmanifest-task.md)需要 `EntryPoint` 來產生應用程式資訊清單 (組件或原生資訊清單不需要 `EntryPoint`)。這項需求已強制使用建置錯誤：「 MSB3185:進入點未指定資訊清單。 」<br /><br /> 未指定 `EntryPoint` 工作參數時，[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 不會發出此錯誤。 但是 \<customHostSpecified> 標記會插入做為 \<entryPoint> 標記的子系，例如：<br /><br /> `<entryPoint xmlns="urn:schemas-`<br /><br /> `microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> 您可以使用下列步驟，將 DLL 相依性加入至應用程式資訊清單︰<br /><br /> 1.藉由呼叫 <xref:Microsoft.Build.Tasks.ResolveAssemblyReference> 解析組件參考。<br />2.將上一個工作和組件本身的輸出傳遞至 <xref:Microsoft.Build.Tasks.ResolveManifestFiles>。<br />3.使用 `Dependencies` 參數將相依性傳遞至 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>。|  
|`ErrorReportUrl`|選擇性的 [String](<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->)參數。<br /><br /> 指定在 ClickOnce 安裝期間顯示在對話方塊中的網頁 URL。|  
|`InputManifest`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指出要作為資訊清單產生器基底的輸入 XML 文件。 這能讓結構化資料 (例如自訂資訊清單定義) 反映在輸出資訊清單中。 XML 文件中的根元素必須是 asmv1 命名空間中的組件節點。|  
|`Install`|選擇性的 `Boolean` 參數。<br /><br /> 指定應用程式是已安裝的應用程式或是線上專用應用程式。 如果此參數為 `true`，應用程式將會安裝在使用者的 [開始] 功能表，並可以使用 [新增或移除程式] 對話方塊來移除。 如果此參數為 `false`，應用程式僅供從網頁線上使用。 此參數的預設值為 `true`。|  
|`MapFileExtensions`|選擇性的 `Boolean` 參數。<br /><br /> 指定是否要使用 .deploy 副檔名對應。 如果此參數為 `true`，每個程式檔都是以 .deploy 副檔名發行。 對於限制必須解除封鎖的副檔名數目，以啟用 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式部署的網頁伺服器安全性，此選項很實用。 此參數的預設值為 `false`。|  
|`MaxTargetPath`|選擇性的 `String` 參數。<br /><br /> 指定 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式部署中允許的檔案路徑長度上限。 如果指定此參數，則會根據此限制來檢查應用程式中的每個檔案路徑長度。 任何超過限制的項目都會造成建置警告。 如果這項輸入未指定或為零，則不會執行任何檢查。|  
|`MinimumRequiredVersion`|選擇性的 `String` 參數。<br /><br /> 指定使用者是否可以略過更新。 如果使用者的版本低於最小必要版本，則無法選擇略過更新。 當 `Install` 參數的值是 `true` 時，此輸入才適用。|  
|`OutputManifest`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定所產生的輸出資訊清單檔名稱。 如果未指定此參數，會從產生的資訊清單識別來推斷輸出檔的名稱。|  
|`Platform`|選擇性的 `String` 參數。<br /><br /> 指定應用程式的目標平台。 此參數的值如下：<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> 預設值為 `AnyCPU`。|  
|`Product`|選擇性的 `String` 參數。<br /><br /> 指定應用程式的名稱。 如果未指定此參數，會從產生的資訊清單識別來推斷名稱。 此名稱可用來做為 [開始] 功能表上的捷徑名稱，而且是出現在 [新增或移除程式] 對話方塊中名稱的一部分。|  
|`Publisher`|選擇性的 `String` 參數。<br /><br /> 指定應用程式的發行者。 如果未指定此參數，會從已註冊使用者或產生的資訊清單識別來推斷名稱。 此名稱可用來做為 [開始] 功能表上的資料夾名稱，而且是出現在 [新增或移除程式] 對話方塊中名稱的一部分。|  
|`SuiteNamel`|選擇性的 `String` 參數。<br /><br /> 指定在 ClickOnce 部署之後，[開始] 功能表上的應用程式所在的資料夾名稱。|  
|`SupportUrl`|選擇性的 `String` 參數。<br /><br /> 指定出現在 [新增或移除程式] 對話方塊中的應用程式連結。 指定的值應該是完整 URL 或 UNC 路徑。|  
|`TargetCulture`|選擇性的 `String` 參數。<br /><br /> 識別應用程式的文化特性，並為產生的資訊清單指定組件識別的 `Language` 欄位。 如果未指定此參數，則會假設應用程式會因文化特性而異。|  
|`TrustUrlParameters`|選擇性的 `Boolean` 參數。<br /><br /> 指定應用程式是否可以使用 URL 查詢字串參數。 此參數的預設值是 `false`，表示應用程式無法使用該參數。|  
|`UpdateEnabled`|選擇性的 `Boolean` 參數。<br /><br /> 指出是否要讓應用程式進行更新。 此參數的預設值為 `false`。 當 `Install` 參數的值是 `true` 時，此參數才適用。|  
|`UpdateInterval`|選擇性的 `Int32` 參數。<br /><br /> 指定應用程式的更新間隔。 此參數的預設值為零。 當 `Install` 與 `UpdateEnabled` 參數的值都是 `true` 時，此參數才適用。|  
|`UpdateMode`|選擇性的 `String` 參數。<br /><br /> 指出應該先在前景檢查更新才啟動應用程式，或於執行應用程式時在背景更新。 此參數的值如下：<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> 此參數的預設值為 `Background`。 當 `Install` 與 `UpdateEnabled` 參數的值都是 `true` 時，此參數才適用。|  
|`UpdateUnit`|選擇性的 `String` 參數。<br /><br /> 指定 `UpdateInterval` 參數的單位。 此參數的值如下：<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> 當 `Install` 與 `UpdateEnabled` 參數的值都是 `true` 時，此參數才適用。|  
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.GenerateManifestBase> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需工作類別的參數清單，請參閱[工作基底類別](../msbuild/task-base-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [GenerateApplicationManifest 工作](../msbuild/generateapplicationmanifest-task.md)   
 [SignFile 工作](../msbuild/signfile-task.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
