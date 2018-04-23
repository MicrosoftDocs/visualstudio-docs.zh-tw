---
title: 參考項目 （Visual Studio 範本） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
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
ms.openlocfilehash: 9e0217360b2a8e9c6c8e723561aff383ed3226d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="reference-element-visual-studio-templates"></a>參考項目 (Visual Studio 範本)
指定項目加入專案時要加入的組件參考。  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<參考 >  
 \<參考 >  
  
## <a name="syntax"></a>語法  
  
```  
<Reference>  
    <Assembly> ... </Assembly>  
</Reference>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節將說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Assembly](../extensibility/assembly-element-visual-studio-templates.md)|必要項目。<br /><br /> 指定的組件範本會使用該組件的參考加入專案的相關資訊。 必須有一個`Assembly`項目中的每個`Reference`項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[參考](../extensibility/references-element-visual-studio-templates.md)|將範本加入至專案的組件參考的群組。|  
  
## <a name="remarks"></a>備註  
 `Reference` 是 `References` 的必要子項目。  
  
 `Reference`和`References`元素只用於.vstemplate 檔案中所`Type`屬性值為`Item`。  
  
## <a name="example"></a>範例  
 下列範例說明`TemplateContent`項目範本的元素。 這段 XML 會加入 System.dll 和 System.Data.dll 組件的參考。  
  
```  
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
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)