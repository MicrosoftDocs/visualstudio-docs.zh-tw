---
title: VsgDbg：： VsgDbg () 的函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3bd179aea7d961df6145b7af2f074927fcdc3e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157445"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (建構函式)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`VsgDbg`使用或不准備圖形診斷的應用程式內元件，以根據指定的布林值參數，主動捕捉和記錄圖形資訊的類別實例。  
  
## <a name="syntax"></a>語法  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bDefaultInit`  
 `true` 若要指定圖形診斷的應用程式內元件要準備主動捕捉和記錄圖形資訊， `false` 若要指定應用程式目前不應準備主動捕捉及記錄圖形資訊。  
  
## <a name="remarks"></a>備註  
 當呼叫此函式時 `bDefaultInit` ，如果將設定為 `true` ，則圖形記錄檔的檔案名取決於 `DONT_SAVE_VSGLOG_TO_TEMP` 和預處理器符號的定義方式，然後才 `VSG_DEFAULT_RUN_FILENAME` `vsgcapture.h` 會包含在您的應用程式中。  
  
 當呼叫此函式時 `bDefaultInit` ，如果將設定為 `false` ，就可以準備圖形診斷的應用程式內元件，以便在稍後藉由呼叫函式來主動捕捉和記錄圖形資訊 `Init` 。  
  
## <a name="see-also"></a>另請參閱  
 [VsgDbg：： ~ VsgDbg () 的函式 ](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
