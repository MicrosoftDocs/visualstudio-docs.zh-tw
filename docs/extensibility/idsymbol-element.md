---
title: IDSymbol 元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ef9ad479d44e43caf0a77c4db01cc349678c73ca
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836698"
---
# <a name="idsymbol-element"></a>IDSymbol 元素
`IDSymbol`項目包含 guid: id 配對，表示功能表、 群組或命令的識別碼。 GUID 是來自父`GuidSymbol`項目。 `IDSymbol`項目具有`name`屬性，提供好記的名稱識別碼中包含的`value`屬性。  
  
## <a name="syntax"></a>語法  
  
```xml  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|名稱|必要項。 名稱的 ID 符號。|  
|value|必要項。 識別碼符號的數值識別碼值。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[GuidSymbol 元素](../extensibility/guidsymbol-element.md)|包含 guid: id 配對，表示功能表、 群組或命令的 GUID。 將 `IDSymbol` 項目設為群組。|  
  
## <a name="remarks"></a>備註  
 每隔`IDSymbol`項目中的指定`GuidSymbol`項目必須具有唯一`value`。 不過，`IDSymbol`是在封裝中可以存在的項目具有相同的值，只要它們有不同的父代。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)