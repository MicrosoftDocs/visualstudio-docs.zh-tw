---
title: IDebugProgram2::WriteDump |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b17d75ace19ac53cbcd229d7c15de573c1ecb8b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
寫入傾印至檔案。  
  
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
 [in]中的值[DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md)列舉，指定的傾印，型別，例如、 short 或 long。  
  
 `pszDumpUrl`  
 [in]要寫入傾印的 URL。 一般而言，這種形式的`file://c:\path\filename.ext`，但可能是任何有效的 URL。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 目前的堆疊框架，本身的堆疊、 執行中的程式，可能是由程式擁有的任何記憶體的執行緒清單，通常會包含程式傾印。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)