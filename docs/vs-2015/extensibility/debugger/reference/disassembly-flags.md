---
title: DISASSEMBLY_FLAGS |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d48fcf9dd941194b56e2c794ad7f5673f8e58421
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159309"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定反組解碼的旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>成員  
 DF_DOCUMENTCHANGE  
 指出這個指令與上一個指令位於不同的檔中。  
  
 DF_DISABLED  
 表示不會執行此指令。  
  
 DF_INSTRUCTION_ACTIVE  
 指出此指令是要執行的下一個指示 (可能有一個以上的) 。  
  
 DF_DATA  
 指出此指示實際上是 (不是程式碼) 的資料。  
  
 DF_HASSOURCE  
 指出此指令具有來源。 某些指示（例如程式碼剖析或垃圾收集程式碼）沒有對應的來源。  
  
 DF_DOCUMENT_CHECKSUM  
 表示 `bstrDocumentUrl` 欄位包含檔 URL 之後的總和檢查碼資料。 請參閱「備註」一節，以瞭解如何儲存總和檢查碼資料的 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 結構。  
  
## <a name="remarks"></a>備註  
 當做 `dwFlags` [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 結構的成員使用。  
  
 這些旗標可以與位結合 `OR` 。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [枚舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
