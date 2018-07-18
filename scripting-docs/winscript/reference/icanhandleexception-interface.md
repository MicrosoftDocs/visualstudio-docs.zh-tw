---
title: ICanHandleException 介面 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bfd9fe2c766d3c390382ccfbcf2a8fd2319e48f5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725208"
---
# <a name="icanhandleexception-interface"></a>ICanHandleException 介面
允許指令碼引擎的呼叫端指定哪些例外狀況的呼叫端控制代碼。  
  
## <a name="methods"></a>方法  
 除了繼承自`IUnknown`、`ICanHandleException`介面會公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[ICanHandleException::CanHandleException](../../winscript/reference/icanhandleexception-canhandleexception.md)|決定是否指令碼引擎的呼叫端可以處理指定的例外狀況。|