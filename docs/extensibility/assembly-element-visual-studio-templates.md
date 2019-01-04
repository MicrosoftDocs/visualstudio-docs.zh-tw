---
title: Assembly 項目 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 74e57ae61ddfaa24de4cc8e3e332b3fa9f7250c6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912895"
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly 項目 （Visual Studio 範本）
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
  
## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
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
  
 `Reference`，`References,`並`Assembly`項目僅適用於在 *.vstemplate*所`Type`屬性值`Item`。  
  
## <a name="example"></a>範例  
 下列範例說明`TemplateContent`的項目範本的項目。 這段 XML 會將參考加入*System.dll*並*System.Data.dll*組件。  
  
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
 [建立專案與項目範本](../ide/creating-project-and-item-templates.md)