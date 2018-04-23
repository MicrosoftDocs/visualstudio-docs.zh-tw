---
title: ToggleHUD |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86ce582ab49d4d079f01f7231f49aa761baa1069
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
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