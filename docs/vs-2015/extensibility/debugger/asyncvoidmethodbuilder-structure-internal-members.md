---
title: AsyncVoidMethodBuilder 結構-內部成員 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 770e66c4136379a24cee349b04fcc06f5278a379
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945462"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>AsyncVoidMethodBuilder 結構 - 內部成員
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題描述的內部成員<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>類別。 如需此類別的一般資訊，請參閱<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>參考主題。  
  
 **命名空間︰** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll 中)  
  
 因為您無法從.NET Framework 來存取這些內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>內部成員  
  
|名稱|描述|  
|----------|-----------------|  
|[ObjectIdForDebugger 屬性](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|取得物件，可用來唯一識別這個產生器偵錯工具。|  
|[m_objectIdForDebugger 欄位](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|表示偵錯工具用來唯一識別這個產生器的延遲初始化的物件。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [.NET Framework 適用的平行擴充內部資訊](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
