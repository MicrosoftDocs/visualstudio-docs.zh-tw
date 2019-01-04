---
title: 參考項目 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 904dc9662b5bb7f2097e0aabce8af989a959f943
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889472"
---
# <a name="reference-element-visual-studio-templates"></a>Reference 項目 （Visual Studio 範本）
指定項目加入專案時要加入的組件參考。  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<參考 >  
 \<參考 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<Reference>  
    <Assembly> ... </Assembly>  
</Reference>  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節將說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[Assembly](../extensibility/assembly-element-visual-studio-templates.md)|必要項目。<br /><br /> 指定的範本會使用該組件的參考加入至專案的組件的相關資訊。 必須有一個`Assembly`中的項目每個`Reference`項目。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[參考](../extensibility/references-element-visual-studio-templates.md)|群組的範本加入至專案的組件參考。|  
  
## <a name="remarks"></a>備註  
 `Reference` 是 `References` 的必要子項目。  
  
 `Reference`並`References`項目僅適用於在 *.vstemplate*檔案具有`Type`屬性值`Item`。  
  
## <a name="example"></a>範例  
 下列範例說明`TemplateContent`的項目範本的項目。 這段 XML 會將參考加入*System.dll*並*System.Data.dll*組件。  
  
```xml  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
