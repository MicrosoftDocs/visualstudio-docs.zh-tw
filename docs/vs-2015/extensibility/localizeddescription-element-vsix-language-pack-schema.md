---
title: LocalizedDescription 元素 （VSIX 語言套件結構描述） |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 766a1732-bbaf-4875-b276-feb42169633a
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 408b582ec5145bab1f022776ba0793eb87b84dea
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797893"
---
# <a name="localizeddescription-element-vsix-language-pack-schema"></a>LocalizedDescription 元素 （VSIX 語言套件結構描述）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

必要。 提供的延伸模組的當地語系化的描述。  
  
## <a name="syntax"></a>語法  
  
```  
<LocalizedDescription>Localized description of the extension</LocalizedDescription>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|無||  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|無||  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[VSIX LanguagePack 元素](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|必要。 VSIX 語言套件中提供的根項目。|  
  
## <a name="text-value"></a>文字值  
 必要。 目標語言擴充功能的文字描述。  
  
## <a name="element-information"></a>項目資訊  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    命名空間    | http://schemas.microsoft.com/developer/vsx-schema-lp/2010 |
|   結構描述名稱   |                 VSIX 語言套件結構描述                 |
| 驗證檔 |                VSIXLanguagePackSchema.xsd                 |
|  可以是空白   |                      不適用                       |
  
## <a name="see-also"></a>另請參閱  
 [VSX 語言套件結構描述參考](../extensibility/vsx-language-pack-schema-reference.md)   
 [將 VSIX 封裝當地語系化](../extensibility/localizing-vsix-packages.md)   
 [VSIX 延伸結構描述 1.0 參考](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)

