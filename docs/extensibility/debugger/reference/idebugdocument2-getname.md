---
title: IDebugDocument2::GetName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f1ef243afd607a565e2c7a8e6f557f0b9906c86
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701013"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
取得數種形式之一的文件的名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetName( 
   GETNAME_TYPE gnType,
   BSTR*        pbstrFileName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE gnType,
   out string        pbstrFileName
);
```

#### <a name="parameters"></a>參數
 `gnType`

 [in]值，以從[GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)列舉，決定要傳回名稱的類型。

 `pbstrFileName`

 [out]傳回字串，包含文件名稱。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 為標題或檔案名稱或甚至是檔案名稱的一部分，這個方法可以比方說，會傳回文件的名稱。

## <a name="see-also"></a>另請參閱
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)