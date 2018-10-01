---
title: Assembly 項目 （Visual Studio 範本） |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 987e46810aa8cfe51102d2940bf48d24fd6824cf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489529"
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[組件元素 （Visual Studio 範本）](https://docs.microsoft.com/visualstudio/extensibility/assembly-element-visual-studio-templates)。  
  
指定的範本會使用該組件的參考加入至專案的組件的相關資訊。  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<參考 >  
 \<參考 >  
 \<組件 >  
  
## <a name="syntax"></a>語法  
  
```  
<Assembly> AssemblyName </Assembly>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[參考](../extensibility/reference-element-visual-studio-templates.md)|指定項目加入專案時要加入的組件參考。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 此文字會指定要加入至專案，項目樣板具現化時的組件。 這個組件名稱必須指定其中一種以下列方式：  
  
-   為完整的組件名稱。 例如:   
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   以簡單文字的參考。 例如:   
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## <a name="remarks"></a>備註  
 `Assembly` 是 `Reference` 的必要子項目。  
  
 `Reference`，`References,`並`Assembly`項目僅適用於具有.vstemplate 檔案中`Type`屬性值`Item`。  
  
## <a name="example"></a>範例  
 下列範例說明`TemplateContent`的項目範本的項目。 這個 XML 加入 System.dll 和 System.Data.dll 組件的參考。  
  
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

