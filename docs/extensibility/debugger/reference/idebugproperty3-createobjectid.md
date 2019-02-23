---
title: IDebugProperty3::CreateObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a523dd7886e46cf1df7c6e70024a052f62ca4748
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694916"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
建立此屬性以確保它是唯一的所有其他屬性的唯一識別碼。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 當工作階段的偵錯管理員想要確定此屬性會唯一識別以及所有其他屬性，會呼叫這個方法。 偵錯引擎 (DE) 支援此方法，除非已經唯一識別它處理的屬性。 如果裝置不支援這個方法，它會傳回`E_NOTIMPL`。

 任何唯一的識別碼以建立`CreateObjectID`時終結[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)呼叫方法時，這也表示用來唯一識別此屬性需要的結束。

> [!NOTE]
>  沒有任何方法來擷取這個唯一識別碼，因此 DE 可以執行它想要的任何唯一的識別碼時`CreateObjectID`呼叫方法。

## <a name="see-also"></a>另請參閱
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)