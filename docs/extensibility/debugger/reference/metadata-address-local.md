---
title: METADATA_ADDRESS_LOCAL |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 720f150be1b7cf992f0949750dd52218939c7d2e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="metadataaddresslocal"></a>METADATA_ADDRESS_LOCAL
此結構表示 （通常是函式或方法） 的範圍內的區域變數的位址。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```csharp  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## <a name="terms"></a>詞彙  
 tokMethod  
 識別碼的方法或函式本機變數是的一部分。  
  
 [C + +]`_mdToken`是`typedef`32 位元`int`。  
  
 pLocal  
 此結構表示的位址語彙基元。  
  
 dwIndex  
 可以是這個方法或函式，或其他值 （語言特有） 的本機變數的索引。  
  
## <a name="remarks"></a>備註  
 這個結構是中的等位的一部分[DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)結構時`dwKind`欄位`DEBUG_ADDRESS_UNION`結構設為`ADDRESS_KIND_LOCAL`(介於[ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)列舉型別）。  
  
 `Warning:` [只有 c + +] 如果`pLocal`不是 null，則您必須呼叫`Release`語彙基元的指標 (`addr`是中的欄位[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構):  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)