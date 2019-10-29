---
title: IWebAppDiagnosticsSetup 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup Interface
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e9bb3905da6227b978bc27b96493500f8d6d2ff
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984546"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup 介面
這個介面是由 PDM debug 應用程式所執行，可在正在進行調試的進程中建立 COM 物件，並啟用 web 診斷。 如果 PDM debug 應用程式物件會執行[IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite)，Internet Explorer 會在其建立後呼叫[SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) ，並傳入[IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127(v=vs.85))的參考。 WWA 應用程式會呼叫[SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) ，並改為傳入 WWA 介面 IWebApplicationHost。 如果已使用非 Null 值呼叫[SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) ， [IWebAppDiagnosticsSetup：:D iagnosticssupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)會傳回 true。 如果不是，則會傳回 false，而對[IWebAppDiagnosticsSetup：： CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)的呼叫會失敗。  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsSetup` 是由 PDM 11.0 和更新版本所執行。 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 此介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|取得指定的篩選所隱藏的文字檔。|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|判斷指定的檔是否屬於此節點的其中一個子節點。|