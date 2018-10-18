---
title: DONT_SAVE_VSGLOG_TO_TEMP |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 488baf1b2b01fe1491ccd00247e245e1642424d1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200001"
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

出現時，定義圖形記錄檔是否儲存到使用者的暫存檔目錄。  
  
## <a name="syntax"></a>語法  
  
```cpp  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>值  
 前置處理器符號會由其存在與否決定是否圖形記錄檔會儲存到使用者的 temporary files 目錄中。 如果這個符號已定義，則所定義的檔名`VSG_DEFAULT_RUN_FILENAME`擷取應用程式中，目前目錄的相對或絕對路徑; 檔案名稱所定義的否則為`VSG_DEFAULT_RUN_FILENAME`相對於使用者的暫存檔案目錄，而且不能是絕對路徑。  
  
## <a name="remarks"></a>備註  
 根據使用者的權限，圖形記錄檔可能無法儲存在任意位置。 我們建議您先想要將圖形記錄檔儲存到使用者的 temporary files 目錄或另一個已知良好的位置，如果您不確定是否要選擇的位置可以寫入至使用者。  
  
 若要避免圖形記錄檔儲存到 temporary files 目錄，您必須定義`DONT_SAVE_VSGLOG_TO_TEMP`您加入之前`vsgcapture.h`。  
  
## <a name="example"></a>範例  
 此範例示範如何將圖形記錄檔儲存至絕對路徑，在主機電腦上。  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)



