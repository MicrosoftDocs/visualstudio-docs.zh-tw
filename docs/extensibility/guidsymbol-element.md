---
title: GuidSymbol 元素 |Microsoft Docs
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
ms.openlocfilehash: 16e7a1b84a6baa26b69545b3fa55e4434e5998f3
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500065"
---
# <a name="guidsymbol-element"></a>GuidSymbol 元素
`GuidSymbol`項目包含 guid: id 配對，表示功能表、 群組或命令的 GUID。 識別碼是來自`IDSymbol`中的項目`GuidSymbol`項目。 `GuidSymbol`項目具有`name`提供的 GUID，包含此功能的易記名稱的屬性`value`屬性。  
  
## <a name="syntax"></a>語法  
  
```xml  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|name|必要。 GUID 符號名稱。|  
|value|必要。 GUID 符號的 GUID。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[IDSymbol 元素](../extensibility/idsymbol-element.md)|包含 guid: id 配對，表示功能表、 群組或命令的識別碼。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[Symbols 元素](../extensibility/symbols-element.md)|群組`GuidSymbol`中的項目 *.vsct*檔案。|  
  
## <a name="remarks"></a>備註  
 通常 *.vsct*檔案包含三種`GuidSymbol`中的項目及其`Symbols`區段、 另一個用於封裝本身，一個 （集合的功能表群組，和封裝提供的命令） 的命令集，和其中一個按鈕和其他視覺元件提供圖示的點陣圖。 每隔`IDSymbol`項目中的指定`GuidSymbol`項目必須具有唯一`value`。不過，`IDSymbol`是在封裝中可以存在的項目具有相同的值，只要它們有不同的父代。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)