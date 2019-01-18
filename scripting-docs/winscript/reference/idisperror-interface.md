---
title: IDispError 介面 |Microsoft Docs
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
ms.openlocfilehash: b717ebfe740a9b356513bb0f15e90c629a14e147
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345834"
---
# <a name="idisperror-interface"></a>IDispError 介面
提供詳細內容錯誤訊息。  
  
> [!NOTE]
>  未實作此介面。  
  
 除了繼承自方法`IUnknown`，則`IDispError`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|擷取特定類型的資訊時發生錯誤。|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|擷取下一個`IDispError`物件。|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|擷取的錯誤程式碼`IDispError`物件。|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|傳回語言的程式設計識別項的類別或引發錯誤的應用程式。|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|傳回說明檔路徑，以及說明錯誤，可能的話，本主題的內容識別碼。|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|傳回此錯誤的文字描述。|