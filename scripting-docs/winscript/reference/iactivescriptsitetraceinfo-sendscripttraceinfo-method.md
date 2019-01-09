---
title: 'Iactivescriptsitetraceinfo:: Sendscripttraceinfo 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0419e4c5-eb7c-45a3-b6dc-1a5e157d95f9
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f08a5cb0e7bd297dede85190ac694185e2fd795
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091620"
---
# <a name="iactivescriptsitetraceinfosendscripttraceinfo-method"></a>IActiveScriptSiteTraceInfo::SendScriptTraceInfo 方法
會傳送包含事件類型、 內容和指令碼陳述式的追蹤資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SendScriptTraceInfo(     [in] SCRIPTTRACEINFO stiEventType,     [in] GUID guidContextID,     [in] DWORD dwScriptContextCookie,     [in] LONG lScriptStatementStart,     [in] LONG lScriptStatementEnd,     [in] DWORD64 dwReserved );   
```  
  
#### <a name="parameters"></a>參數  
 `stiEventType`  
 事件類型。  
  
 `guidContextId`  
 內容的 GUID。  
  
 `dwScriptContextCookie`  
 內容的 cookie。  
  
 `lScriptStatementStart`  
 指令碼陳述式開始的位置。  
  
 `lScriptStatementEnd`  
 指令碼陳述式結尾的位置。  
  
 `dwReserved`  
 保留的。