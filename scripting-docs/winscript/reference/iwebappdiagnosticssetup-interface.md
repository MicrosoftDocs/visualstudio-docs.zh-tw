---
title: IWebAppDiagnosticsSetup 介面 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 6e273f29bee6e4d2aae26c01c477373a735624c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733998"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup 介面
實作這個介面是由 PDM 偵錯應用程式進行偵錯的處理序中建立 COM 物件，並啟用 web 診斷。 如果 PDM 偵錯應用程式物件實作[IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438)，Internet Explorer 呼叫[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)它之後已建立並傳入的參考上[IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). WWA 應用程式呼叫[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)和 WWA 傳入介面 IWebApplicationHost 改為。 如果[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)已使用非 NULL 值，呼叫[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)傳回 true。 如果您沒有，它會傳回 false，並呼叫[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)失敗。  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup`會實作由 PDM v11.0 和更新版本。 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 此介面會公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|取得所指定的篩選條件會隱藏文字文件。|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|判斷指定的文件是否屬於這個節點的子節點的其中一個。|