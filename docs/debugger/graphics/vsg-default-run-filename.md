---
title: "VSG_DEFAULT_RUN_FILENAME |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f7fe31b96911329089174772094784c0d0f3371c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
定義圖形記錄檔的預設檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```C++  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>參數  
 `filename`  
 預設的圖形記錄檔時指定以程式設計方式擷取圖形資訊的檔案名稱。  
  
## <a name="value"></a>值  
 字串常值所代表的檔案名稱的圖形記錄檔。 根據預設，L"default.vsglog"。  
  
```C++  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>備註  
 如果前置處理器符號`DONT_SAVE_VSGLOG_TO_TEMP`是定義，然後檔案名稱是相對於目前目錄擷取應用程式，或者是絕對路徑; 否則相對於使用者的暫存檔案的目錄，而且不能是絕對路徑。  
  
 若要變更定義的檔案名稱，您必須重新定義它後再納入`vsgcapture.h`程式中。  
  
## <a name="example"></a>範例  
 此範例顯示如何變更擷取檔案的預設檔案名稱：  
  
```C++  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>請參閱  
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)