---
title: "RequiredPlatformVersion 項目 （Visual Studio 範本） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 818405e6c7df6466208db325a7417e0b5b9387e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion 項目 (Visual Studio 樣板)
指定的專案範本需要正常運作的作業系統最低版本。 這個項目用於建立的專案範本[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]應用程式。  
  
 `RequiredPlatformVersion`直接與作業系統的版本進行比較的值。 如果`RequiredPlatformVersion`高於作業系統版本中，範本不會出現在**新專案** 對話方塊。 若要指定的範本[!INCLUDE[win8](../debugger/includes/win8_md.md)]或更高版本，將`RequiredPlatformVersion`6.2.0 至。 若要指定的範本[!INCLUDE[win81](../debugger/includes/win81_md.md)]或更高版本，將 RequiredPlatformVersion 至 6.3.0。  
  
 指定範本`RequiredPlatformVersion`= 8 都與先前的客戶相容[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]範本。  
  
 VSTemplate  
TemplateData  
.....TargetPlatformName  
RequiredPlatformVersion  
  
## <a name="syntax"></a>語法  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 無。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|指定專案範本的目標平台。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
## <a name="remarks"></a>備註  
 此文字會指定範本所需的最低作業系統版本。  
  
## <a name="example"></a>範例  
 這個範例會指定專案範本以 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 或更新版本為目標。  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>請參閱  
 [TargetPlatformName 項目 （Visual Studio 範本）](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)