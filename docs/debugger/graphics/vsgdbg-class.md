---
title: VsgDbg 類別 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9235adfdf99bd898f8dcd074a3a3cd169161acf7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018692"
---
# <a name="vsgdbg-class"></a>VsgDbg 類別
表示讓您以程式設計方式控制圖形診斷的應用程式元件的介面。  
  
## <a name="syntax"></a>語法  
  
```C++  
class VsgDbg;  
```  
  
## <a name="members"></a>成員  
 `VsgDbg`類別支援下列成員。  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (建構函式)](vsgdbg-vsgdbg-constructor.md)|建構的執行個體`VsgDbg`類別，並選擇性地準備 圖形診斷來主動擷取與記錄的圖形資訊的應用程式元件。|  
|[VsgDbg::~VsgDbg (解構函式)](vsgdbg-tilde-vsgdbg-destructor.md)|終結的執行個體`VsgDbg`類別。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[AddMessage](addmessage.md)|將圖形診斷抬頭顯示器 （Hud 顯示器） 的自訂訊息。|  
|[BeginCapture](begincapture.md)|開始會結束，在擷取間隔`EndCapture`。|  
|[CaptureCurrentFrame](capturecurrentframe.md)|擷取目前畫面的圖形記錄檔的其餘部分。|  
|[複製 (程式設計擷取)](copy-programmatic-capture.md)|使用中的圖形記錄 (.vsglog) 檔案的內容複製到新的檔案。|  
|[EndCapture](endcapture.md)|結束用來啟動在擷取間隔`BeginCapture`。|  
|[Init](init.md)|準備圖形診斷來主動擷取與記錄的圖形資訊的應用程式元件。|  
|[ToggleHUD](togglehud.md)|開啟或關閉，請切換圖形診斷抬頭顯示器覆疊。|  
|[UnInit](uninit.md)|完成的圖形記錄檔、 關閉，並釋出應用程式的作用中記錄的圖形資訊時所使用的資源。|  
  
## <a name="remarks"></a>備註  
 `VsgDbg`類別代表的介面，可用來以程式設計方式控制圖形診斷功能。 您可以使用某些功能，即使您未主動擷取並記錄圖形資訊;這包括`AddMessage`成員函式和`ToggleHUD`成員函式。 其他成員函式會準備圖形診斷來啟動或停止作用中的擷取圖形資訊的應用程式元件，或主動擷取及記錄到圖形記錄檔的圖形資訊的應用程式時，必須呼叫。