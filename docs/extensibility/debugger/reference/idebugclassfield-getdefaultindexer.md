---
description: 取得預設索引子的名稱。
title: IDebugClassField：： GetDefaultIndexer |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ebdcab870ba18d38fa6957d37f09abb65db000
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164210"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
取得預設索引子的名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetDefaultIndexer( 
   BSTR* pbstrIndexer
);
```

```csharp
int GetDefaultIndexer(
   out string pbstrIndexer
);
```

## <a name="parameters"></a>參數
`pbstrIndexer` 擴展傳回字串，其中包含預設索引子的名稱。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK，或如果沒有預設索引子，則傳回 S_FALSE。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 類別的預設索引子是標示為 `Default` 陣列存取屬性的屬性。 這是特有的 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] 。 以下是在中宣告的預設索引子範例 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] ，以及其使用方式。

```vb
Imports System.Collections;

Public Class Class1
    Private myList as Hashtable

    Default Public Property Item(ByVal Index As Integer) As Integer
        Get
            Return CType(List(Index), Integer)
        End Get
        Set(ByVal Value As Integer)
            List(Index) = Value
        End Set
    End Property
End Class

Function GetItem(Index as Integer) as Integer
    Dim classList as Class1 = new Class1
    Dim value as Integer

    ' Access array through default indexer
    value = classList(2)

    ' Access array through explicit property
    value = classList.Item(2)

    Return value
End Function
```

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
