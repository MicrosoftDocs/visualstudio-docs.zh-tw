---
title: 'Vsgdbg:: Vsgdbg （建構函式） |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a35443dbf4fc413908c61e989d2138122c0991
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490694"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (建構函式)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[vsgdbg:: Vsgdbg （建構函式）](https://docs.microsoft.com/visualstudio/debugger/graphics/vsgdbg-vsgdbg-constructor)。  
  
建構的執行個體`VsgDbg`不論是否正在準備圖形診斷，以主動擷取和記錄的圖形資訊預設會根據指定的布林值參數的應用程式元件的類別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bDefaultInit`  
 `true` 以指定的圖形診斷的應用程式元件是準備好主動擷取與記錄圖形資訊;`false`來指定應用程式不應該準備主動擷取並記錄在此階段的圖形資訊。  
  
## <a name="remarks"></a>備註  
 當建構函式呼叫`bDefaultInit`設為`true`，圖形記錄檔的檔案名稱取決於如何`DONT_SAVE_VSGLOG_TO_TEMP`並`VSG_DEFAULT_RUN_FILENAME`之前所定義的前置處理器符號`vsgcapture.h`納入您的應用程式。  
  
 當建構函式呼叫`bDefaultInit`設定為`false`，在應用程式元件的圖形診斷可以準備好主動擷取與記錄圖形資訊稍後藉由呼叫`Init`函式。  
  
## <a name="see-also"></a>另請參閱  
 [VsgDbg:: ~ VsgDbg （解構函式）](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)



