---
title: IDispError 介面 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f139d317db5aa00f03f8e9abd71020e5ff35b03
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728108"
---
# <a name="idisperror-interface"></a>IDispError 介面
提供內容的詳細的錯誤訊息。  
  
> [!NOTE]
>  未實作這個介面。  
  
 除了繼承自`IUnknown`、`IDispError`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|擷取特定類型的資訊時發生錯誤。|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|擷取下一個`IDispError`物件。|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|擷取中的錯誤碼`IDispError`物件。|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|傳回對類別或引發錯誤的應用程式的語言相依程式設計識別項。|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|傳回說明檔的路徑和盡可能說明此錯誤，該主題的內容識別碼。|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|傳回錯誤的文字描述。|