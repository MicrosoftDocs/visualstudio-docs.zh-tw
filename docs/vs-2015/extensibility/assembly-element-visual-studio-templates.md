---
title: Assembly 項目 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e3dfc502157b2d0016f1a0fd9a12dc3905f623c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945040"
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定的範本會使用該組件的參考加入至專案的組件的相關資訊。  
  
 \<VSTemplate>  
 \<TemplateContent>  
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
  
-   為完整的組件名稱。 例如：  
  
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
