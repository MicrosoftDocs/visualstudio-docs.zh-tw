---
title: VSG_DEFAULT_RUN_FILENAME |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d82052c48444c8c22f205326cfb5ce614ac36aa7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485982"
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[VSG_DEFAULT_RUN_FILENAME](https://docs.microsoft.com/visualstudio/debugger/graphics/vsg-default-run-filename)。  
  
定義圖形記錄檔的預設檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>參數  
 `filename`  
 當以程式設計方式擷取圖形資訊，指定預設圖形記錄檔的檔名。  
  
## <a name="value"></a>值  
 字串常值，表示檔案名稱的圖形記錄檔。 根據預設，L"default.vsglog"。  
  
```cpp  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>備註  
 如果前置處理器符號`DONT_SAVE_VSGLOG_TO_TEMP`是定義，然後檔案名稱是相對於目前的目錄，擷取應用程式，或者是絕對路徑; 否則它是相對於使用者的 temporary files 目錄，不能是絕對路徑。  
  
 若要變更定義的檔案名稱，您必須重新定義它後再納入`vsgcapture.h`在程式中。  
  
## <a name="example"></a>範例  
 此範例示範如何變更擷取檔案的預設檔案名稱：  
  
```cpp  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>另請參閱  
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)



