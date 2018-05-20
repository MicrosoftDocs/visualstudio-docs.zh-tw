---
title: IManagedAddin::Unload
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 283fd069e0de72af92f7999871190c6c8a0d345b
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  卸載 Managed VSTO 增益集之前呼叫。  
  
## <a name="syntax"></a>語法  
  
```c++
HRESULT Unload();  
```  
  
## <a name="return-value"></a>傳回值  
 HRESULT 值，表示此方法是否已順利完成。  
  
## <a name="remarks"></a>備註  
 Microsoft Office 的目前版本不會呼叫這個方法。 這個方法是保留供日後使用。  
  
## <a name="see-also"></a>另請參閱  
 [IManagedAddin 介面](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
  
  