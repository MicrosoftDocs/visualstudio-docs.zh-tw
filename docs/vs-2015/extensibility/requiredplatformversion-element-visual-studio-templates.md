---
title: RequiredPlatformVersion 元素 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e5ba8cfef6674b5603cf03c73619f686338af3c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939505"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion 項目 (Visual Studio 樣板)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定的專案範本正常運作所需的作業系統最低版本。 這個項目用於建立的專案範本[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]應用程式。  
  
 `RequiredPlatformVersion`值會直接與作業系統的版本。 如果`RequiredPlatformVersion`高於作業系統的版本，不會顯示範本，這是在**新的專案** 對話方塊。 若要指定的範本[!INCLUDE[win8](../includes/win8-md.md)]或更高版本，設定`RequiredPlatformVersion`6.2.0 到。 若要指定的範本[!INCLUDE[win81](../includes/win81-md.md)]或更高版本，設定 RequiredPlatformVersion 至 6.3.0。  
  
 指定的範本`RequiredPlatformVersion`= 8 都與先前的客戶相容[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]範本。  
  
 VSTemplate  
TemplateData  
…..TargetPlatformName  
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
 這個範例會指定專案範本以 [!INCLUDE[win8](../includes/win8-md.md)] 或更新版本為目標。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [TargetPlatformName 元素 （Visual Studio 範本）](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
