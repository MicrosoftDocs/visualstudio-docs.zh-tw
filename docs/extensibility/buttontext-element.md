---
title: "ButtonText 項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c9f2374af403c37f18d1aa91700e51bd038a71c6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="buttontext-element"></a>ButtonText 項目
此欄位可讓您指定各種功能表所顯示的文字。 根據預設，`ButtonText`元素會出現在功能表控制器。 `ButtonText`項目也會成為預設值，如果是空白的其他文字欄位。 `ButtonText`元素不可為空白，即使指定的文字欄位。  
  
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
 文字值`ButtonText`項目會提供功能表項目、 組合，以及某些使用者介面 (UI) 項目所顯示的文字顯示的文字。  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)