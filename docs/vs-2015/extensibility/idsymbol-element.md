---
title: IDSymbol 元素 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4e686b5e105b0ea0aa80783137093679d4cad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203959"
---
# <a name="idsymbol-element"></a>IDSymbol 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`IDSymbol`元素包含 GUID： id 組的識別碼，代表功能表、群組或命令。 GUID 來自父 `GuidSymbol` 元素。 專案 `IDSymbol` 具有屬性， `name` 該屬性會提供識別碼的易記名稱，該名稱包含在屬性中 `value` 。  
  
## <a name="syntax"></a>語法  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|NAME|必要。 識別碼符號的名稱。|  
|value|必要。 識別碼符號的數值識別碼值。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[GuidSymbol 元素](../extensibility/guidsymbol-element.md)|包含代表功能表、群組或命令之 GUID： ID 組的 GUID。 將 `IDSymbol` 項目設為群組。|  
  
## <a name="remarks"></a>備註  
 `IDSymbol`指定專案中的每個元素都 `GuidSymbol` 必須有唯一的 `value` 。 不過， `IDSymbol` 具有相同值的專案可以存在於封裝中，前提是它們有不同的父系。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
