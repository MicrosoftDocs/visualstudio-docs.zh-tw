---
title: VSIXLanguagePack 元素 （VSIX 語言套件結構描述） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b4ba4e98b8b2d42485a7594d5bab658e1bd6ccb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943545"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>VSIXLanguagePack 元素 （VSIX 語言套件結構描述）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

必要項。 VSIX 語言套件中提供的根項目。 VSIX 語言套件會提供 VSIX 封裝當地語系化的安裝資訊。  
  
## <a name="syntax"></a>語法  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`xmlns`|VSIX 語言套件結構描述定義的 XML 命名空間。|  
  
## <a name="xmlns-attribute"></a>xmlns 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|必要項。 定義語言組件的結構描述檔案的位置。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[LocalizedName 元素](../extensibility/localizedname-element-vsix-language-pack-schema.md)|必要項。 安裝延伸模組的當地語系化的名稱。|  
|[LocalizedDescription 元素](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|必要項。 安裝延伸模組的當地語系化的描述。|  
|[MoreInfoURL 元素](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|選擇性。 有關擴充功能的當地語系化資訊的連結。|  
|[License 元素](../extensibility/license-element-vsix-language-pack-schema.md)|選擇性。 當地語系化版本的延伸模組的授權檔案的路徑。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|None||  
  
## <a name="element-information"></a>項目資訊  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    命名空間    | http://schemas.microsoft.com/developer/vsx-schema-lp/2010 |
|   結構描述名稱   |                 VSIX 語言套件結構描述                 |
| 驗證檔 |                VSIXLanguagePackSchema.xsd                 |
|  可以是空白   |                            否                             |
  
## <a name="see-also"></a>另請參閱  
 [VSX 語言套件結構描述參考](../extensibility/vsx-language-pack-schema-reference.md)   
 [將 VSIX 封裝當地語系化](../extensibility/localizing-vsix-packages.md)   
 [VSIX 延伸結構描述 1.0 參考](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
