---
title: "IDebugAsyncOperation 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 157ed1248535855fcb53ca2eb6f49427fea94149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperation-interface"></a>IDebugAsyncOperation 介面
程序進行偵錯管理員實作`IDebugAsyncOperation`介面。 語言引擎會呼叫`IDebugApplication::CreateAsyncDebugOperation`方法，以取得此介面的參考。 語言引擎就可以使用`IDebugAsyncOperation`介面，以提供非同步存取為同步的偵錯作業。  
  
 除了繼承自`IUnknown`、`IDebugAsyncOperation`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|傳回這個物件相關聯的同步偵錯作業。|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|會導致開始非同步作業。|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|取消作業。|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|判定偵錯作業已完成。|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|提供傳回值和同步的偵錯作業傳回的物件參數。|