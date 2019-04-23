---
title: RegisterAssembly 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RegisterAssembly task
- RegisterAssembly task [MSBuild]
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47fba490edd07c61490760114ca8df91b3e35eb1
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59668219"
---
# <a name="registerassembly-task"></a>RegisterAssembly 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

讀取所指定組件內的中繼資料，並將必要的項目加入至登錄，這樣可讓 COM 用戶端順利地建立 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 類別。 此工作的行為和 [Regasm.exe (組件登錄工具)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb) 很類似，但不是完全相同。  
  
## <a name="parameters"></a>參數  
 下表說明 `RegisterAssembly` 工作的參數。  
  
|參數|說明|  
|---------------|-----------------|  
|`Assemblies`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要向 COM 註冊的組件。|  
|`AssemblyListFile`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 包含 `RegisterAssembly` 工作與 [UnregisterAssembly](../msbuild/unregisterassembly-task.md) 工作之間狀態的相關資訊。 如此可防止 `UnregisterAssembly` 工作嘗試取消註冊無法在 `RegisterAssembly` 工作中註冊的組件。|  
|`CreateCodeBase`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，則會建立程式碼基底項目，以指定未安裝於全域組件快取中之組件的檔案路徑。 如果您將接著安裝要在全域組件快取中註冊的組件，則不應該指定這個選項。|  
|`TypeLibFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定要從指定組件產生的類型程式庫。 產生的類型程式庫包含組件內所定義的可存取類型定義。 只有在下列其中一項條件成立時，才會產生類型程式庫︰<br /><br /> - 該位置沒有那個名稱的類型程式庫存在時。<br />- 有類型程式庫存在，但比傳入的組件還舊。<br /><br /> 如果類型程式庫比傳入的組件還新時，不會建立新的程式庫，但仍會註冊該組件。<br /><br /> 如果指定此參數，它必須要有相同數目的項目做為 `Assemblies` 參數，否則工作將會失敗。 如果沒有指定輸入，該工作將預設為該組件的名稱，並將項目的副檔名變更為 .tlb。|  
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `RegisterAssembly` 工作來註冊 `MyAssemblies` 項目集合所指定的組件。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="MyAssembly.dll" />  
    <ItemGroup>  
  
    <Target Name="RegisterAssemblies">  
        <RegisterAssembly  
            Assemblies="@(MyAssemblies)" >  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
