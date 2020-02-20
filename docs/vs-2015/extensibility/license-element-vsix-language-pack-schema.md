---
title: License 元素（VSIX 語言套件架構） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1299d97cbda78049732d3367a9231272397e2ec
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477080"
---
# <a name="license-element-vsix-language-pack-schema"></a>License 元素（VSIX 語言套件架構）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

選擇性。 延伸模組的當地語系化版本授權檔案的路徑。  
  
## <a name="syntax"></a>語法  
  
```  
<License>FilePath\license.txt</License>  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|None||  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|None||  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[VSIX LanguagePack 元素](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|必要。 提供 VSIX 語言套件的根項目。|  
  
## <a name="text-value"></a>文字值  
 要顯示之當地語系化授權檔案的相對路徑。  
  
## <a name="remarks"></a>備註  
 如果定義了 `License` 專案，則在安裝期間會顯示指定之授權檔案的文字，使用者必須接受該授權才能繼續。  
  
## <a name="element-information"></a>項目資訊  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    命名空間    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   結構描述名稱   |                 VSIX 語言套件架構                 |
| 驗證檔 |                VSIXLanguagePackSchema .xsd                 |
|  可以是空的   |                      不適用                       |
  
## <a name="see-also"></a>另請參閱  
 [VSX 語言套件架構參考](../extensibility/vsx-language-pack-schema-reference.md)   
 [當地語系化 VSIX 封裝](../extensibility/localizing-vsix-packages.md)   
 [VSIX 延伸模組架構1.0 參考](/previous-versions/dd393700(v=vs.110))
