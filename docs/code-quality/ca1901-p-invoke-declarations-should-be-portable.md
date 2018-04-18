---
title: 'CA1901: P Invoke 宣告應該是可攜式 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44c58860c09ab1ef0bb1f6cac15c380fe22dfc93
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901：P/Invoke 宣告應該是可移植的
|||  
|-|-|  
|TypeName|PInvokeDeclarationsShouldBePortable|  
|CheckId|CA1901|  
|分類|Microsoft.Portability|  
|中斷變更|中斷-如果是在組件外部可見的 P/Invoke。 非中斷-如果 P/Invoke 不是組件外部可見。|  
  
## <a name="cause"></a>原因  
 此規則會評估每個參數的大小和 P/Invoke 的傳回值，並確認封送處理至 unmanaged 程式碼，在 32 位元和 64 位元平台上時其大小正確。 最常見違反此規則是傳遞固定大小的整數，其中是必要的平台而定，指標大小的變數。  
  
## <a name="rule-description"></a>規則描述  
 下列案例中擇一違反此規則就會發生：  
  
-   傳回值或參數型別為固定大小的整數時應該類型為`IntPtr`。  
  
-   傳回值或參數類型為`IntPtr`當它輸入應該為固定大小的整數。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 您可以使用，以修正此違規`IntPtr`或`UIntPtr`來代表控制代碼，而不是`Int32`或`UInt32`。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 您不應該隱藏這個警告。  
  
## <a name="example"></a>範例  
 下列範例會示範這項規則的違規情形。  
  
```csharp  
internal class NativeMethods  
{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]  
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, IntPtr nIconIndex);  
}  
```  
  
 在此範例中，`nIconIndex`參數宣告為`IntPtr`，這是 4 個位元組的 32 位元平台和寬的 64 位元平台上為 8 個位元組寬。 在 unmanaged 後面宣告中，您可以看到`nIconIndex`是 4 位元組不帶正負號的整數，在所有平台上。  
  
```csharp  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## <a name="example"></a>範例  
 若要修正的違規情形，變更宣告所示：  
  
```csharp  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Portability Warnings](../code-quality/portability-warnings.md)