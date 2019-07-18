---
title: IDebugSymbolProvider::GetNextAddress |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e1bf0798e0f49d9e7b2871c5601f966bc282b186
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "62421446"
---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得會遵循在方法中的指定偵錯位址的偵錯位址。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetNextAddress(   
   IDebugAddress*  pAddress,  
   BOOL            fStatementOnly,  
   IDebugAddress** ppAddress  
);  
```  
  
```csharp  
int GetNextAddress(   
   IDebugAddress     pAddress,  
   bool              fStatementOnly,  
   out IDebugAddress ppAddress  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pAddress`  
 [in]指定偵錯位址。  
  
 `fStatementOnly`  
 [in]如果為 TRUE，會限制單一陳述式的偵錯位址。  
  
 `ppAddress`  
 [out]傳回下一個偵錯位址。  
  
## <a name="return-value"></a>傳回值  
 會傳回有效`HRESULT`，通常是 S_OK。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
