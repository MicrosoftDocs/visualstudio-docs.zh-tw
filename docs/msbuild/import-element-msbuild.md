---
title: Import 元素 (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3ebe16f03c185437bc0ab79fe7c038748c5eb50
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="import-element-msbuild"></a>Import 項目 (MSBuild)
將某個專案檔的內容匯入至另一個專案檔。  

 \<Project>  
 \<Import>  

## <a name="syntax"></a>語法  

```  
<Import Project="ProjectPath"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  

### <a name="attributes"></a>屬性  

|屬性|描述|  
|---------------|-----------------|  
|`Project`|必要屬性。<br /><br /> 要匯入之專案檔的路徑。 路徑可以包含萬用字元。 相符的檔案會依排序的順序進行匯入。 使用這項功能，只要將程式碼檔案新增至目錄，就可以將程式碼新增至專案。|  
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|  

### <a name="child-elements"></a>子元素  
 無  

### <a name="parent-elements"></a>父項目  

|元素|描述|  
|-------------|-----------------|  
|[專案](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔案的必要根項目。|  
|[ImportGroup](../msbuild/importgroup-element.md)|包含群組在選擇性條件下方的 `Import` 項目集合。|  

## <a name="remarks"></a>備註  
 使用 `Import` 項目，您可以重複使用通用於許多專案檔的程式碼。 因為您對共用程式碼的更新都會傳播至匯入它的所有專案，所以這可讓您更輕鬆地維護程式碼。  

 依照慣例，共用的匯入專案檔儲存為 .targets 檔案，但它們是標準 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 可讓您匯入副檔名不同的專案，但基於一致性，建議您使用 .targets 副檔名。  

 所匯入專案中的相對路徑是解譯成相對於匯入專案的目錄。 因此，如果將專案檔匯入至不同位置中的數個專案檔，則針對每個匯入的專案，會以不同的方式解譯匯入之專案檔中的相對路徑。  

 所有與匯入的專案中所參考的專案檔有關的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 保留屬性 (例如 `MSBuildProjectDirectory` 和 `MSBuildProjectFile`)，都會根據匯入專案檔來指派值。  

 如果匯入的專案沒有 `DefaultTargets` 屬性，則會依匯入順序來檢查匯入的專案，並使用第一個探索到之 `DefaultTargets` 屬性的值。 例如，如果 ProjectA 匯入 ProjectB 和 ProjectC (依該順序)，而 ProjectB 匯入 ProjectD，則 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 會依序尋找 ProjectA、ProjectB、ProjectD 和 ProjectC 上指定的 `DefaultTargets` 。  

 匯入之專案的結構描述與標準專案的結構描述完全相同。 雖然 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 可能可以建置匯入的專案，但是無法達成，因為匯入的專案通常不會包含要設定之屬性或目標執行順序的相關資訊。 匯入的專案取決於匯入它以提供該資訊的專案。  

> [!NOTE]
>  雖然條件式匯入陳述式可在命令列 MSBuilds 中運作，但是在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 整合式開發環境 (IDE) 中無法與 MSBuild 搭配運作。 條件式匯入是使用載入專案時所設定的組態與平台值進行評估。 如果後續變更需要重新評估專案檔中的條件 (例如，變更平台)，則 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會重新評估屬性和項目的條件，但匯入時不會重新評估。 因為不會重新評估條件式匯入，所以會略過匯入。  
>   
>  若要解決這個問題，請將條件式匯入放到 .targets 檔案中，或將程式碼放到條件式區塊中 (例如 [Choose Element (MSBuild)](../msbuild/choose-element-msbuild.md) 區塊)。  

## <a name="wildcards"></a>萬用字元  
 在 .NET Framework 4 中，MSBuild 允許在 Project 屬性中使用萬用字元。 有萬用字元時，會排序所有找到的相符項目 (適用於重現性)，然後依該順序進行匯入，就像已明確設定順序一樣。  

 如果您想要提供擴充點，讓其他人可以匯入檔案，而不需要您將檔案名稱明確地新增至匯入檔案，則這非常好用。 基於此目的，Microsoft.Common.Targets 會在檔案頂端包含下行。  

```xml  
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>  
```  

## <a name="example"></a>範例  
 下列範例示範具有數個項目和屬性並匯入一般專案檔的專案。  

```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  

    <PropertyGroup>  
        <resourcefile>Strings.resx</resourcefile>  

        <compiledresources>  
            $(O)\$(MSBuildProjectName).Strings.resources  
        </compiledresources>  
    </PropertyGroup>  

    <ItemGroup>  
        <CSFile Include="*.cs" />  

        <Reference Include="System" />  
        <Reference Include="System.Data" />  
    </ItemGroup>  

    <Import Project="$(CommonLocation)\General.targets" />  
</Project>  
```  

## <a name="see-also"></a>請參閱  
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)   
 [如何：使用多個專案檔內相同的目標](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
