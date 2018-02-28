---
title: "IRemoteDebugApplication110::SetDebuggerOptions |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::SetDebuggerOptions
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16782329de6268b309710e60e707d629fd9929a1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplication110setdebuggeroptions"></a>IRemoteDebugApplication110::SetDebuggerOptions
呼叫以更新偵錯工具選項。 這個方法應該呼叫之後[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)。 [IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)方法會自動重設為預設選項。 選項預設值為 0 (SDO_NONE)。  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)會實作由 PDM v11.0 和更新版本。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetDebuggerOptions(        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,        [in] enum SCRIPT_DEBUGGER_OPTIONS value    );  
```  
  
#### <a name="parameters"></a>參數  
 `mask`  
 [SCRIPT_DEBUGGER_OPTIONS 列舉](../../winscript/reference/script-debugger-options-enumeration.md)遮罩。  
  
 `value`  
 [SCRIPT_DEBUGGER_OPTIONS 列舉](../../winscript/reference/script-debugger-options-enumeration.md)值。  
  
## <a name="see-also"></a>另請參閱  
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 介面](../../winscript/reference/iremotedebugapplication110-interface.md)