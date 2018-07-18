---
title: 'Iactivescriptprofilercallback3:: Setwebworkerid 方法 |Microsoft 文件'
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
ms.openlocfilehash: 426767b8d4d23964d6bfaa7102ee53b550e7ab9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724608"
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>IActiveScriptProfilerCallback3::SetWebWorkerId 方法
通知分析工具有關要用於此程式碼剖析工作階段的背景工作識別碼。 如果函式未在頁面的內容中執行，則這個方法是不叫用。 值`webWorkerId`會遞增每個背景工作，從 1 開始的 1。 ID 值不適合穩定超過工作階段，並只會對應至背景工作建立的順序。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>參數  
 `webWorkerId`  
 Web 背景工作識別碼。  
  
## <a name="return-value"></a>傳回值  
 這個方法的傳回值會忽略指令碼引擎。