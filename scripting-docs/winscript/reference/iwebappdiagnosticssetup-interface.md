---
title: IWebAppDiagnosticsSetup 介面 |Microsoft Docs
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
ms.openlocfilehash: fc29282ec9d00ff79131765d2bf294c54fa347c6
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344898"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup 介面
此介面是由 PDM 偵錯應用程式正在偵錯的處理序中建立 COM 物件，並在啟用 web 診斷實作的。 如果 PDM 偵錯應用程式物件會實作[IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438)，會呼叫 Internet Explorer [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)並在其上建立它之後的參考傳入[IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). WWA 應用程式會呼叫[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)和 WWA 傳入介面 IWebApplicationHost 改。 如果[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)已使用非 NULL 值，呼叫[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) ，則傳回 true。 如果沒有，它會傳回 false，並呼叫[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)失敗。  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup` 會實作由 PDM v11.0 和更新版本。 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 此介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|取得指定的篩選條件會隱藏文字文件。|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|判斷指定的文件是否屬於這個節點的子節點的其中一個。|