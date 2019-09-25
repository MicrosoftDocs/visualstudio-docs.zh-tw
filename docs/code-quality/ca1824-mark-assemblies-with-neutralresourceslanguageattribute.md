---
title: CA1824:組件必須標記 NeutralResourcesLanguageAttribute
ms.date: 03/29/2018
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df5c0db4e9e141e5833893bbbb447328eab8851e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233350"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824:組件必須標記 NeutralResourcesLanguageAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|分類|Microsoft.Performance|
|重大變更|不中斷|

## <a name="cause"></a>原因

元件包含以**ResX**為基礎的資源，但未<xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName>套用至它。

## <a name="rule-description"></a>規則描述

<xref:System.Resources.NeutralResourcesLanguageAttribute>屬性會通知資源管理員應用程式的預設文化特性。 如果預設文化特性的資源內嵌在應用程式的主要元件中，而且<xref:System.Resources.ResourceManager>必須取出屬於與預設文化特性相同文化特性的資源，則<xref:System.Resources.ResourceManager>會自動使用位於主要元件中的資源而不是搜尋附屬元件。 這會略過一般的元件探查、改善您載入的第一個資源的查閱效能，並可減少您的工作集。

> [!TIP]
> 如需使用探查資源檔的進程， <xref:System.Resources.ResourceManager>請參閱[封裝和部署資源](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps)。

## <a name="fix-violations"></a>修正違規

若要修正此規則的違規，請將屬性新增至元件，並指定中性文化特性之資源的語言。

### <a name="to-specify-the-neutral-language-for-resources"></a>若要指定資源的中性語言

1. 在**方案總管**中，以滑鼠右鍵按一下您的專案，然後選取 [**屬性**]。

2. 選取 [**應用程式**] 索引標籤，然後選取 [**元件資訊**]。

   > [!NOTE]
   > 如果您的專案是 .NET Standard 或 .NET Core 專案，請選取 [**封裝**] 索引標籤。

3. 從 [**中性語言**] 或 [**元件中性語言**] 下拉式清單中選取語言。

4. 選取 [確定]。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

允許隱藏此規則的警告。 不過，啟動效能可能會降低。

## <a name="see-also"></a>另請參閱

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [桌面應用程式中的資源（.NET）](/dotnet/framework/resources/)
- [CA1703-資源字串應該拼寫正確](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701-資源字串複合字應該是正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)