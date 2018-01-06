---
title: "VsgDbg 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e1a3810f6f0c2de6bffb2f97c2f1fc446ea3b6d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="vsgdbg-class"></a>VsgDbg 類別
表示程式設計的方式控制圖形診斷的應用程式元件的介面。  
  
## <a name="syntax"></a>語法  
  
```C++  
class VsgDbg;  
```  
  
## <a name="members"></a>成員  
 `VsgDbg`類別支援下列成員。  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (建構函式)](vsgdbg-vsgdbg-constructor.md)|建構的執行個體`VsgDbg`類別，並選擇性地準備主動擷取和記錄的圖形資訊的圖形診斷的應用程式元件。|  
|[VsgDbg::~VsgDbg (解構函式)](vsgdbg-tilde-vsgdbg-destructor.md)|終結的執行個體`VsgDbg`類別。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[AddMessage](addmessage.md)|將圖形診斷抬頭顯示器 （Hud 顯示器） 的自訂訊息。|  
|[BeginCapture](begincapture.md)|開始將結尾擷取間隔`EndCapture`。|  
|[CaptureCurrentFrame](capturecurrentframe.md)|擷取目前畫面的圖形記錄檔的其餘部分。|  
|[複製 (程式設計擷取)](copy-programmatic-capture.md)|將使用中的圖形記錄 (.vsglog) 檔案的內容複製到新的檔案。|  
|[EndCapture](endcapture.md)|已啟動，且在擷取間隔的結束`BeginCapture`。|  
|[Init](init.md)|準備主動擷取和記錄的圖形資訊的圖形診斷的應用程式元件。|  
|[ToggleHUD](togglehud.md)|開啟或關閉切換圖形診斷抬頭顯示器覆疊。|  
|[UnInit](uninit.md)|終結的圖形記錄檔，就會關閉它，並釋出應用程式的作用中記錄的圖形資訊時所使用的資源。|  
  
## <a name="remarks"></a>備註  
 `VsgDbg`類別代表介面可讓您以程式設計方式控制圖形診斷功能。 您可以使用某些功能，即使您未在擷取以及記錄圖形資訊;這包括`AddMessage`成員函式和`ToggleHUD`成員函式。 其他成員函式會準備圖形診斷來啟動或停止使用中的擷取圖形資訊的應用程式元件，或主動擷取和記錄到圖形記錄檔的圖形資訊的應用程式時，必須呼叫。