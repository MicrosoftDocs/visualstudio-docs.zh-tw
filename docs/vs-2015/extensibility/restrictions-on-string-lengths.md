---
title: 字串長度限制 |Microsoft Docs
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
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aa5517445930b5d543148af68df7eeeb29fa8a22
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499283"
---
# <a name="restrictions-on-string-lengths"></a>字串長度限制
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[字串長度限制](https://docs.microsoft.com/visualstudio/extensibility/restrictions-on-string-lengths)。  
  
原始檔控制外掛程式 API 限制各種函式中使用的字串的長度。  
  
## <a name="string-length-values"></a>字串長度值  
  
|常數|值|  
|--------------|-----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  長度不包含終止`null`。 其他常數"大小 _s"後置詞，而不是"_LEN 」 並包含終止的空間`null`。  
  
|常數|值|  
|--------------|-----------|  
|SCC_NAME_SIZE|32|  
|SCC_AUXLABEL_SIZE|32|  
|SCC_USER_SIZE|32|  
|SCC_PRJPATH_SIZE|301|  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)

