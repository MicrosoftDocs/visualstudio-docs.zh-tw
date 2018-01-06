---
title: "Idiaframedata:: Get_program |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 10d5d331c4308586485ea77824cda4864c6ee943
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
擷取用來計算目前的函式的呼叫之前設定的暫存器的程式字串。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回程式字串。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 程式字串是一串巨集，以便建立序言解譯。 例如，一般的堆疊框架可能會使用程式字串`"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`。 此格式為反向波蘭文標記法，其中運算子後面接著運算元。 `T0`表示在堆疊上的暫存變數。 這個範例會執行下列步驟：  
  
1.  將暫存器的內容移`ebp`至`T0`。  
  
2.  新增`4`值以`T0`產生地址、 從該位址，取得值，並將值儲存在暫存器`eip`。  
  
3.  取得值，從儲存在位址`T0`並將該值儲存在暫存器`ebp`。  
  
4.  新增`8`值以`T0`並將該值儲存在暫存器`esp`。  
  
 請注意，程式字串是特定的 cpu 和設定由目前的堆疊框架的函式的呼叫慣例。  
  
## <a name="see-also"></a>請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)