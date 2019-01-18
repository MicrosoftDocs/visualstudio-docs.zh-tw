---
title: IActiveScriptParseProcedureOld 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa7ea909680afdb65004f47e458d735e82ead929
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349984"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld 介面
可讓來源的程式碼文字，可以加入至指令碼的程序。 解譯的指令碼語言沒有獨立撰寫環境，例如 VBScript，這會提供替代機制 (而非`IActiveScriptParse`或`IPersist*`) 將命名空間中的指令碼程序。  
  
> [!NOTE]
>  此介面已被取代的益處`IActiveScriptParseProcedure`介面。  
  
## <a name="methods"></a>方法  
 除了繼承自方法`IUnknown`，則`IActiveScriptParseProcedureOld`介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|剖析指定的程式碼程序，並將命名空間中的程序。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)