---
title: GuidSymbol 項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d5e3a3f4d33e166d344669dbeb4bc1a877335f0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|name|必要。 GUID 符號名稱。|  
|value|必要。 GUID 符號的 GUID。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[IDSymbol 元素](../extensibility/idsymbol-element.md)|包含 guid: id 配對，代表功能表、 群組或命令的識別碼。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Symbols 元素](../extensibility/symbols-element.md)|群組`GuidSymbol`.vsct 檔中的項目。|  
  
## <a name="remarks"></a>備註  
 .Vsct 檔通常包含三種`GuidSymbol`中的項目及其`Symbols`> 一節，另一個用於封裝本身、 命令集 （功能表、 群組和命令，可讓封裝的集合）、 一個，一個用於提供的點陣圖按鈕和其他視覺化元件的圖示。 每個`IDSymbol`中的項目指定`GuidSymbol`項目必須具有唯一`value`。不過，`IDSymbol`封裝中可以存在有相同的值的項目，只要他們有不同父代。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)