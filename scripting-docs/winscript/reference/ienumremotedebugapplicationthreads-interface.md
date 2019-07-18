---
title: IEnumRemoteDebugApplicationThreads 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumRemoteDebugApplicationThreads interface
ms.assetid: 4ae6f8ef-e7be-4e2d-9be4-e0cde0a70eb1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d57e945593641036bbfbbecc90b790251c12075f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62807208"
---
# <a name="ienumremotedebugapplicationthreads-interface"></a>IEnumRemoteDebugApplicationThreads 介面
列舉應用程式中的執行中執行緒。  
  
 除了繼承自方法`IUnknown`，則`IEnumRemoteDebugApplicationThreads`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IEnumRemoteDebugApplicationThreads::Next](../../winscript/reference/ienumremotedebugapplicationthreads-next.md)|擷取指定的數目的列舉型別序列中的區段。|  
|[IEnumRemoteDebugApplicationThreads::Skip](../../winscript/reference/ienumremotedebugapplicationthreads-skip.md)|略過指定的數目的列舉型別序列中的區段。|  
|[IEnumRemoteDebugApplicationThreads::Reset](../../winscript/reference/ienumremotedebugapplicationthreads-reset.md)|將列舉型別序列重設到開頭。|  
|[IEnumRemoteDebugApplicationThreads::Clone](../../winscript/reference/ienumremotedebugapplicationthreads-clone.md)|建立列舉值，包含目前的列舉值相同的狀態。|