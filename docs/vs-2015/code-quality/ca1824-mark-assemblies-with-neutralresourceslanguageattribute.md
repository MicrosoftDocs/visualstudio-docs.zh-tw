---
title: CA1824:組件必須標記 neutralresourceslanguageattribute |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 795d48b96392057a3f96cf3a67f3c49de8aee9b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203079"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824:組件必須標記 NeutralResourcesLanguageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|分類|Microsoft.Performance|
|中斷變更|非重大|

## <a name="cause"></a>原因
 組件包含**ResX**-基礎資源，但並沒有<xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName>套用到它。

## <a name="rule-description"></a>規則描述
 **NeutralResourcesLanguage**屬性會通知**ResourceManager**用來顯示組件的中性文化特性之資源的語言。 尋找在文化特性中性資源語言，與相同的資源時**ResourceManager**會自動使用位於主要組件中的資源。 它的運作而不是搜尋具有目前執行緒的目前使用者介面文化特性的附屬組件。 這可改善載入第一個資源的查詢效能，而且可以減少您的工作集。

## <a name="fixing-violations"></a>修正違規
 若要修正此規則的違規情形，將屬性新增至組件，並指定語言的中性文化特性的資源。

## <a name="specifying-the-language"></a>指定的語言

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>若要指定不因文化特性中性資源語言

1. 在 **方案總管**，以滑鼠右鍵按一下您的專案，然後按一下**屬性**。

2. 從左側的導覽列中選取**應用程式**，然後按一下**組件資訊**。

3. 在 **組件資訊**對話方塊方塊中，選取語言，從**中性語言**下拉式清單。

4. 按一下 [確定 **Deploying Office Solutions**]。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 就可以隱藏此規則的警告。 不過，可能會降低啟動效能。
