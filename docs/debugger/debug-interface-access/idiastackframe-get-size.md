---
title: 'Idiastackframe:: Get_size |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_size method
ms.assetid: 71e2f5ab-4aa8-4922-aa8a-b7db97ee143c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4988bf047bf500c7d7cd8a17a4783cac47596833
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861380"
---
# <a name="idiastackframegetsize"></a>IDiaStackFrame::get_size
擷取堆疊框架，以位元組為單位的大小。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_size (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回以位元組為單位的堆疊框架的大小。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`不支援的屬性。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)