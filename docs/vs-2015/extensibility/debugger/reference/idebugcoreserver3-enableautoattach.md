---
title: IDebugCoreServer3::EnableAutoAttach |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4b5c420a03fd69d767331f356eb4353d52630376
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490608"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugCoreServer3::EnableAutoAttach](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcoreserver3-enableautoattach)。  
  
可讓自動附加指定的偵錯引擎。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>參數  
 `rgguidSpecificEngines`  
 [in]每個偵錯引擎將標示為自動附加 Guid 的陣列。  
  
 `celtSpecificEngines`  
 [in]中指定的引擎數`rgguidSpecificEngines`。  
  
 `pszStartPageUrl`  
 [in]若要使用自動附加時起始的 URL。  
  
 `pbstrSessionID`  
 [out]已自動附加的工作階段識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。 一個錯誤碼是`E_AUTO_ATTACH_NOT_REGISTERED`，這表示尚未註冊 auto-attach class factory。  
  
## <a name="remarks"></a>備註  
 使用指定的 URL 相關聯的程式啟動時，將指定的偵錯引擎會自動啟動和附加。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)

