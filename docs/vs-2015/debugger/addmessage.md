---
title: AddMessage |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b60f8bac24b01e39327357b89e9e96c04765077
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248998"
---
# <a name="addmessage"></a>AddMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在圖形診斷會將自訂訊息*抬頭顯示器*（抬頭顯示器）。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>參數  
 `szMessage`  
 要加入至抬頭顯示器的訊息。  
  
## <a name="remarks"></a>備註  
 圖形診斷抬頭顯示器會顯示在圖形診斷下執行的應用程式的左上角。 它會顯示有關應用程式和圖形資訊擷取，並藉由呼叫此函式會新增訊息的執行階段資訊。  
  
 若要將訊息新增至抬頭顯示器，您不需要主動擷取圖形資訊 — 也就是新增的訊息，透過的執行個體`VsgDbg`類別，但[Init](../debugger/init.md)成員函式不適用於第一次呼叫。 訊息只會顯示在抬頭顯示器，所以不會記錄在圖形記錄檔中。



