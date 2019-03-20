---
title: IEnumRemoteDebugApplications 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumRemoteDebugApplications interface
ms.assetid: ceb5fbe7-d131-4352-9dd1-af80acd3f3f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 430551002bc7603d86f9c7fb624ec438734bd766
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150617"
---
# <a name="ienumremotedebugapplications-interface"></a>IEnumRemoteDebugApplications 介面
列舉應用程式物件。 此介面可用來列舉"附加至應用程式 」 的對話方塊中的機器上執行的應用程式。  
  
 除了繼承自方法`IUnknown`，則`IEnumRemoteDebugApplications`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IEnumRemoteDebugApplications::Clone](../../winscript/reference/ienumremotedebugapplications-clone.md)|建立列舉值，包含目前的列舉值相同的狀態。|  
|[IEnumRemoteDebugApplications::Next](../../winscript/reference/ienumremotedebugapplications-next.md)|擷取指定的數目的列舉型別序列中的區段。|  
|[IEnumRemoteDebugApplications::Reset](../../winscript/reference/ienumremotedebugapplications-reset.md)|將列舉型別序列重設到開頭。|  
|[IEnumRemoteDebugApplications::Skip](../../winscript/reference/ienumremotedebugapplications-skip.md)|略過指定的數目的列舉型別序列中的區段。|