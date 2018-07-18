---
title: 'Vsgdbg:: Vsgdbg （建構函式） |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04f33b117a7ee47fb0c11932c3722f6f2a4a3541
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473299"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (建構函式)
建構的執行個體`VsgDbg`不論是否準備主動擷取和記錄的圖形資訊預設會根據指定的布林值參數的圖形診斷的應用程式元件的類別。  
  
## <a name="syntax"></a>語法  
  
```C++  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bDefaultInit`  
 `true` 若要指定要在應用程式元件的圖形診斷準備好主動擷取記錄的圖形資訊;`false`來指定應用程式不應該準備主動擷取和記錄在此階段的圖形資訊。  
  
## <a name="remarks"></a>備註  
 當建構函式呼叫與`bDefaultInit`設`true`，圖形記錄檔的檔案名稱取決於如何`DONT_SAVE_VSGLOG_TO_TEMP`和`VSG_DEFAULT_RUN_FILENAME`之前所定義的前置處理器符號`vsgcapture.h`隨附於您的應用程式。  
  
 當建構函式呼叫與`bDefaultInit`設`false`，圖形診斷的應用程式元件可以準備主動擷取和記錄在稍後的圖形資訊，藉由呼叫`Init`函式。  
  
## <a name="see-also"></a>另請參閱  
 [VsgDbg:: ~ VsgDbg （解構函式）](vsgdbg-tilde-vsgdbg-destructor.md)   
 [初始化](init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)