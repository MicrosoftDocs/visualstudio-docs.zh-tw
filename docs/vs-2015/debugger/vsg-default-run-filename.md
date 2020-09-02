---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2980d34028c58a6abadb2df21bf22c8d37cda6e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160766"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

定義圖形記錄檔的預設檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>參數  
 `filename`  
 當以程式設計方式捕捉圖形資訊時，預設會提供給圖形記錄檔的檔案名。  
  
## <a name="value"></a>值  
 表示圖形記錄檔檔案名的字串常值。 預設為 L "vsglog"。  
  
```cpp  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>備註  
 如果已定義預處理器符號 `DONT_SAVE_VSGLOG_TO_TEMP` ，則檔案名會相對於所捕獲應用程式的目前的目錄，或者是絕對路徑; 否則，它會相對於使用者的暫存檔案目錄，而不能是絕對路徑。  
  
 若要變更定義的檔案名，您必須在包含于程式之前重新定義該名稱 `vsgcapture.h` 。  
  
## <a name="example"></a>範例  
 此範例顯示如何變更 capture 檔案的預設檔案名：  
  
```cpp  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>另請參閱  
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)
