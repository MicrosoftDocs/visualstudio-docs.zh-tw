---
title: CA5350：請勿使用弱式密碼編譯演算法 |Microsoft Docs
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9c2c996c383c8834e44e16f382c14b695c83f26
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668989"
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: 請勿使用弱式密碼編譯演算法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseWeakCryptographicAlgorithms|
|CheckId|CA5350|
|Category|Microsoft.Cryptography|
|中斷變更|非中斷|

> [!NOTE]
> 上次於 2015 年 11 月更新此警告。

## <a name="cause"></a>原因
 例如 <xref:System.Security.Cryptography.TripleDES> 的加密演算法，和例如 <xref:System.Security.Cryptography.SHA1> 及 <xref:System.Security.Cryptography.RIPEMD160> 的雜湊演算法，被視為弱式。

 這些密碼編譯演算法提供的安全性保證不像更新的同類型演算法那麼多。 密碼編譯雜湊演算法 <xref:System.Security.Cryptography.SHA1> 和 <xref:System.Security.Cryptography.RIPEMD160> 提供的衝突防禦比更新的雜湊演算法少。 加密演算法 <xref:System.Security.Cryptography.TripleDES> 提供比更新的加密演算法較少的安全性位元。

## <a name="rule-description"></a>規則描述
 現今，弱式加密演算法和雜湊函式用於多種原因，但它們不應該用來保證所保護資料的機密性。

 此規則會在它在程式碼中發現 3DES、SHA1 或 RIPEMD160 演算法時觸發，並擲回警告給使用者。

## <a name="how-to-fix-violations"></a>如何修正違規
 使用密碼編譯較強的選項：

- 若為 TripleDES 加密，請使用 <xref:System.Security.Cryptography.Aes> 加密。

- 若為 SHA1 或 RIPEMD160 雜湊函式，請使用 [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) 系列 (例如 <xref:System.Security.Cryptography.SHA512>、 <xref:System.Security.Cryptography.SHA384>、 <xref:System.Security.Cryptography.SHA256>)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當資料所需的保護層級不需要安全性保證時，隱藏此規則的警告。

## <a name="pseudo-code-example"></a>虛擬程式碼範例
 在本文撰寫之時，下列虛擬程式碼範例說明這個規則偵測到的模式。

### <a name="sha-1-hashing-violation"></a>SHA-1 雜湊違規

```
using System.Security.Cryptography;
...
var hashAlg = SHA1.Create();

```

### <a name="solution"></a>方案

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="ripemd160-br-br-hashing-violation"></a>RIPEMD160 <br /><br />雜湊違規

```
using System.Security.Cryptography;
...
var hashAlg = RIPEMD160Managed.Create();

```

### <a name="solution"></a>方案

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="tripledes-encryption-violation"></a>TripleDES 加密違規

```
using System.Security.Cryptography;
...
using (TripleDES encAlg = TripleDES.Create())
{
  ...
}
```

### <a name="solution"></a>方案

```
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```