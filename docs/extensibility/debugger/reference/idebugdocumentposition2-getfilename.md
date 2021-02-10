---
title: IDebugDocumentPosition2：： GetFileName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetFileName
helpviewer_keywords:
- IDebugDocumentPosition2::GetFileName
ms.assetid: d713635e-088f-465b-b26d-00ac971c9e86
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fde4f0eea0d873a22bde5771bfce9afa247e524f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946874"
---
# <a name="idebugdocumentposition2getfilename"></a>IDebugDocumentPosition2::GetFileName
取得包含檔位置之原始程式檔的檔案名。

## <a name="syntax"></a>語法

```cpp
HRESULT GetFileName( 
   BSTR* pbstrFileName
);
```

```csharp
int GetFileName( 
   out string pbstrFileName
);
```

## <a name="parameters"></a>參數
`pbstrFileName`\
擴展傳回來源檔案的檔案名。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 來源檔案不一定會有檔案名 (來源檔案可能不存在於磁片上，例如) 。

## <a name="see-also"></a>另請參閱
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
