---
title: "IDebugSyncOperation 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugSyncOperation interface
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6705c2aa990aef3cf551a94546bf78a64026cecc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsyncoperation-interface"></a>IDebugSyncOperation 介面
可讓指令碼引擎抽象 （例如，運算式評估中） 需要特定的已封鎖執行緒中的巢狀時執行的作業。 介面也提供一種機制，正在取消作業沒有回應。  
  
 除了繼承自`IUnknown`、`IDebugSyncOperation`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|傳回這項同步作業的目標應用程式執行緒。|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|以同步方式執行操作，並傳回。|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|取消進行中的另一個執行緒上的作業。|