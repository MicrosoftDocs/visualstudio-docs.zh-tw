---
title: IDebugClassField::D介面存在 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734506"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
確定是否在類中定義了特定介面。

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
[在]包含要尋找的介面名稱的字串。

## <a name="return-value"></a>傳回值
 如果成功,則返回S_OK,如果介面不存在,則返回S_FALSE;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法實際上獲取所有介面的枚舉,並搜索列表以尋找匹配的介面。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
