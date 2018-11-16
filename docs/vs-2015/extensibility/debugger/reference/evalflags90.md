---
title: EVALFLAGS90 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 943609ed841029017d77082cc44bde3abc083561
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723590"
---
# <a name="evalflags90"></a>EVALFLAGS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

列舉有效的控制運算式評估的旗標值。 這個列舉型別會擴充[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)列舉型別。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
typedef DWORD EVALFLAGS90;  
```  
  
```csharp  
public enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
```  
  
#### <a name="parameters"></a>參數  
 EVAL90_RETURNVALUE  
 指定的評估傳回的值，如果有的話。  
  
 EVAL90_NOSIDEEFFECTS  
 指定不允許副作用。  
  
 EVAL90_ALLOWBPS  
 指定中斷點停止。  
  
 EVAL90_ALLOWERRORREPORT  
 指定允許主應用程式報告該錯誤。 主要用於在 Internet Explorer 中的指令碼中的運算式評估。  
  
 EVAL90_FUNCTION_AS_ADDRESS  
 要評估做為位址，而不是叫用函式的強制函式。  
  
 EVAL90_NOFUNCEVAL  
 函式可防止進行評估。 例如，請考慮`int`運算式中的語彙基元`myExpression(int) + 10`。 為位址，但不是能作為值，就可以正確評估此函式。  
  
 EVAL90_NOEVENTS  
 旗標，指出工作階段的偵錯管理員 (SDM) 或 ide，不應該傳送之運算式評估期間發生的事件。  
  
 EVAL90_DESIGN_TIME_EXPR_EVAL  
 可讓設計階段運算式評估。  
  
 EVAL90_ALLOW_IMPLICIT_VARS  
 允許隱含變數的建立。  
  
 EVAL90_FORCE_EVALUATION_NOW  
 若要立即發生強制評估。 服務要求，例如使用者要求時，這非常有用。  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg90.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

