---
title: IDSymbol 元素 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7b4855fbdf2e395e6f309692fe531762e3ada7f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817564"
---
# <a name="idsymbol-element"></a>IDSymbol 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`IDSymbol`項目包含 guid: id 配對，表示功能表、 群組或命令的識別碼。 GUID 是來自父`GuidSymbol`項目。 `IDSymbol`項目具有`name`屬性，提供好記的名稱識別碼中包含的`value`屬性。  
  
## <a name="syntax"></a>語法  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|名稱|必要。 名稱的 ID 符號。|  
|value|必要。 識別碼符號的數值識別碼值。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[GuidSymbol 元素](../extensibility/guidsymbol-element.md)|包含 guid: id 配對，表示功能表、 群組或命令的 GUID。 將 `IDSymbol` 項目設為群組。|  
  
## <a name="remarks"></a>備註  
 每隔`IDSymbol`項目中的指定`GuidSymbol`項目必須具有唯一`value`。 不過，`IDSymbol`是在封裝中可以存在的項目具有相同的值，只要它們有不同的父代。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

