---
title: METADATA_ADDRESS_LOCAL |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5928f6092adc62dc8f0eb075f20367c056fc50c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547165"
---
# <a name="metadata_address_local"></a>METADATA_ADDRESS_LOCAL
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此結構代表範圍內的區域變數位址， (通常是) 的函式或方法。  
  
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
 區域變數所屬方法或函數的識別碼。  
  
 [C + +] `_mdToken` 是 `typedef` 32 位的 `int` 。  
  
 pLocal  
 此結構所代表之位址的標記。  
  
 dwIndex  
 可以是方法或函式中這個區域變數的索引，也可以是 (語言特定) 的其他值。  
  
## <a name="remarks"></a>備註  
 當結構的[DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` 欄位 `DEBUG_ADDRESS_UNION` 設定為 `ADDRESS_KIND_LOCAL` ([ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)列舉) 中的值時，此結構就是 DEBUG_ADDRESS_UNION 結構中聯集的一部分。  
  
 `Warning:` [僅限 c + +] 如果不 `pLocal` 是 null，則您必須在 `Release` token 指標上呼叫， (`addr` 是 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 結構) 中的欄位：  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>需求  
 標頭： sh. h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
