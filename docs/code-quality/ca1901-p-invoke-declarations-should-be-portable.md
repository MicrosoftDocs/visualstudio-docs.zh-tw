---
title: CA1901:P-Invoke 宣告應該為可移植的
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e74c798cc273fe331118139df99ec890cdcd3086
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001666"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901:P/Invoke 宣告應該為可移植的

|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|分類|Microsoft.Portability|
|中斷變更|中斷-如果 P/Invoke 是組件外部可見。 非中斷-如果 P/Invoke 不是組件外部可見。|

## <a name="cause"></a>原因
 此規則會評估每個參數的大小和 P/Invoke 的傳回值，並確認其大小，封送處理至 unmanaged 程式碼在 32 位元和 64 位元平台上時正確無誤。 此規則的最常見的違規是傳遞其中一個平台相依，指標大小的變數是必要的固定大小的整數。

## <a name="rule-description"></a>規則描述
 下列案例其中一種方法違反此規則就會發生：

- 傳回值或參數的型別為固定大小的整數時應該鍵入為`IntPtr`。

- 傳回值或參數的型別為`IntPtr`時它應該鍵入為固定大小的整數。

## <a name="how-to-fix-violations"></a>如何修正違規
 您可以使用，以修正此違規`IntPtr`或是`UIntPtr`來表示控制代碼，而不是`Int32`或`UInt32`。

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

 在此範例中，`nIconIndex`參數宣告為`IntPtr`，這是 4 個位元組寬的 32 位元平台和 8 個位元組寬的 64 位元平台上。 在 unmanaged 宣告接下來，您可以看到`nIconIndex`是 4 位元組不帶正負號的整數，在所有平台上。

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>範例
 若要修正此違規情形，請將宣告變更如下：

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>另請參閱
 [Portability Warnings](../code-quality/portability-warnings.md)