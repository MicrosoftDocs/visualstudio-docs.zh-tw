---
title: " (Visual Studio 範本的參考元素) |Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 19fd3e260e6c7079ccfb98f520858a31191cc112
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538197"
---
# <a name="references-element-visual-studio-templates"></a>參考項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

將範本加入至專案的元件參考組成群組。  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<References>  
  
## <a name="syntax"></a>語法  
  
```  
<References>  
    <Reference>... </Reference>  
    <Reference>... </Reference>  
    ...  
</References>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節將說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[參考](../extensibility/reference-element-visual-studio-templates.md)|必要元素。<br /><br /> 指定項目加入專案時要加入的組件參考。 元素中必須有一個或多個 `Reference` 元素 `References` 。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|指定範本的內容。|  
  
## <a name="remarks"></a>備註  
 `References` 是 `TemplateContent` 的選擇性子項目。  
  
 `Reference`和 `References` 元素只能用在具有 `Type` 屬性值的 .vstemplate 檔案中 `Item` 。  
  
## <a name="example"></a>範例  
 下列範例說明 `TemplateContent` 專案範本的元素。 這個 XML 會將參考加入 System.dll 和 System.Data.dll 元件。  
  
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
 [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
