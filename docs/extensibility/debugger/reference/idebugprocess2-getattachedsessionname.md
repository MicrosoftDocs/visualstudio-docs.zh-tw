---
title: IDebugProcess2::獲取附加會話名稱 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b70fd48adacdbbf936c6997fc373ad4a8d7e696b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724079"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
獲取調試此過程的工作階段的名稱。 IDE 可以向正在特定計算機上調試特定進程的用戶顯示此資訊。

> [!NOTE]
> 此方法被棄用,並且其實現應始終返回`E_NOTIMPL`。

## <a name="syntax"></a>語法

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>參數
`pbstrSessionName`\

## <a name="return-value"></a>傳回值
 此方法應始終傳`E_NOTIMPL`回 。

## <a name="see-also"></a>另請參閱
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
