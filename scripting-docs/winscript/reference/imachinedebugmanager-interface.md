---
title: IMachineDebugManager 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManager interface
ms.assetid: 0b7133bb-5a52-4036-b4db-d69260790db7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d491b03ba04d346e3a14a08d5e2b6b9d34c7d97
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573926"
---
# <a name="imachinedebugmanager-interface"></a>IMachineDebugManager 介面
電腦 Debug Manager 的主要介面。 這個介面類別似于 `IMachineDebugManagerCookie` 介面。  
  
 除了繼承自 `IUnknown` 的方法之外，`IMachineDebugManager` 介面也會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IMachineDebugManager::AddApplication](../../winscript/reference/imachinedebugmanager-addapplication.md)|將應用程式新增至執行中的應用程式清單。|  
|[IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)|從執行中的應用程式清單中移除應用程式。|  
|[IMachineDebugManager::EnumApplications](../../winscript/reference/imachinedebugmanager-enumapplications.md)|傳回目前正在執行之應用程式清單的列舉值。|  
  
## <a name="see-also"></a>請參閱  
 [IMachineDebugManagerCookie 介面](../../winscript/reference/imachinedebugmanagercookie-interface.md)