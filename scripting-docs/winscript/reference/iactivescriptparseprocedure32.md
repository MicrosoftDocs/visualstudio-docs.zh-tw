---
title: IActiveScriptParseProcedure32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 10cdff328216d06a3326dd3595ef8fc78bc9cfc9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348109"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
如果 Windows 指令碼引擎可讓您可以加入至指令碼的程序的來源的程式碼文字，它會實作`IActiveScriptParseProcedure32`介面。 解譯的指令碼語言具有無獨立的撰寫環境，例如 VBScript，這會提供替代機制 (而非`IActiveScriptParse32`或`IPersist`*) 加入命名空間中的指令碼程序。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|||  
|-|-|  
|方法|描述|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|剖析指定的程式碼程序，並將程式新增至命名空間。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼介面](../../winscript/reference/active-script-interfaces.md)