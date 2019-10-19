---
title: IDebugApplication：： FCanJitDebug |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FCanJitDebug
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FCanJitDebug
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d68240ffd86935e9936642c09d5131f70b46e9ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576869"
---
# <a name="idebugapplicationfcanjitdebug"></a>IDebugApplication::FCanJitDebug
判斷是否已註冊即時（JIT）偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```cpp
BOOL FCanJitDebug();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法不接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功且已註冊 JIT 偵錯程式，則方法會傳回 `TRUE`。 否則它會傳回 `FALSE`。  
  
## <a name="remarks"></a>備註  
 這個方法會判斷是否已註冊 JIT 偵錯程式。  
  
## <a name="see-also"></a>請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)