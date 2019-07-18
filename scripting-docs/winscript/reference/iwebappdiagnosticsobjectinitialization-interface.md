---
title: IWebAppDiagnosticsObjectInitialization 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsObjectInitialization Interface
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a992f8512d4927eeb58d6437ccb830abda688b28
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443693"
---
# <a name="iwebappdiagnosticsobjectinitialization-interface"></a>IWebAppDiagnosticsObjectInitialization 介面
此介面實作的類別上實作[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)。 [IWebAppDiagnosticsSetup 介面](../../winscript/reference/iwebappdiagnosticssetup-interface.md)藉由實作的物件[IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)。 在大部分情況下這個物件是 PDM。  
  
 在建立物件之後， [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)稱為 PDM 偵錯應用程式的參考並`hPassToObject`參數`CreateObjectWithSiteAtWebApp`。  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsObjectInitialization` 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 此介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|初始化物件。|