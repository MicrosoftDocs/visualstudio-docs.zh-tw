---
title: METADATA_TYPE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d8596704408c1266d98d24f221ac7642150c79af
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852871"
---
# <a name="metadatatype"></a>METADATA_TYPE
此結構會指定取自中繼資料的欄位類型的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```csharp  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### <a name="parameters"></a>參數  
 ulAppDomainID  
 符號所來自的應用程式的識別碼。 這用來唯一識別應用程式的執行個體。  
  
 guidModule  
 模組包含此欄位的 GUID。  
  
 tokClass  
 此類型的中繼資料語彙基元的識別碼。  
  
 [C + +]`_mdToken`已`typedef`適用於 32 位元`int`。  
  
## <a name="remarks"></a>備註  
 此結構會顯示為中的等位的一部分[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)結構時`dwKind`欄位`TYPE_INFO`結構設定為`TYPE_KIND_METADATA`(值[dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)列舉型別）。  
  
 `tokClass`值是唯一識別類型的中繼資料語彙基元。 如需有關如何解譯較高的位元的中繼資料語彙基元 ID 的詳細資訊，請參閱 < `CorTokenType` corhdr.h 檔案中的列舉型別[!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)]SDK。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)