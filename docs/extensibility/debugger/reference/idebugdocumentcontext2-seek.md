---
title: IDebugDocumentContext2::Seek |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f001eb73e3c24ac1c9f15a4bd2c37c8d2cbe660e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709521"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
以指定數目的陳述式或字行中移動的文件內容。

## <a name="syntax"></a>語法

```cpp
HRESULT Seek( 
   int                      nCount,
   IDebugDocumentContext2** ppDocContext
);
```

```cpp
int Seek( 
   int                        nCount,
   out IDebugDocumentContext2 ppDocContext
);
```

#### <a name="parameters"></a>參數
 `nCount`

 [in]陳述式或移動，根據文件內容的程式行數目。

 `ppDocContext`

 [out]傳回新[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)物件做為新的位置。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)