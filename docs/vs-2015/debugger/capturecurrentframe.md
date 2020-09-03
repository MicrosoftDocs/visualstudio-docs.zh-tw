---
title: CaptureCurrentFrame | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2718e800e2a31eb66319259ed1e43f2ab8b084c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161638"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

將目前框架的其餘部分捕獲到圖形記錄檔。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>備註  
 如果另一個捕捉正在進行中（例如，由函式啟動的 capture `BeginCapture` ），該 capture 就會完成，並記錄到圖形記錄檔中，做為不同的框架。 之後，圖形診斷會開始捕獲目前框架的其餘部分，也會記錄為不同的畫面格。 目前框架的結尾會以目前的呼叫來標示。  
  
 若要取得畫面格，您必須準備您的應用程式來捕獲和記錄圖形資訊，也就是說，您必須先透過類別的實例呼叫 [Init](../debugger/init.md) ， `VsgDbg` 才能呼叫 `CaptureCurrentFrame` 。  
  
## <a name="see-also"></a>另請參閱  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)
