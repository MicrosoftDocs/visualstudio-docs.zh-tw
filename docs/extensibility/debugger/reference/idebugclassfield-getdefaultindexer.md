---
title: IDebugClassField::GetDefaultIndexer |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f16f4dc94a5019fa66425f55c8f7706db566db9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
取得預設索引子名稱。  
  
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
  
#### <a name="parameters"></a>參數  
 `pbstrIndexer`  
 [out]傳回字串，包含預設索引子名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功的話，會傳回 S_OK，或如果沒有預設索引子會傳回 S_FALSE。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 類別的預設索引子會標示為屬性`Default`屬性的陣列存取。 這是特定[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]。 以下是範例中所宣告的預設索引子的[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]和使用方式。  
  
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
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)