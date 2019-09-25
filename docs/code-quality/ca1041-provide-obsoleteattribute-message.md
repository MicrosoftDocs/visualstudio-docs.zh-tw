---
title: CA1041:必須提供 ObsoleteAttribute 訊息
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6620ac646c7fe20de856185708effc9e1a331e57
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235858"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041:必須提供 ObsoleteAttribute 訊息

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|分類|Microsoft.Design|
|重大變更|不中斷|

## <a name="cause"></a>原因

類型或成員是使用<xref:System.ObsoleteAttribute?displayProperty=fullName>未指定其<xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName>屬性的屬性來標記。

根據預設，此規則只會查看外部可見的類型和成員，但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

<xref:System.ObsoleteAttribute>用來標示已取代的程式庫類型和成員。 程式庫取用者應避免使用標示為已淘汰的任何類型或成員。 這是因為它可能不受支援，而且最終會從程式庫的較新版本中移除。 當編譯使用<xref:System.ObsoleteAttribute>標記的類型或成員時<xref:System.ObsoleteAttribute.Message%2A> ，會顯示內容（attribute）的屬性（property）。 以便提供使用者有關過時類型或成員的資訊。 這項資訊通常包含程式庫設計工具支援過時類型或成員的時間長度，以及使用的慣用取代。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請`message`將參數新增<xref:System.ObsoleteAttribute>至此函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則中的警告，因為<xref:System.ObsoleteAttribute.Message%2A>屬性會提供有關過時類型或成員的重要資訊。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則（而不是使用舊版分析），您可以根據其存取範圍，設定程式碼基底中的哪些部分來執行此規則。 例如，若要指定規則只針對非公用 API 介面執行，請將下列機碼值組新增至專案中的 editorconfig 檔案：

```ini
dotnet_code_quality.ca1041.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則（設計）設定此選項。 如需詳細資訊，請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例顯示已正確<xref:System.ObsoleteAttribute>宣告的過時成員。

[!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
[!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
[!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>另請參閱

- <xref:System.ObsoleteAttribute?displayProperty=fullName>