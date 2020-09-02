---
title: BeginCapture | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b16fdc4d0a12d7082400e697ca44a7ca4c549f9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431793"
---
# <a name="begincapture"></a>BeginCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

開始將結束的捕獲間隔 `EndCapture` 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void BeginCapture();  
```  
  
## <a name="remarks"></a>備註  
 捕捉間隔通常會跨越一個框架的子集，例如，當您只想要捕獲特定種類之繪製呼叫的圖形資訊時。 如果捕捉間隔超過呼叫的範圍，則會捕捉兩個圖形資訊框架。 第一個框架橫跨呼叫和目前的呼叫之間的間隔 `BeginCapture` ; 第二個框架則是在呼叫出現的和呼叫之後，跨越第一個 Direct3D 事件之間的間隔 `EndCapture` 。  
  
 若要取得間隔，您必須準備您的應用程式來捕獲和記錄圖形資訊，也就是說，您必須先透過類別的實例呼叫 [Init](../debugger/init.md) ， `VsgDbg` 才能呼叫 `BeginCapture` 或 `EndCapture` 。  
  
## <a name="see-also"></a>另請參閱  
 [EndCapture](../debugger/endcapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)
