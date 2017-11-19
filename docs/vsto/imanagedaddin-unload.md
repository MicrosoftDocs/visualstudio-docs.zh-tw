---
title: "IManagedAddin::Unload |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Unload method
ms.assetid: 40a73f07-2605-4745-8ac5-0a0189167fd7
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4c904d70ea72ba485405a64d4898acc90fffbab2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  卸載 Managed VSTO 增益集之前呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Unload();  
```  
  
## <a name="return-value"></a>傳回值  
 HRESULT 值，表示此方法是否已順利完成。  
  
## <a name="remarks"></a>備註  
 Microsoft Office 的目前版本不會呼叫這個方法。 這個方法是保留供日後使用。  
  
## <a name="see-also"></a>另請參閱  
 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
  
  