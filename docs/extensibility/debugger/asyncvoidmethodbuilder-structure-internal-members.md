---
title: "AsyncVoidMethodBuilder 結構-內部成員 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e2a8b9f7e287ccf8bc63a8d7392cba0d58cb9bb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>AsyncVoidMethodBuilder 結構-內部成員
本主題描述的內部成員<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>類別。 如需此類別的一般資訊，請參閱<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>參考主題。  
  
 **命名空間：**<xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll)  
  
 因為您無法從.NET Framework 來存取這些內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>內部成員  
  
|名稱|說明|  
|----------|-----------------|  
|[ObjectIdForDebugger 屬性](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|取得可用來唯一識別此產生器偵錯工具的物件。|  
|[m_objectIdForDebugger 欄位](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|表示偵錯工具用來唯一識別此產生器的延遲初始化的物件。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [.NET Framework 適用的平行擴充內部資訊](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)