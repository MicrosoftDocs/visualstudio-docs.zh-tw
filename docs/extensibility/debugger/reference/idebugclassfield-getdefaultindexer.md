---
title: IDebugClassField::GetDefaultIndexer |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b3e12c9c572485e878f2dd489157ea020b6fe762
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>請參閱  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)