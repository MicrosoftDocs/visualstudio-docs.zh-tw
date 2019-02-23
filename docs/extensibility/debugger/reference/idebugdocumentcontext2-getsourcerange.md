---
title: IDebugDocumentContext2::GetSourceRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 206ed65d4374a6dc9ec14d946ae6fabfb0aa3c8c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678585"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
取得此文件內容的來源的程式碼範圍。

## <a name="syntax"></a>語法

```cpp
HRESULT GetSourceRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetSourceRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

#### <a name="parameters"></a>參數
 `pBegPosition`

 [in、 out]A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)會填入的開始位置的結構。 如果不需要這項資訊，請將這個引數為 null 值。

 `pEndPosition`

 [in、 out]A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)會填入結束位置的結構。 如果不需要這項資訊，請將這個引數為 null 值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 來源範圍是從目前的陳述式後，終於貢獻程式碼的前一個陳述式之後的原始碼的整個範圍。 來源範圍通常用於混合來源陳述式，包括註解，以在反組譯碼視窗中的程式碼。

 若要取得範圍只是程式碼陳述式包含在此文件內容，請呼叫[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)