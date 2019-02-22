---
title: IDebugProgram2::WriteDump | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4fc77748e456a612130de4b8f814ea7ba491f22
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021841"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
寫入檔案中的傾印。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```csharp  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### <a name="parameters"></a>參數  
 `DumpType`  
 [in]值，以從[DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md)列舉，指定的傾印，型別，比方說，short 或 long。  
  
 `pszDumpUrl`  
 [in]要寫入傾印的 URL。 一般而言，這是採用`file://c:\path\filename.ext`，但可能是任何有效的 URL。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 目前的堆疊框架、 本身的堆疊、 執行緒執行程式，並可能是由程式所擁有的任何記憶體中的清單，通常會包含程式的傾印。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)