---
title: "CustomParameters 項目 （Visual Studio 範本） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords: CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90515cfa8a3aea03336aaee5503cb41df4704953
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParameters 項目 (Visual Studio 範本)
群組精靈進行參數取代時，應該傳遞至範本精靈的自訂參數。  
  
## <a name="syntax"></a>語法  
  
```  
<CustomParameters>  
    <CustomParameter/>  
    <CustomParameter/>  
</CustomParameters>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
|項目|說明|  
|-------------|-----------------|  
|[設定成 CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 包含自訂的參數名稱和值，以從範本建立專案或項目時使用。 `CustomParameter` 項目中可能有零個或多個 `CustomParameters` 項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|指定範本的內容。|  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列範例會示範如何在範本中使用數個自訂參數。 當從使用下列自訂參數的所有執行個體範本建立專案或項目`$color1$`和`$color2$`範本中的檔案將會取代`Red`和`Blue`分別。  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>另請參閱  
 [CustomParameter 項目 （Visual Studio 範本）](../extensibility/customparameter-element-visual-studio-templates.md)   
 [範本參數](../ide/template-parameters.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)