---
title: IRemoteDebugApplication110 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110 Interface
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d702699aa2e980c3be9d4d05eef96261a788788
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145092"
---
# <a name="iremotedebugapplication110-interface"></a>IRemoteDebugApplication110 介面
用來提供新功能，可以呼叫由指令碼偵錯工具和程序中的呼叫端。  
  
> [!IMPORTANT]
>  這個介面是由 PDM v11.0 和更新版本所實作。 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 `IRemoteDebugApplication110` 介面公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|呼叫以更新 偵錯工具選項。 選項預設值為 0 (SDO_NONE)。|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|傳回目前的已啟用的選項集。|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|傳回主執行緒呼叫 SetSite 的主機。|