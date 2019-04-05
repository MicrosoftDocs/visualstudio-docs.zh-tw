---
title: GuidSymbol 元素 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f11ed48d9dcf961228957cf15db3815c00d14d7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941105"
---
# <a name="guidsymbol-element"></a>GuidSymbol 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`GuidSymbol`項目包含 guid: id 配對，表示功能表、 群組或命令的 GUID。 識別碼是來自`IDSymbol`中的項目`GuidSymbol`項目。 `GuidSymbol`項目具有`name`提供的 GUID，包含此功能的易記名稱的屬性`value`屬性。  
  
## <a name="syntax"></a>語法  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|名稱|必要項。 GUID 符號名稱。|  
|value|必要項。 GUID 符號的 GUID。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[IDSymbol 元素](../extensibility/idsymbol-element.md)|包含 guid: id 配對，表示功能表、 群組或命令的識別碼。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Symbols 元素](../extensibility/symbols-element.md)|群組`GuidSymbol`.vsct 檔案中的項目。|  
  
## <a name="remarks"></a>備註  
 一般而言，在.vsct 檔包含三種`GuidSymbol`中的項目及其`Symbols`區段，一個用於封裝本身、 一個命令集 （功能表、 群組和套件提供的命令的集合），，一個提供的點陣圖按鈕和其他視覺化元件的圖示。 每隔`IDSymbol`項目中的指定`GuidSymbol`項目必須具有唯一`value`。不過，`IDSymbol`是在封裝中可以存在的項目具有相同的值，只要它們有不同的父代。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
