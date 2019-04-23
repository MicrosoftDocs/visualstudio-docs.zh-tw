---
title: Item 項目 (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cc3d606bb890b5f95089bfc7b1e83b2d34cd56ba
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59650757"
---
# <a name="item-element-msbuild"></a>Item 項目 (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

包含使用者定義的項目及其中繼資料。 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 專案中使用的每個項目，都必須指定為 `ItemGroup` 項目的子系。  
  
 \<Project>  
 \<ItemGroup>  
 \<Item>  
  
## <a name="syntax"></a>語法  
  
```  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|`Include`|必要屬性。<br /><br /> 要包含在項目清單中的檔案或萬用字元。|  
|`Exclude`|選擇性屬性。<br /><br /> 要從項目清單中排除的檔案或萬用字元。|  
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|  
|`Remove`|選擇性屬性。<br /><br /> 要從項目清單移除的檔案或萬用字元。<br /><br /> 這個屬性只有在針對 `ItemGroup` 中的 `Target` 項目指定時才有效。|  
|`KeepMetadata`|選擇性屬性。<br /><br /> 要加入目標項目之來源項目的中繼資料。 只有其名稱指定在分號分隔清單中的中繼資料，會從來源項目傳輸到目標項目。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。<br /><br /> 這個屬性只有在針對 `ItemGroup` 中的 `Target` 項目指定時才有效。|  
|`RemoveMetadata`|選擇性屬性。<br /><br /> 不要傳輸到目標項目之來源項目的中繼資料。 所有中繼資料會從來源項目傳輸到目標項目，名稱包含在以分號分隔的名稱清單中之中繼資料除外。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。<br /><br /> 這個屬性只有在針對 `ItemGroup` 中的 `Target` 項目指定時才有效。|  
|`KeepDuplicates`|選擇性屬性。<br /><br /> 指定項目如果與現有項目完全重複，是否應加入目標群組。 如果來源和目標項目具有相同的 `Include` 值，但中繼資料不同，則即使 `KeepDuplicates` 設定為 `false`，也會加入該項目。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。<br /><br /> 這個屬性只有在針對 `ItemGroup` 中的 `Target` 項目指定時才有效。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|說明|  
|-------------|-----------------|  
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|使用者定義的項目中繼資料索引鍵，其中含有項目中繼資料值。 項目中可能有零個或多個 `ItemMetadata` 項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|說明|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|項目的群組項目。|  
  
## <a name="remarks"></a>備註  
 `Item` 項目定義建置系統的輸入，且會依據使用者定義的集合名稱，分組成為項目集合。 這些項目集合可以用來做為[工作](../msbuild/msbuild-tasks.md)的參數，工作會使用集合中個別的項目來執行建置程序的步驟。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。  
  
 使用標記法 `@(`*myType*`)`，可讓類型 *myType* 的項目集合展開為以分號分隔的字串清單，並傳遞至參數。 如果參數的類型是 `string`，則參數的值會是以分號分隔的項目清單。 如果參數是字串陣列 (`string[]`)，則每個項目都會根據分號的位置，插入到陣列中。 如果工作參數的類型是 <xref:Microsoft.Build.Framework.ITaskItem>`[]`，則值就是項目集合的內容再加上任何附加的中繼資料。 若要使用分號以外的字元來分隔每個項目，請使用語法 `@(`*myType*`, '`*separator*`')`。  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 引擎可以評估萬用字元 (例如 `*` 和 `?`) 以及遞迴萬用字元 (例如 `/**/*.cs`)。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何宣告類型為 `CSFile` 的兩個項目。 第二個宣告項目包含 `MyMetadata` 設定為 `HelloWorld` 的中繼資料。  
  
```  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>請參閱  
 [項目](../msbuild/msbuild-items.md)   
 [MSBuild 屬性](msbuild-properties1.md)   
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)
