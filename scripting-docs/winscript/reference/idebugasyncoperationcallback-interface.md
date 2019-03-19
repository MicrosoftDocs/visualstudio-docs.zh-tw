---
title: IDebugAsyncOperationCallBack Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperationCallBack interface
ms.assetid: ccbe12fe-2aac-4d9f-9e70-601003f1a34d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 664c09a8262f2be474ea51a4e36cff40414e1cd2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146262"
---
# <a name="idebugasyncoperationcallback-interface"></a>IDebugAsyncOperationCallBack 介面
提供與 `IDebugAsyncOperation` 介面評估進度相關的狀態事件。  
  
## <a name="methods"></a>方法  
 除了繼承自方法`IUnknown`，則`IDebugAsyncOperationCallBack`介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugAsyncOperationCallBack::onComplete](../../winscript/reference/idebugasyncoperationcallback-oncomplete.md)|結果是可從非同步偵錯作業的訊號。|