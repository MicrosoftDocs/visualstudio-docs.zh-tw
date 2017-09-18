---
title: "EVALFLAGS90 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "EVALFLAGS90 列舉型別"
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# EVALFLAGS90
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

列舉控制運算式評估的旗標的有效值。  這個列舉型別擴充[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)列舉型別。  
  
## 語法  
  
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
  
```c#  
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
  
#### 參數  
 EVAL90\_RETURNVALUE  
 指定傳回的值，如果有的話，進行評估。  
  
 EVAL90\_NOSIDEEFFECTS  
 指定不允許副作用。  
  
 EVAL90\_ALLOWBPS  
 指定中斷點停止。  
  
 EVAL90\_ALLOWERRORREPORT  
 指定允許主應用程式報告該錯誤。  主要用於在 Internet Explorer 中的指令碼中運算式的評估。  
  
 EVAL90\_FUNCTION\_AS\_ADDRESS  
 要評估的地址，而不是叫用函式的部隊函式。  
  
 EVAL90\_NOFUNCEVAL  
 函式會防止進行評估。  例如，假設`int`運算式中的語彙基元`myExpression(int) + 10`。  為地址，但不是以一個值，就可以正確地評估此函式。  
  
 EVAL90\_NOEVENTS  
 旗標，表示 \[工作階段偵錯管理員 \(SDM\) 或 IDE，您不應該傳送運算式的評估期間發生的事件。  
  
 EVAL90\_DESIGN\_TIME\_EXPR\_EVAL  
 可讓設計階段運算式評估。  
  
 EVAL90\_ALLOW\_IMPLICIT\_VARS  
 允許隱含變數的建立。  
  
 EVAL90\_FORCE\_EVALUATION\_NOW  
 若要立即強制評估。  在處理要求，如使用者要求時，這非常有用。  
  
## 需求  
 標頭: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)