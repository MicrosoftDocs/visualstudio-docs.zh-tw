---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 68ef36185c193263db386a1e1f80877c0327440c
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874337"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  卸載 Managed VSTO 增益集之前呼叫。  
  
## <a name="syntax"></a>語法  
  
```csharp
HRESULT Unload();  
```  
  
## <a name="return-value"></a>傳回值  
 HRESULT 值，表示此方法是否已順利完成。  
  
## <a name="remarks"></a>備註  
 Microsoft Office 的目前版本不會呼叫這個方法。 這個方法是保留供日後使用。  
  
## <a name="see-also"></a>另請參閱  
 [IManagedAddin 介面](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
