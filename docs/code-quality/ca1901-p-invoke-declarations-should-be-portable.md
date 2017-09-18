---
title: "CA1901：P/Invoke 宣告應該是可移植的 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
helpviewer_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# CA1901：P/Invoke 宣告應該是可移植的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|PInvokeDeclarationsShouldBePortable|  
|CheckId|CA1901|  
|分類|Microsoft.Portability|  
|中斷變更|中斷 \- 如果可以在組件外部看見 P\/Invoke。  非中斷 \- 如果不能在組件外部看見 P\/Invoke。|  
  
## 原因  
 這項規則會評估每個參數的大小和 P\/Invoke 的傳回值，並且在 32 位元和 64 位元平台上封送處理至 Unmanaged 程式碼時驗證其大小是否正確。  這項規則最常見的違規情形，就是在需要與平台相關之指標大小變數的地方傳遞固定大小的整數。  
  
## 規則描述  
 下列任一案例違反此規則，就會發生：  
  
-   傳回值或參數的型別應該是 `IntPtr`，但其型別卻是固定大小的整數。  
  
-   傳回值或參數的型別應該固定大小的整數，但其型別卻是 `IntPtr`。  
  
## 如何修正違規  
 您可以使用 `IntPtr` 或 `UIntPtr` 表示控制代碼 \(而不是 `Int32` 或 `UInt32`\)，藉以修正此違規情形。  
  
## 隱藏警告的時機  
 您不應該隱藏這項警告。  
  
## 範例  
 下列範例示範這項規則的違規情形。  
  
```c#  
internal class NativeMethods  
{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]  
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, IntPtr nIconIndex);  
}  
```  
  
 在此範例中， `nIconIndex` 參數被宣告為 `IntPtr`，在 32 位元平台上是 4 個位元組寬，在 64 位元平台上是 8 個位元組寬。  在接下來的未管理的宣告中，可以看到 `nIconIndex` 適用於所有平台的 4 位元組不帶正負號的整數。  
  
```c#  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## 範例  
 若要修正此違規情形，請將宣告變更如下：  
  
```c#  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## 請參閱  
 [可攜性警告](../code-quality/portability-warnings.md)