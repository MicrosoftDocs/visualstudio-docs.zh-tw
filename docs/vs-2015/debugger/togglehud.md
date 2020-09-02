---
title: ToggleHUD | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 87c2571926b92e59ae03e5e988bbf535474dc6d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144583"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

切換 [圖形診斷] *抬頭顯示器* (上層顯示) 重迭顯示或關閉。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>備註  
 [圖形診斷] 抬頭顯示器會顯示在 [圖形診斷] 下執行之應用程式的左上角。 它會顯示應用程式的執行時間資訊，以及有關圖形資訊捕捉的執行時間資訊，以及藉由呼叫 [AddMessage](../debugger/addmessage.md) 成員函式而加入的訊息。  
  
 若要切換抬頭顯示器，您不需要主動捕捉圖形資訊，也就是可以透過類別的實例來切換 `VsgDbg` ，但不需要先呼叫 [Init](../debugger/init.md) 成員函式。
