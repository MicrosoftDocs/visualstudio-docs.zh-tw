---
title: "ToggleHUD |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bf1e27b9385257203653f3bff5241f6c3875373
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="togglehud"></a>ToggleHUD
切換 圖形診斷*抬頭顯示器*（Hud 顯示器） 重疊或關閉。  
  
## <a name="syntax"></a>語法  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>備註  
 圖形診斷抬頭顯示器會顯示在圖形診斷下執行的應用程式的左上角。 它會顯示有關應用程式以及圖形資訊擷取和訊息所新增的呼叫的執行階段資訊[AddMessage](addmessage.md)成員函式。  
  
 若要切換抬頭顯示器，您不需要主動擷取圖形資訊 — 也就是透過執行個體切換`VsgDbg`類別，但是[Init](init.md)成員函式沒有先呼叫。