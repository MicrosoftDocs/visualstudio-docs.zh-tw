---
title: ItemMetadata 元素 (MSBuild) | Microsoft Docs
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
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e3d9f72abfd095288b50ab8de9b9bc3eae4cc51
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665372"
---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata 項目 (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

包含使用者定義的項目中繼資料索引鍵，其中含有項目中繼資料值。 項目可能有任何數目的中繼資料索引鍵值組。  
  
 \<Project>  
 \<ItemGroup>  
 \<Item>  
  
## <a name="syntax"></a>語法  
  
```  
<ItemMetadataName> Item Metadata value</ItemMetadataName>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|說明|  
|-------------|-----------------|  
|[Item](../msbuild/item-element-msbuild.md)|使用者定義的元素，可定義建置程序的輸入。|  
  
## <a name="text-value"></a>文字值  
 可選擇使用文字值。  
  
 此文字會指定項目中繼資料值，它可以是文字或 XML。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何新增含有值 `fr` 的 `Culture` 中繼資料到項目 `CSFile`。  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>請參閱  
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)   
 [項目](../msbuild/msbuild-items.md)
