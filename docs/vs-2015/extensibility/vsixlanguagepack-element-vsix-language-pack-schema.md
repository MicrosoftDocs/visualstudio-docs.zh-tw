---
title: VSIXLanguagePack 元素（VSIX 語言套件架構） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2e1df362fddeab5be98ff90460a8a1a7d4b7876
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557998"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>VSIXLanguagePack 元素（VSIX 語言套件架構）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

必要。 提供 VSIX 語言套件的根項目。 VSIX 語言套件提供 VSIX 封裝的當地語系化安裝資訊。  
  
## <a name="syntax"></a>語法  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`xmlns`|定義 VSIX 語言套件架構的 XML 命名空間。|  
  
## <a name="xmlns-attribute"></a>xmlns 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|必要。 檔案的位置，可定義語言套件的架構。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[LocalizedName 元素](../extensibility/localizedname-element-vsix-language-pack-schema.md)|必要。 要安裝之延伸模組的當地語系化名稱。|  
|[LocalizedDescription 元素](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|必要。 要安裝之延伸模組的當地語系化描述。|  
|[MoreInfoURL 元素](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|選擇性。 延伸模組的當地語系化資訊連結。|  
|[License 元素](../extensibility/license-element-vsix-language-pack-schema.md)|選擇性。 延伸模組的當地語系化版本授權檔案的路徑。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|None||  
  
## <a name="element-information"></a>項目資訊  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    命名空間    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   結構描述名稱   |                 VSIX 語言套件架構                 |
| 驗證檔 |                VSIXLanguagePackSchema .xsd                 |
|  可以是空的   |                            否                             |
  
## <a name="see-also"></a>另請參閱  
 [VSX 語言套件架構參考](../extensibility/vsx-language-pack-schema-reference.md)[當地語系化 Vsix 封裝](../extensibility/localizing-vsix-packages.md) [Vsix 延伸模組架構1.0 參考](/previous-versions/dd393700(v=vs.110))
