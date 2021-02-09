---
title: VsgDbg 類別 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 67bce62612a85e0bcff5e51cd07d4c374e13b01e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861396"
---
# <a name="vsgdbg-class"></a>VsgDbg 類別
表示介面，可讓您以程式設計方式控制圖形診斷的應用程式內元件。

## <a name="syntax"></a>語法

```C++
class VsgDbg;
```

## <a name="members"></a>成員
 `VsgDbg`類別支援下列成員。

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[VsgDbg::VsgDbg (建構函式)](vsgdbg-vsgdbg-constructor.md)|會建立類別的實例 `VsgDbg` ，並選擇性地準備圖形診斷的應用程式內元件，以主動捕捉和記錄圖形資訊。|
|[VsgDbg::~VsgDbg (解構函式)](vsgdbg-tilde-vsgdbg-destructor.md)|終結類別的實例 `VsgDbg` 。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[AddMessage](addmessage.md)|將自訂訊息新增至 [圖形診斷] 抬頭顯示器 (上層顯示) 。|
|[BeginCapture](begincapture.md)|開始將結束的捕獲間隔 `EndCapture` 。|
|[CaptureCurrentFrame](capturecurrentframe.md)|將目前框架的其餘部分捕獲到圖形記錄檔。|
|[複製 (程式設計擷取)](copy-programmatic-capture.md)|將現用圖形記錄檔 ( 的內容複寫到新的檔案中。 vsglog) 檔案。|
|[EndCapture](endcapture.md)|結束以啟動的捕獲間隔 `BeginCapture` 。|
|[Init](init.md)|準備圖形診斷的應用程式內元件，以主動捕捉及記錄圖形資訊。|
|[ToggleHUD](togglehud.md)|切換圖形診斷抬頭顯示器重迭開啟或關閉。|
|[UnInit](uninit.md)|完成圖形記錄檔、將其關閉，並釋放應用程式主動記錄圖形資訊時所使用的資源。|

## <a name="remarks"></a>備註
 `VsgDbg`類別代表您可以用來以程式設計方式控制圖形診斷功能的介面。 即使您不主動捕捉和錄製圖形資訊，還是可以使用某些功能;這包括成員函式 `AddMessage` 和 `ToggleHUD` 成員函式。 另一個成員函式會準備圖形診斷的應用程式內元件，以啟動或停止圖形資訊的主動式抓取，或者必須在應用程式主動捕獲圖形資訊並將其記錄到圖形記錄檔時呼叫。