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
ms.openlocfilehash: 40cb2a3674884a9fb4f1449c9afa2e0a2d27050f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808556"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824:組件必須標記 NeutralResourcesLanguageAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|分類|Microsoft.Performance|
|中斷變更|非重大|

## <a name="cause"></a>原因

組件包含**ResX**-基礎資源，但並沒有<xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName>套用到它。

## <a name="rule-description"></a>規則描述

<xref:System.Resources.NeutralResourcesLanguageAttribute>屬性會通知應用程式的預設文化特性的資源管理員。 如果預設文化特性的資源內嵌在應用程式的主要組件，並<xref:System.Resources.ResourceManager>來擷取屬於相同的文化特性，與預設文化特性的資源具有<xref:System.Resources.ResourceManager>會自動使用位於主要組件中的資源而不是搜尋的附屬組件。 這會略過一般組件探查，可改善查詢效能，您載入，並可減少您的工作集的第一個資源。

> [!TIP]
> 請參閱[封裝和部署資源](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps)處理程序，<xref:System.Resources.ResourceManager>用來探查資源檔。

## <a name="fix-violations"></a>修正違規

若要修正此規則的違規情形，將屬性新增至組件，並指定語言的中性文化特性的資源。

### <a name="to-specify-the-neutral-language-for-resources"></a>若要指定資源的中性語言

1. 在 **方案總管**，以滑鼠右鍵按一下您的專案，然後選取**屬性**。

2. 選取 **應用程式**索引標籤，然後按**組件資訊**。

   > [!NOTE]
   > 如果您的專案的.NET Standard 或.NET Core 專案，請選取**封裝** 索引標籤。

3. 選取的語言從**中性語言**或是**組件的中性語言**下拉式清單。

4. 選取 [確定]。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

就可以隱藏此規則的警告。 不過，可能會降低啟動效能。

## <a name="see-also"></a>另請參閱

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [桌面應用程式 (.NET) 中的資源](/dotnet/framework/resources/)
- [CA1703-資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701-資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)