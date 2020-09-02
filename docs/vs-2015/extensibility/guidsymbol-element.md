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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204228"
---
# <a name="guidsymbol-element"></a>GuidSymbol 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`GuidSymbol`元素包含 guid： ID 組的 guid，代表功能表、群組或命令。 識別碼來自 `IDSymbol` 元素中的元素 `GuidSymbol` 。 專案 `GuidSymbol` 具有屬性， `name` 該屬性會提供 GUID 的易記名稱，該名稱包含在屬性中 `value` 。  
  
## <a name="syntax"></a>語法  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|NAME|必要。 GUID 符號的名稱。|  
|value|必要。 GUID 符號的 GUID。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[IDSymbol 項目](../extensibility/idsymbol-element.md)|包含代表功能表、群組或命令之 GUID： ID 組的識別碼。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Symbols 元素](../extensibility/symbols-element.md)|`GuidSymbol`將 .vsct 檔案中的元素群組在一起。|  
  
## <a name="remarks"></a>備註  
 一般而言，.vsct 檔案 `GuidSymbol` 會在其區段中包含三個元素 `Symbols` ，一個用於封裝本身，一個用於命令集 (封裝提供的功能表、群組和命令的集合) ，另一個則用於提供按鈕和其他視覺效果元件圖示的點陣圖。 `IDSymbol`指定專案中的每個元素都 `GuidSymbol` 必須有唯一的 `value` 。不過， `IDSymbol` 具有相同值的專案可以存在於封裝中，前提是它們有不同的父系。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
