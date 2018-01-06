---
title: "DONT_SAVE_VSGLOG_TO_TEMP |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5a98081aa73d11d9a2edea9293804d6c83a211d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
出現時，定義圖形記錄檔是否儲存到使用者的暫存檔目錄。  
  
## <a name="syntax"></a>語法  
  
```C++  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>值  
 前置處理器符號，其存在與否的決定是否圖形記錄檔會儲存到使用者的暫存檔目錄。 如果這個符號已定義，則所定義的檔案名稱`VSG_DEFAULT_RUN_FILENAME`擷取應用程式時，目前目錄的相對或絕對路徑; 否則檔案名稱會由`VSG_DEFAULT_RUN_FILENAME`相對於使用者的暫存檔案的目錄，不能是絕對路徑。  
  
## <a name="remarks"></a>備註  
 根據使用者的權限，圖形記錄檔可能無法儲存在任意的位置。 我們建議您先想要將圖形記錄儲存到使用者的暫存檔的目錄或另一個已知正確的位置，如果您不確定是否要選擇的位置可以被寫回由使用者。  
  
 若要防止圖形記錄檔儲存到暫存檔目錄中，您必須定義`DONT_SAVE_VSGLOG_TO_TEMP`您包含之前`vsgcapture.h`。  
  
## <a name="example"></a>範例  
 這個範例示範如何在主機上，將圖形記錄檔儲存至絕對路徑。  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>請參閱  
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)