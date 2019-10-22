---
title: CA1901： P-Invoke 宣告應該是可移植的 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d1b4c0c5bcf22db6558f156fd1acd0be94026b08
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661068"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901：P/Invoke 宣告應該是可移植的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Category|Microsoft 可攜性|
|中斷變更|中斷-如果 P/Invoke 在元件外部是可見的。 不中斷-如果在元件外部看不到 P/Invoke。|

## <a name="cause"></a>原因
 此規則會評估 P/Invoke 的每個參數和傳回值的大小，並在32位和64位平臺上封送處理至未受管理的程式碼時，驗證其大小是否正確。 此規則最常見的違規是傳遞固定大小的整數，其中需要平臺相依的指標大小變數。

## <a name="rule-description"></a>規則描述
 下列其中一種情況違反此規則：

- 當傳回值或參數應該輸入為 `IntPtr` 時，會輸入為固定大小的整數。

- 當傳回值或參數的類型為固定大小的整數時，會將其輸入為 `IntPtr`。

## <a name="how-to-fix-violations"></a>如何修正違規
 您可以使用 `IntPtr` 或 `UIntPtr` 來表示控制碼，而不是 `Int32` 或 `UInt32` 來修正此違規。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您不應該隱藏這個警告。

## <a name="example"></a>範例
 下列範例示範此規則的違規。

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

 在此範例中，`nIconIndex` 參數會宣告為 `IntPtr`，在32位平臺上為4個位元組寬，64位平臺上為8個位元組寬。 在接下來的非受控宣告中，您可以看到 `nIconIndex` 在所有平臺上都是4位元組不帶正負號的整數。

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>範例
 若要修正違規，請將宣告變更為下列內容：

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>請參閱
 [可攜性警告](../code-quality/portability-warnings.md)
