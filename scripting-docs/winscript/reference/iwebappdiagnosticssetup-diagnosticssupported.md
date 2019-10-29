---
title: IWebAppDiagnosticsSetup：:D iagnosticsSupported |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd27e7c8759054fa2d7d67858d8d006fa9c9a152
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984576"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
判斷此應用程式是否支援診斷。 如果在使用非 Null 值來執行此介面的物件上呼叫了[SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) ， [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)會傳回 `true`。 如果不是，則會傳回 `false`，而對[IWebAppDiagnosticsSetup：： CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)的呼叫會失敗。  
  
> [!IMPORTANT]
> [IWebAppDiagnosticsSetup 介面](../../winscript/reference/iwebappdiagnosticssetup-interface.md)是由 PDM 11.0 和更新版本所執行。 在 activdbg100 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 如果在使用非 Null 值來執行此介面的物件上呼叫了[SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) ， [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)會傳回 `true`。 如果不是，則會傳回 `false`，而對[IWebAppDiagnosticsSetup：： CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)的呼叫會失敗。