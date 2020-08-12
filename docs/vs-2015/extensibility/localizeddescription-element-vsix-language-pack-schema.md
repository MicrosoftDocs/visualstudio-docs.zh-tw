---
title: " (VSIX 語言套件架構) 的 LocalizedDescription 元素 |Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 766a1732-bbaf-4875-b276-feb42169633a
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b4eb077ba8c957466568967804487929254117e
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114175"
---
# <a name="localizeddescription-element-vsix-language-pack-schema"></a>LocalizedDescription 元素 (VSIX 語言套件結構描述)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

必要。 提供延伸模組的當地語系化描述。  
  
## <a name="syntax"></a>語法  
  
```  
<LocalizedDescription>Localized description of the extension</LocalizedDescription>  
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
 必要。 目的語言之延伸模組的文字描述。  
  
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
