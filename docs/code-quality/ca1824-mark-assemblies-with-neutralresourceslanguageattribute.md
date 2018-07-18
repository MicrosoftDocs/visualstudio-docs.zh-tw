---
title: CA1824：以 NeutralResourcesLanguageAttribute 標記組件
ms.date: 03/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: beaef23dd5b3047d1d65b90fdd984dfdedd7e145
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916383"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824：以 NeutralResourcesLanguageAttribute 標記組件

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|分類|Microsoft.Performance|
|中斷變更|非中斷|

## <a name="cause"></a>原因

組件包含**ResX**-基礎資源，但沒有<xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName>套用到它。

## <a name="rule-description"></a>規則描述

<xref:System.Resources.NeutralResourcesLanguageAttribute>屬性會通知應用程式的預設文化特性的資源管理員。 如果預設文化特性的資源會內嵌在應用程式的主要組件和<xref:System.Resources.ResourceManager>必須擷取屬於文化特性的預設文化特性中，與相同資源<xref:System.Resources.ResourceManager>會自動使用位於主要組件中的資源而不是搜尋的附屬組件。 這會略過一般組件探查，可改善查詢效能，您載入，而且可以減少您的工作集的第一個資源。

> [!TIP]
> 請參閱[封裝和部署資源](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps)處理程序，<xref:System.Resources.ResourceManager>用來探查資源檔。

## <a name="fix-violations"></a>修正違規

若要修正此規則的違規情形，將屬性加入至組件，並指定語言的中性文化特性的資源。

### <a name="to-specify-the-neutral-language-for-resources"></a>若要指定資源的中性語言

1. 在**方案總管 中**，以滑鼠右鍵按一下您的專案，然後選取**屬性**。

2. 選取**應用程式**索引標籤，然後選取**組件資訊**。

   > [!NOTE]
   > 如果您的專案的.NET 標準或.NET Core 專案，請選取**封裝** 索引標籤。

3. 選取的語言，從**中性語言**或**組件的中性語言**下拉式清單。

4. 選取 [確定]。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它是可以隱藏此規則的警告。 不過，可能會降低啟動效能。

## <a name="see-also"></a>另請參閱

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [桌面應用程式 (.NET) 中的資源](/dotnet/framework/resources/)
- [CA1703-資源字串應該拼寫正確](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701-資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)