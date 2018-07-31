---
title: ProjectExtensions 元素 (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c977578a01c6d0af62f328e44a617ff2e00fe128
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39150852"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions 元素 (MSBuild)
可讓 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔包含非 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 的資訊。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 將會忽略 `ProjectExtensions` 內部的一切。  

 \<Project>  
 \<ProjectExtensions>  

## <a name="syntax"></a>語法  

```xml  
<ProjectExtensions>  
    Non-MSBuild information to include in file.  
</ProjectExtensions>  
```  

## <a name="attributes-and-elements"></a>屬性和元素  
 以下各節說明屬性、子元素和父元素。  

### <a name="attributes"></a>屬性  
 無  

### <a name="child-elements"></a>子元素  
 無  

### <a name="parent-elements"></a>父元素  

|元素|描述|  
|-------------|-----------------|  
|[專案](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔案的必要根元素。|  

## <a name="remarks"></a>備註  
 在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案中，只能使用一個 `ProjectExtensions` 元素。  

## <a name="example"></a>範例  
 下列程式碼範例會顯示來自整合式開發環境中且儲存於 `ProjectExtensions` 元素內的資訊。  

```xml  
<ProjectExtensions>  
    <VSIDE>  
        <External>  
            <!--  
            Raw XML passed to the IDE by an external source  
            -->  
        </External>  
    </VSIDE>  
</ProjectExtensions>  
```  

## <a name="see-also"></a>另請參閱  
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)  
 [ MSBuild](../msbuild/msbuild.md)
