---
title: AddMessage |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de3460a345dba21e3a8f481adb510b9e3bdd4990
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="addmessage"></a>AddMessage
將自訂訊息加入至 圖形診斷*抬頭顯示器*（Hud 顯示）。  
  
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
 圖形診斷抬頭顯示器會顯示在圖形診斷下執行的應用程式的左上角。 它會顯示有關應用程式和圖形資訊的擷取，並由呼叫這個函式所加入的訊息，執行階段資訊。  
  
 若要將訊息加入至抬頭顯示器，您不需要主動擷取圖形資訊 — 也就是新增的訊息執行個體透過`VsgDbg`類別，但[Init](init.md)成員函式不適用於第一次呼叫。 訊息只會顯示在抬頭顯示器，所以不會記錄在圖形記錄檔中。