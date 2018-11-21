---
title: EndCapture |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3547de40190a7a591b3781d982f34378c3354044
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817551"
---
# <a name="endcapture"></a>EndCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

結束用來啟動在擷取間隔`BeginCapture`。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void EndCapture();  
```  
  
## <a name="remarks"></a>備註  
 在擷取間隔通常會跨越一個框架，例如當您想要擷取的相關特定種類的繪製呼叫的圖形資訊的子集。 如果擷取間隔跨越呼叫呈現，則會擷取圖形資訊的兩個框架。 第一個畫面格跨越的呼叫之間的間隔`BeginCapture`呈現; 的呼叫與第二個畫面格跨越呈現呼叫之後的第一個 Direct3D 事件和呼叫之間的間隔`EndCapture`。  
  
 若要擷取的間隔，您必須準備您的應用程式，來擷取和記錄的圖形資訊 — 也就是您必須先呼叫[Init](../debugger/init.md)的執行個體透過`VsgDbg`類別在呼叫之前`BeginCapture`或`EndCapture`。  
  
## <a name="see-also"></a>另請參閱  
 [BeginCapture](../debugger/begincapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)



