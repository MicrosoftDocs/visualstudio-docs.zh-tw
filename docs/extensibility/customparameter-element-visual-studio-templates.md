---
title: CustomParameter 元素 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6cb97e6b4c111689cb94c0df7c04c565e96a39cb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966760"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter 元素 （Visual Studio 範本）
包含自訂的參數名稱和值，以從範本建立專案或項目時使用。  
  
## <a name="syntax"></a>語法  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`Name`|必要項。 參數名稱。 參數的格式為 $*名稱*$。|  
|`Value`|必要項。 參數的取代值。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|群組精靈會讓參數替代項目時，要傳遞至 [範本] 精靈的自訂參數。|  
  
## <a name="remarks"></a>備註  
 當範本包含`CustomParameter`項目，每個執行個體`Name`屬性會取代`Value`中建立的專案或項目檔案的屬性。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用在範本中的數個自訂參數。 當從具有下列自訂參數的所有執行個體的範本建立專案或項目`$color1$`並`$color2$`範本中的檔案將會取代`Red`和`Blue`分別。  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>另請參閱  
 [CustomParameters 項目 （Visual Studio 範本）](../extensibility/customparameters-element-visual-studio-templates.md)   
 [範本參數](../ide/template-parameters.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)