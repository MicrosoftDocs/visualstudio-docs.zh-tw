---
title: AddMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5aa23265c2f0d8d006d53faf575e2ea608c071d8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027525"
---
# <a name="addmessage"></a>AddMessage
在圖形診斷會將自訂訊息*抬頭顯示器*（抬頭顯示器）。  
  
## <a name="syntax"></a>語法  
  
```C++  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>參數  
 `szMessage`  
 要加入至抬頭顯示器的訊息。  
  
## <a name="remarks"></a>備註  
 圖形診斷抬頭顯示器會顯示在圖形診斷下執行的應用程式的左上角。 它會顯示有關應用程式和圖形資訊擷取，並藉由呼叫此函式會新增訊息的執行階段資訊。  
  
 若要將訊息新增至抬頭顯示器，您不需要主動擷取圖形資訊 — 也就是新增的訊息，透過的執行個體`VsgDbg`類別，但[Init](init.md)成員函式不適用於第一次呼叫。 訊息只會顯示在抬頭顯示器，所以不會記錄在圖形記錄檔中。