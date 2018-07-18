---
title: 'Iactivescriptsitetraceinfo:: Sendscripttraceinfo 方法 |Microsoft 文件'
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
ms.openlocfilehash: 5290cc6a92be7c8bc99e4715c77bfe6f8f6abb53
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724838"
---
# <a name="iactivescriptsitetraceinfosendscripttraceinfo-method"></a>IActiveScriptSiteTraceInfo::SendScriptTraceInfo 方法
會傳送追蹤資訊，包括事件類型、 內容和指令碼陳述式。  
  
## <a name="syntax"></a>語法  
  
```  
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