---
title: ButtonText 元素 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d7cbf92a762fd3fce80e7f59e77c03c8cd81cc22
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485834"
---
# <a name="buttontext-element"></a>ButtonText 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[ButtonText 元素](https://docs.microsoft.com/visualstudio/extensibility/buttontext-element)。  
  
此欄位可讓您指定各種功能表所顯示的文字。 根據預設，`ButtonText`元素會出現在功能表控制站。 `ButtonText`項目也會成為預設值，如果其他的文字欄位為空白。 `ButtonText`元素不可為空白，即使指定的其他文字欄位。  
  
## <a name="syntax"></a>語法  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Strings 元素](../extensibility/strings-element.md)|群組文字項目，例如`ButtonText`和`CommandName`。|  
  
## <a name="text-value"></a>文字值  
 文字值`ButtonText`項目提供為功能表項目、 combos 和其他可見文字的使用者介面 (UI) 項目顯示的文字。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

