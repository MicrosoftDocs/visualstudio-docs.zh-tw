---
title: ICanHandleException Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ICanHandleException interface
ms.assetid: 32df7f81-557d-40cf-a844-06a6eaa292f3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 363a52cfeb409d293ba3589b9d869bbc4fdf5918
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991337"
---
# <a name="icanhandleexception-interface"></a>ICanHandleException 介面
允許指令碼引擎來指定哪些例外狀況的呼叫端的呼叫端控制代碼。  
  
## <a name="methods"></a>方法  
 除了繼承自方法`IUnknown`，則`ICanHandleException`介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[ICanHandleException::CanHandleException](../../winscript/reference/icanhandleexception-canhandleexception.md)|決定是否指令碼引擎的呼叫端可以處理指定的例外狀況。|