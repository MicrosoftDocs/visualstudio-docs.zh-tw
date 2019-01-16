---
title: CaptureCurrentFrame |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c96a931593771e381d8f526919a5180da1eb919a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990158"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
擷取目前畫面的圖形記錄檔的其餘部分。  
  
## <a name="syntax"></a>語法  
  
```C++  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>備註  
 如果另一個擷取目前正在進行中，例如擷取所啟動的`BeginCapture`函式，該擷取會完成，且會記錄到圖形記錄檔，做為不同的框架。 立即之後，圖形診斷會開始擷取目前的框架，也會記錄為不同的畫面格的其餘部分。 目前的框架結束是由呼叫呈現標記。  
  
 若要擷取的畫面格，您必須準備您的應用程式，來擷取和記錄的圖形資訊 — 也就是您必須先呼叫[Init](init.md)的執行個體透過`VsgDbg`類別在呼叫之前`CaptureCurrentFrame`。  
  
## <a name="see-also"></a>請參閱  
 [Init](init.md)   
 [BeginCapture](begincapture.md)