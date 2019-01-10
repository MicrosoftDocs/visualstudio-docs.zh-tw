---
title: DONT_SAVE_VSGLOG_TO_TEMP |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d945f3ef7fe2c5aa2abb0bd2263bae693d517f7c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859151"
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
出現時，定義圖形記錄檔是否儲存到使用者的暫存檔目錄。  

## <a name="syntax"></a>語法  

```C++  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  

## <a name="value"></a>值  
 前置處理器符號會由其存在與否決定是否圖形記錄檔會儲存到使用者的 temporary files 目錄中。 如果這個符號已定義，則所定義的檔名`VSG_DEFAULT_RUN_FILENAME`擷取應用程式中，目前目錄的相對或絕對路徑; 檔案名稱所定義的否則為`VSG_DEFAULT_RUN_FILENAME`相對於使用者的暫存檔案目錄，而且不能是絕對路徑。  

## <a name="remarks"></a>備註  
 根據使用者的權限，圖形記錄檔可能無法儲存在任意位置。 我們建議您先想要將圖形記錄檔儲存到使用者的 temporary files 目錄或另一個已知良好的位置，如果您不確定是否要選擇的位置可以寫入至使用者。  

 若要避免圖形記錄檔儲存到 temporary files 目錄，您必須定義`DONT_SAVE_VSGLOG_TO_TEMP`您加入之前`vsgcapture.h`。  

## <a name="example"></a>範例  
 此範例示範如何將圖形記錄檔儲存至絕對路徑，在主機電腦上。  

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  

#include <vsgcapture.h>  
```  

## <a name="see-also"></a>請參閱  
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
