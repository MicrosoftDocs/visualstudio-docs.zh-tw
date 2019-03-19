---
title: IDebugSessionProviderEx 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9bf341adeaeb17c8986b1b30b12f58113aef562
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146769"
---
# <a name="idebugsessionproviderex-interface"></a>IDebugSessionProviderEx 介面
提供偵錯工具 IDE，以啟用主控件和語言初始化偵錯的主要介面。 它會建立執行中應用程式的偵錯工作階段。 機器偵錯管理員會實作這個介面。  
  
 除了繼承自方法`IUnknown`，則`IDebugSessionProviderEx`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|判斷是否可用於指定的應用程式進行偵錯的 Just In Time。|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|初始化具有指定的應用程式的偵錯工作階段。|