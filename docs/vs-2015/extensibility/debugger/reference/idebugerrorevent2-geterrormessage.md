---
title: IDebugErrorEvent2::GetErrorMessage |Microsoft Docs
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
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7fb5e3f2f048221b127286eecc0494ed5c648006
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49179006"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

傳回可讓人類看得懂的錯誤訊息建構的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pMessageType`  
 [out]傳回值，以從[MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)描述的訊息類型的列舉。  
  
 `pbstrErrorFormat`  
 [out]使用者的最後一個訊息的格式 （如需詳細資訊，請參閱 < 備註 >）。  
  
 `hrErrorReason`  
 [out]錯誤碼訊息是關於。  
  
 `pdwType`  
 [out]錯誤的嚴重性 (使用如 MB_XXX 常數`MessageBox`; 例如，`MB_EXCLAMATION`或`MB_WARNING`)。  
  
 `pbstrHelpFileName`  
 [out]說明檔 （設為 null 值，如果沒有說明檔） 的路徑。  
  
 `pdwHelpId`  
 [out][說明] 主題的顯示 （設為 0，如果沒有任何 [說明] 主題） 的識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 格式化錯誤訊息應該像`"What I was doing.  %1"`。 `"%1"`就會取代呼叫端所衍生自錯誤碼的錯誤訊息 (這會傳入`hrErrorReason`)。 `pMessageType`參數會告訴呼叫端應該顯示的最後一個錯誤訊息的方式。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)

