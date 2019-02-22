---
title: ICanHandleException Interface | Microsoft Docs
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
ms.openlocfilehash: 23b886b9960742abf94cc44c3631a1123fc0e83d
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349968"
---
# <a name="icanhandleexception-interface"></a>ICanHandleException 介面
允許指令碼引擎來指定哪些例外狀況的呼叫端的呼叫端控制代碼。  
  
## <a name="methods"></a>方法  
 除了繼承自方法`IUnknown`，則`ICanHandleException`介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[ICanHandleException::CanHandleException](../../winscript/reference/icanhandleexception-canhandleexception.md)|決定是否指令碼引擎的呼叫端可以處理指定的例外狀況。|