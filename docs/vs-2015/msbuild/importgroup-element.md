---
title: ImportGroup 元素 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ImportGroup> element [MSBuild]
- ImportGroup element [MSBuild]
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b579b75970539c6639f98e321bb6e0a03341aa59
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485878"
---
# <a name="importgroup-element"></a>ImportGroup 元素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[ImportGroup 項目](https://docs.microsoft.com/visualstudio/msbuild/importgroup-element)。  
  
  
包含群組在選擇性條件下方的 `Import` 元素集合。 如需詳細資訊，請參閱 [Import 元素 (MSBuild)](../msbuild/import-element-msbuild.md)。  
  
 \<Project>  
 \<ImportGroup>  
  
## <a name="syntax"></a>語法  
  
```  
<ImportGroup Condition="'String A' == 'String B'">  
    <Import ... />  
    <Import ... />  
</ImportGroup>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[Import](../msbuild/import-element-msbuild.md)|將某個專案檔的內容匯入至另一個專案檔。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[專案](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 專案檔案的必要根項目。|  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列程式碼範例示範 `ImportGroup` 元素。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ImportGroup>  
        <Import Project="$(Targets1.targets) />  
        <Import Project="$(Targets2.targets) />  
    </ImportGroup>  
...  
</Project>  
```  
  
## <a name="see-also"></a>另請參閱  
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)   
 [項目](../msbuild/msbuild-items.md)



