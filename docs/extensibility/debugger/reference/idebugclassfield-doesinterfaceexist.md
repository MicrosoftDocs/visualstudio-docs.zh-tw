---
title: IDebugClassField：:D oesInterfaceExist |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba732b698f7372772142fda73e71d9e22aa443a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734506"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
判斷類別中是否已定義特定介面。

## <a name="syntax"></a>語法

```cpp
HRESULT DoesInterfaceExist( 
   LPCOLESTR pszInterfaceName
);
```

```csharp
int DoesInterfaceExist(
   [In] string pszInterfaceName
);
```

## <a name="parameters"></a>參數
`pszInterfaceName`\
在字串，其中包含要尋找的介面名稱。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK，如果介面不存在，則傳回 S_FALSE;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 此方法實際上會取得所有介面的列舉，並在清單中搜尋相符的介面。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
