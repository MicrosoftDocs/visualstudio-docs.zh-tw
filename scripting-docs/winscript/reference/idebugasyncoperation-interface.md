---
title: IDebugAsyncOperation 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 820ecc40924ace4153b76f46c8b8fd1603512ebb
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150812"
---
# <a name="idebugasyncoperation-interface"></a>IDebugAsyncOperation 介面
處理序偵錯管理員實作`IDebugAsyncOperation`介面。 語言引擎會呼叫`IDebugApplication::CreateAsyncDebugOperation`方法，以取得此介面的參考。 語言引擎就可以使用`IDebugAsyncOperation`介面，以提供同步偵錯作業的非同步存取。  
  
 除了繼承自方法`IUnknown`，則`IDebugAsyncOperation`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|傳回與這個物件相關聯的同步偵錯作業。|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|會導致開始非同步作業。|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|取消作業。|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|判斷是否已完成偵錯作業。|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|提供同步偵錯作業傳回的物件參數與傳回值。|