---
title: "GuidSymbol 項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5dcad9882b1c72c15837529d736eeabff58f3826
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="guidsymbol-element"></a>GuidSymbol 項目
`GuidSymbol`項目包含 guid: id 配對，代表功能表、 群組或命令的 GUID。 識別碼是來自`IDSymbol`中的項目`GuidSymbol`項目。 `GuidSymbol`項目具有`name`所提供的 GUID 中才包含的好記名稱屬性`value`屬性。  
  
## <a name="syntax"></a>語法  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|name|必要項。 GUID 符號名稱。|  
|值|必要項。 GUID 符號的 GUID。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|[IDSymbol 元素](../extensibility/idsymbol-element.md)|包含 guid: id 配對，代表功能表、 群組或命令的識別碼。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[Symbols 元素](../extensibility/symbols-element.md)|群組`GuidSymbol`.vsct 檔中的項目。|  
  
## <a name="remarks"></a>備註  
 .Vsct 檔通常包含三種`GuidSymbol`中的項目及其`Symbols`> 一節，另一個用於封裝本身、 命令集 （功能表、 群組和命令，可讓封裝的集合）、 一個，一個用於提供的點陣圖按鈕和其他視覺化元件的圖示。 每個`IDSymbol`中的項目指定`GuidSymbol`項目必須具有唯一`value`。不過，`IDSymbol`封裝中可以存在有相同的值的項目，只要他們有不同父代。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)