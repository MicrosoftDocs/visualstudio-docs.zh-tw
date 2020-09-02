---
title: ProjectExtensions 項目 (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
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
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0afc4f73ed287f753acf87bd0b112e6f5303e996
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551246"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions 項目 (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

可讓 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 專案檔包含非 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 的資訊。 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 將會忽略 `ProjectExtensions` 內部的一切。  
  
 \<Project>  
 \<ProjectExtensions>  
  
## <a name="syntax"></a>語法  
  
```  
<ProjectExtensions>  
    Non-MSBuild information to include in file.  
</ProjectExtensions>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[專案](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 專案檔案的必要根項目。|  
  
## <a name="remarks"></a>備註  
 在 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 專案中，只能使用一個 `ProjectExtensions` 項目。  
  
## <a name="example"></a>範例  
 下列程式碼範例會顯示來自整合式開發環境中且儲存於 `ProjectExtensions` 項目內的資訊。  
  
```  
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
 [專案檔結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)  
 [MSBuild](msbuild.md)
