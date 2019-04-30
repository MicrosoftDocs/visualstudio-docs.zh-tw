---
title: IDebugPortEx2::GetProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetProgram
helpviewer_keywords:
- IDebugPortEx2::GetProgram
ms.assetid: cd83a111-bfd5-4eae-b576-526466c6b6ec
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1fd56bf6705cb6e47e94422ab06261645d0d512
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871838"
---
# <a name="idebugportex2getprogram"></a>IDebugPortEx2::GetProgram
取得與程式節點相關聯的程式。

## <a name="syntax"></a>語法

```cpp
HRESULT GetProgram( 
   IDebugProgramNode2* pProgramNode,
   IDebugProgram2**    ppProgram
);
```

```csharp
int GetProgram( 
   IDebugProgramNode2 pProgramNode,
   out IDebugProgram2 ppProgram
);
```

#### <a name="parameters"></a>參數
 `pProgramNode`

 [in][IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件，表示程式節點。

 `ppProgram`

 [out]傳回[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，代表與程式節點相關聯的程式。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)