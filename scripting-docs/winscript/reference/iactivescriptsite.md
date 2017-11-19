---
title: "IActiveScriptSite |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c23dba403a7889fe46817a21ed8e4be65b1c05b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
藉由建立 Windows 指令碼引擎的站台主機。 通常，此站台將會顯示指令碼 （例如，ActiveX 控制項） 的所有物件的容器相關聯。 一般而言，此容器會對應至文件或檢視的頁面。 例如，Microsoft Internet Explorer 中，會建立這類容器，每個要顯示之 HTML 頁面。 每個 ActiveX 控制項 （或其他自動化物件） 頁面上，以及指令碼引擎本身，則會是此容器中的可列舉。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|||  
|-|-|  
|方法|說明|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|擷取主機會顯示使用者介面項目使用的地區設定識別碼。|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|取得已加入到引擎透過呼叫項目資訊[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)方法。|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|擷取主應用程式定義的字串可唯一識別目前的文件版本，從主應用程式的觀點來看。|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|指令碼完成執行時呼叫。|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|通知主機指令碼引擎已變更狀態。|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|通知主機在引擎執行指令碼時發生執行錯誤。|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|通知主機指令碼引擎已開始執行指令碼的程式碼。|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|通知主機指令碼引擎已執行的指令碼傳回。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼介面](../../winscript/reference/active-script-interfaces.md)