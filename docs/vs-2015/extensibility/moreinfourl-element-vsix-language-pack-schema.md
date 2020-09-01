---
title: MoreInfoURL 元素 (VSIX 語言套件架構) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 3f07b67b-95c5-4ae8-8b7e-d643cbbb0348
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c583d67e1920080f11158a4001e191e93e234006
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2020
ms.locfileid: "89284391"
---
# <a name="moreinfourl-element-vsix-language-pack-schema"></a>MoreInfoURL 元素 (VSIX 語言套件結構描述)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

選擇性。 有關延伸模組之當地語系化資訊的連結。  
  
## <a name="syntax"></a>語法  
  
```  
<MoreInfoURL>URL</MoreInfoURL>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
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
|[VSIX LanguagePack 元素](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|必要。 提供 VSIX 語言套件的根項目。|  
  
## <a name="text-value"></a>文字值  
 選擇性。 網站的連結。 此連結是文字字串。  
  
## <a name="element-information"></a>項目資訊  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    命名空間    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   結構描述名稱   |                 VSIX 語言套件架構                 |
| 驗證檔 |                VSIXLanguagePackSchema .xsd                 |
|  可以是空的   |                      不適用                       |
  
## <a name="see-also"></a>另請參閱  
 [VSX 語言套件架構參考](../extensibility/vsx-language-pack-schema-reference.md)   
 [將 VSIX 封裝當地語系化](../extensibility/localizing-vsix-packages.md)   
 [VSIX 延伸架構1.0 參考](/previous-versions/dd393700(v=vs.110))
