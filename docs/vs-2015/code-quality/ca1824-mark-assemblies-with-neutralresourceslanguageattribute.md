---
title: CA1824：使用 NeutralResourcesLanguageAttribute 標記元件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: efa328fdff9c357e0183fc2ca80e4d77d4f6782e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661109"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824：以 NeutralResourcesLanguageAttribute 標記組件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Category|Microsoft。效能|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 元件包含以**ResX**為基礎的資源，但未套用 <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述
 **NeutralResourcesLanguage**屬性會通知**ResourceManager** ，這是用來顯示元件中性文化特性之資源的語言。 當它查閱的資源與中性資來源語言相同時， **ResourceManager**會自動使用位於主要元件中的資源。 它會執行這項工作，而不是搜尋具有目前線程之目前使用者介面文化特性的附屬元件。 這可改善載入第一個資源的查詢效能，而且可以減少您的工作集。

## <a name="fixing-violations"></a>修正違規
 若要修正此規則的違規，請將屬性新增至元件，並指定中性文化特性之資源的語言。

## <a name="specifying-the-language"></a>指定語言

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>指定中性文化特性的資來源語言

1. 在**方案總管**中，以滑鼠右鍵按一下您的專案，然後按一下 [**屬性**]。

2. 從左側導覽列中選取 [**應用程式**]，然後按一下 [**元件資訊**]。

3. 在 [**元件資訊**] 對話方塊中，從 [**中性語言**] 下拉式清單中選取語言。

4. 按一下 [確定]。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 允許隱藏此規則的警告。 不過，啟動效能可能會降低。
