---
title: ToggleHUD |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b224fdbd4dfadc6af29a0491bba5a18089c260b4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487781"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[ToggleHUD](https://docs.microsoft.com/visualstudio/debugger/graphics/togglehud)。  
  
切換 圖形診斷*抬頭顯示器*（抬頭顯示器） 重疊或關閉。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>備註  
 圖形診斷抬頭顯示器會顯示在圖形診斷下執行的應用程式的左上角。 它會顯示有關應用程式以及圖形資訊擷取，並由呼叫所加入的訊息，會產生執行階段資訊。 [AddMessage](../debugger/addmessage.md)成員函式。  
  
 若要切換抬頭顯示器，您不需要主動擷取圖形資訊 — 也就是透過執行個體的切換`VsgDbg`類別，但[Init](../debugger/init.md)成員函式不需要先呼叫。



