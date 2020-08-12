---
title: " (VSIX 語言套件架構) 的 LocalizedName 元素 |Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 64d8430dbcf563ca232d1b8d850678925770219f
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114167"
---
# <a name="localizedname-element-vsix-language-pack-schema"></a>LocalizedName 元素 (VSIX 語言套件結構描述)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

必要。 要安裝之延伸模組的當地語系化名稱。  
  
## <a name="syntax"></a>語法  
  
```  
<Name>Localized name of the extension</Name>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|無||  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|無||  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[VSIX LanguagePack 元素](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|必要。 提供 VSIX 語言套件的根項目。|  
  
## <a name="text-value"></a>文字值  
 必要。 語言套件的名稱（以目的語言）。  
  
## <a name="element-information"></a>項目資訊  

:::row:::
    :::column:::
        命名空間
    :::column-end:::
    :::column:::
        `http://schemas.microsoft.com/developer/vsx-schema-lp/2010`
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        結構描述名稱
    :::column-end:::
    :::column:::
        VSIX 語言套件架構
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        驗證檔
    :::column-end:::
    :::column:::
        VSIXLanguagePackSchema .xsd
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        可以是空的
    :::column-end:::
    :::column:::
        不適用
    :::column-end:::
:::row-end:::
  
## <a name="see-also"></a>另請參閱  
 [VSX 語言套件架構參考](../extensibility/vsx-language-pack-schema-reference.md)   
 [當地語系化 VSIX 封裝](../extensibility/localizing-vsix-packages.md)   
 [VSIX 延伸模組架構1.0 參考](/previous-versions/dd393700(v=vs.110))
