---
title: IProcessDebugManager Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProcessDebugManager interface
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d68c044cdc3d523841cc56814b8ca34bcd8aa037
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944794"
---
# <a name="iprocessdebugmanager-interface"></a>IProcessDebugManager 介面
處理序偵錯管理員的主要介面。 此介面可以建立、新增或移除處理序中的虛擬應用程式。 它可以列舉堆疊框架和應用程式執行緒。  
  
 除了繼承自方法`IUnknown`，則`IProcessDebugManager`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|建立新的偵錯應用程式物件為此應用程式。|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|傳回目前的處理序的預設應用程式物件。|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|新增機器偵錯管理員的清單執行應用程式的應用程式。|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|移除應用程式從執行的應用程式清單。|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|建立新的偵錯文件協助程式，此應用程式。|