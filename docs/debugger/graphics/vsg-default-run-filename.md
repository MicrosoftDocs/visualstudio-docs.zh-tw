---
title: VSG_DEFAULT_RUN_FILENAME |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 303bce554ff6345a37719a8d2f529f3c1ffe02e2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
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
  
## <a name="see-also"></a>另請參閱  
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)