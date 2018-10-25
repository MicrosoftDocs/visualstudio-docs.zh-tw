---
title: 'Idiastackframe:: Get_type |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_type method
ms.assetid: 99daa97b-5c05-455d-bd1e-800762ccf7c9
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9108b4951b2ea32fdbaec2dfefe0d6d19e9164d0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866788"
---
# <a name="idiastackframegettype"></a>IDiaStackFrame::get_type
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取的框架類型。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回值，以從[StackFrameTypeEnum 列舉](../../debugger/debug-interface-access/stackframetypeenum.md)列舉型別。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`不支援的屬性。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [StackFrameTypeEnum 列舉](../../debugger/debug-interface-access/stackframetypeenum.md)



