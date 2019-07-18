---
title: 字串長度限制 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc6ff1e77a9a973e184384d98ef8b880aaa2f005
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432527"
---
# <a name="restrictions-on-string-lengths"></a>字串長度限制
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

原始檔控制外掛程式 API 限制各種函式中使用的字串的長度。  
  
## <a name="string-length-values"></a>字串長度值  
  
|常數|值|  
|--------------|-----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
> 長度不包含終止`null`。 其他常數"大小 _s"後置詞，而不是"_LEN 」 並包含終止的空間`null`。  
  
|常數|值|  
|--------------|-----------|  
|SCC_NAME_SIZE|32|  
|SCC_AUXLABEL_SIZE|32|  
|SCC_USER_SIZE|32|  
|SCC_PRJPATH_SIZE|301|  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
