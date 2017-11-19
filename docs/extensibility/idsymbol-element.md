---
title: "IDSymbol 項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 734d05dd013be9a3d6c4a173a5c7abc7a01ef2d8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idsymbol-element"></a>IDSymbol 項目
`IDSymbol`項目包含 guid: id 配對，代表功能表、 群組或命令的識別碼。 GUID 是來自父`GuidSymbol`項目。 `IDSymbol`項目具有`name`提供包含此識別碼的易記名稱的屬性`value`屬性。  
  
## <a name="syntax"></a>語法  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|name|必要項。 識別碼符號名稱。|  
|值|必要項。 識別碼符號的數值識別碼值。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[GuidSymbol 元素](../extensibility/guidsymbol-element.md)|包含 guid: id 配對，代表功能表、 群組或命令的 GUID。 將 `IDSymbol` 項目設為群組。|  
  
## <a name="remarks"></a>備註  
 每個`IDSymbol`中的項目指定`GuidSymbol`項目必須具有唯一`value`。 不過，`IDSymbol`封裝中可以存在有相同的值的項目，只要他們有不同父代。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)