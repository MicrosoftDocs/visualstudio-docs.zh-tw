---
title: IDebugProcess2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetName
helpviewer_keywords:
- IDebugProcess2::GetName
ms.assetid: a2f66ab5-53e5-4cdc-a1b5-3b8afa8ee646
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: acaa43d4a9afe1084502c44f5221bc8518a9bd3e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713317"
---
# <a name="idebugprocess2getname"></a>IDebugProcess2::GetName
取得標題、 易記名稱或處理序檔案名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetName( 
   GETNAME_TYPE  gnType,
   BSTR*         pbstrName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE  gnType,
   out string         pbstrName
);
```

#### <a name="parameters"></a>參數
 `gnType`

 [in]值，以從[GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)列舉，指定要傳回名稱的類型。

 `pbstrName`

 [out]傳回處理序的名稱。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)