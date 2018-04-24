---
title: DONT_SAVE_VSGLOG_TO_TEMP |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b70ddf2933b8bd2d96db1636612cb35a6a759a1a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
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
  
## <a name="see-also"></a>另請參閱  
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)