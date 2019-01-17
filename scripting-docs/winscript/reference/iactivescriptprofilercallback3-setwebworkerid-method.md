---
title: IActiveScriptProfilerCallback3::SetWebWorkerId 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4025dbee7b8b5b246163a1919aec335a8863937
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347212"
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>IActiveScriptProfilerCallback3::SetWebWorkerId 方法
通知分析工具有關要用於此程式碼剖析工作階段的背景工作角色識別碼。 如果函式不在頁面的內容中執行，則不被呼叫此方法。 值`webWorkerId`就會遞增 1，每個背景工作角色，從 1 開始。 穩定超過工作階段，並只會對應至背景工作角色建立所在的順序不適合的識別碼值。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>參數  
 `webWorkerId`  
 Web 背景工作角色識別碼。  
  
## <a name="return-value"></a>傳回值  
 這個方法的傳回值會忽略指令碼引擎。