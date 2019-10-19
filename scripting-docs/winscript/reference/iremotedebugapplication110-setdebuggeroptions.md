---
title: IRemoteDebugApplication110：： SetDebuggerOptions |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::SetDebuggerOptions
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7168a4ef8ec70368c0ff691ba1f721275f9d65d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577416"
---
# <a name="iremotedebugapplication110setdebuggeroptions"></a>IRemoteDebugApplication110::SetDebuggerOptions
呼叫以更新偵錯工具選項。 在[IRemoteDebugApplication：： ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)之後，應該呼叫這個方法。 [IRemoteDebugApplication：:D isconnectdebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)方法會自動重設為預設選項。 選項預設為0（SDO_NONE）。  
  
> [!IMPORTANT]
> [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)是由 PDM 11.0 和更新版本所執行。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetDebuggerOptions(        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,        [in] enum SCRIPT_DEBUGGER_OPTIONS value    );  
```  
  
#### <a name="parameters"></a>參數  
 `mask`  
 [SCRIPT_DEBUGGER_OPTIONS 列舉](../../winscript/reference/script-debugger-options-enumeration.md)遮罩。  
  
 `value`  
 [SCRIPT_DEBUGGER_OPTIONS 列舉](../../winscript/reference/script-debugger-options-enumeration.md)值。  
  
## <a name="see-also"></a>請參閱  
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 介面](../../winscript/reference/iremotedebugapplication110-interface.md)