---
title: ImportGroup 元素 | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ImportGroup> element [MSBuild]
- ImportGroup element [MSBuild]
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97d5aeac5115dfa251b42c824b88a779e22ad6a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54978330"
---
# <a name="importgroup-element"></a>ImportGroup 項目
包含群組在選擇性條件下方的 `Import` 元素集合。 如需詳細資訊，請參閱 [Import 項目 (MSBuild)](../msbuild/import-element-msbuild.md)。  

 \<Project>  
 \<ImportGroup>  

## <a name="syntax"></a>語法  

```xml  
<ImportGroup Condition="'String A' == 'String B'">  
    <Import ... />  
    <Import ... />  
</ImportGroup>  
```  

## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子元素和父元素。  

### <a name="attributes"></a>屬性  

|屬性|說明|  
|---------------|-----------------|  
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|  

### <a name="child-elements"></a>子元素  

|元素|說明|  
|-------------|-----------------|  
|[Import](../msbuild/import-element-msbuild.md)|將某個專案檔的內容匯入至另一個專案檔。|  

### <a name="parent-elements"></a>父元素  

| 元素 | 說明 |
| - | - |
| [專案](../msbuild/project-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔案的必要根項目。 |

## <a name="example"></a>範例  
 下列程式碼範例示範 `ImportGroup` 元素。  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ImportGroup>  
        <Import Project="$(Targets1.targets)" />  
        <Import Project="$(Targets2.targets)" />  
    </ImportGroup>  
...  
</Project>  
```  

## <a name="see-also"></a>另請參閱  
 [專案檔結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)   
 [項目](../msbuild/msbuild-items.md)
