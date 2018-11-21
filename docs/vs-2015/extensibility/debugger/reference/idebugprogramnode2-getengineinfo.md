---
title: IDebugProgramNode2::GetEngineInfo |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7f4a885d1c2f119c6c0e978614502102adc5c4d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741513"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得名稱和執行程式的偵錯引擎 (DE) 的識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrEngine`  
 [out]傳回的執行程式的預設名稱 (c + + 特有： 這可以是 null 指標，指出呼叫端不想在引擎的名稱)。  
  
 `pguidEngine`  
 [out]傳回執行程式 DE 的全域唯一識別碼 (c + + 特有： 這可以是 null 指標，表示呼叫端不感興趣的引擎 GUID)。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

