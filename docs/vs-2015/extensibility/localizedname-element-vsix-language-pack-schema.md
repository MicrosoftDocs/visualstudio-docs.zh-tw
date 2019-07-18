---
title: LocalizedName 元素 （VSIX 語言套件結構描述） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fcbda9f8c7a98d0830c898c81471854efc3a6403
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686144"
---
# <a name="localizedname-element-vsix-language-pack-schema"></a>LocalizedName 元素 （VSIX 語言套件結構描述）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

必要項。 安裝延伸模組的當地語系化的名稱。  
  
## <a name="syntax"></a>語法  
  
```  
<Name>Localized name of the extension</Name>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|None||  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|None||  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[VSIX LanguagePack 元素](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|必要項。 VSIX 語言套件中提供的根項目。|  
  
## <a name="text-value"></a>文字值  
 必要項。 目標語言的語言套件名稱。  
  
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
 [VSIX 延伸結構描述 1.0 參考](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
