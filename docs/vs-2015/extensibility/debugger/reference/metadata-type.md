---
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1be7cb6071a0307a56285b8929e52e038c263fdc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942621"
---
# <a name="metadatatype"></a>METADATA_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此結構會指定取自中繼資料的欄位類型的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
  
 `tokClass`值是唯一識別類型的中繼資料語彙基元。 如需有關如何解譯較高的位元的中繼資料語彙基元 ID 的詳細資訊，請參閱 < `CorTokenType` corhdr.h 檔案中的列舉型別[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]SDK。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
