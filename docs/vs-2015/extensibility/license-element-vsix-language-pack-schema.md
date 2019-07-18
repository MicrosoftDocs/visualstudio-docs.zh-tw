---
title: 授權元素 （VSIX 語言套件結構描述） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a079dee3fc01995d70f77a9fa9791a5ab0f42561
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680598"
---
# <a name="license-element-vsix-language-pack-schema"></a>License 元素 （VSIX 語言套件結構描述）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

選擇性。 當地語系化版本的延伸模組的授權檔案的路徑。  
  
## <a name="syntax"></a>語法  
  
```  
<License>FilePath\license.txt</License>  
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
 要顯示當地語系化的授權檔案的相對路徑。  
  
## <a name="remarks"></a>備註  
 如果`License`定義項目，然後指定的授權檔案的文字會顯示在安裝期間使用者必須接受授權以繼續。  
  
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
