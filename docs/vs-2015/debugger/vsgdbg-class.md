---
title: VsgDbg 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f83f3060764df37411477333a92f04648d66204f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193084"
---
# <a name="vsgdbg-class"></a>VsgDbg 類別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

表示讓您以程式設計方式控制圖形診斷的應用程式元件的介面。  
  
## <a name="syntax"></a>語法  
  
```cpp  
class VsgDbg;  
```  
  
## <a name="members"></a>成員  
 `VsgDbg`類別支援下列成員。  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (建構函式)](../debugger/vsgdbg-vsgdbg-constructor.md)|建構的執行個體`VsgDbg`類別，並選擇性地準備 圖形診斷來主動擷取與記錄的圖形資訊的應用程式元件。|  
|[VsgDbg::~VsgDbg (解構函式)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|終結的執行個體`VsgDbg`類別。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[AddMessage](../debugger/addmessage.md)|將圖形診斷抬頭顯示器 （Hud 顯示器） 的自訂訊息。|  
|[BeginCapture](../debugger/begincapture.md)|開始會結束，在擷取間隔`EndCapture`。|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|擷取目前畫面的圖形記錄檔的其餘部分。|  
|[複製 (程式設計擷取)](../debugger/copy-programmatic-capture.md)|使用中的圖形記錄 (.vsglog) 檔案的內容複製到新的檔案。|  
|[EndCapture](../debugger/endcapture.md)|結束用來啟動在擷取間隔`BeginCapture`。|  
|[Init](../debugger/init.md)|準備圖形診斷來主動擷取與記錄的圖形資訊的應用程式元件。|  
|[ToggleHUD](../debugger/togglehud.md)|開啟或關閉，請切換圖形診斷抬頭顯示器覆疊。|  
|[UnInit](../debugger/uninit.md)|完成的圖形記錄檔、 關閉，並釋出應用程式的作用中記錄的圖形資訊時所使用的資源。|  
  
## <a name="remarks"></a>備註  
 `VsgDbg`類別代表的介面，可用來以程式設計方式控制圖形診斷功能。 您可以使用某些功能，即使您未主動擷取並記錄圖形資訊;這包括`AddMessage`成員函式和`ToggleHUD`成員函式。 其他成員函式會準備圖形診斷來啟動或停止作用中的擷取圖形資訊的應用程式元件，或主動擷取及記錄到圖形記錄檔的圖形資訊的應用程式時，必須呼叫。



