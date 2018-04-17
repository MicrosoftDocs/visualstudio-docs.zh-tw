---
title: Assembly 項目 （Visual Studio 範本） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5202d7468ecefe9de1754f592eef826f0390b869
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly 項目 (Visual Studio 範本)
指定的組件範本會使用該組件的參考加入專案的相關資訊。  
  
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
  
 此文字會指定要加入至專案，當項目樣板具現化的組件。 這個組件名稱必須指定下列方式之一：  
  
-   做為完整的組件名稱。 例如:   
  
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
  
 `Reference`，`References,`和`Assembly`元素只用於.vstemplate 檔案中所`Type`屬性值為`Item`。  
  
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
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)