---
title: 如何：使用程式碼分析簽入原則強制程式碼可維護性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d54ca9a31e8a1bbd2496bf8689a119e53580c79
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660211"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>如何：以程式碼分析簽入原則強制程式碼的可維護性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

開發人員可以使用「程式碼度量」工具來測量其程式碼的複雜性和可維護性，但無法在簽入原則中叫用程式碼度量。 不過，小組可以啟用程式碼分析規則，以驗證程式代碼與程式碼計量標準的合規性，並透過簽入原則強制執行這些規則。 如需程式碼度量的詳細資訊，請參閱程式 [代碼度量值](../code-quality/code-metrics-values.md)。

 開發人員可以透過程式碼分析簽入原則來啟用繼承、類別結合、可維護性索引和複雜度規則的深度，以強制執行可維護的程式碼。 這四個規則都位於程式碼分析原則編輯器的 [可維護性規則] 類別之下。

 版本控制的系統管理員 [!INCLUDE[esprfound](../includes/esprfound-md.md)] 可以將程式碼分析可維護性規則新增至簽入原則需求。 這些簽入原則要求開發人員在起始簽入之前，根據這些規則變更來執行程式碼分析。

### <a name="to-open-the-code-analysis-policy-editor"></a>開啟程式碼分析原則編輯器

1. 在 **Team Explorer**中，以滑鼠右鍵按一下 team 專案，然後按一下 [ **team 專案設定**]，再按一下 [ **原始檔控制**]。

     [ **原始檔控制** ] 對話方塊隨即出現。

2. 在 [ **簽入原則** ] 索引標籤上，按一下 [ **新增**]。

     [ **加入簽入原則** ] 對話方塊隨即出現。

3. 在 [ **簽入原則** ] 清單中，選取 [程式 **代碼分析** ] 核取方塊，然後按一下 **[確定]**。

     [程式 **代碼分析原則編輯器** ] 對話方塊隨即出現。

### <a name="to-enable-code-analysis-maintainability-rules"></a>啟用程式碼分析可維護性規則

1. 在 [程式 **代碼分析原則編輯器** ] 對話方塊的 [ **規則設定**] 下，展開 [可 **維護性規則** ] 節點。

2. 選取下列規則的核取方塊：

    - 繼承深度： **CA1501 AvoidExcessiveInheritance** -臨界值：超過5個層級的警告深

    - 複雜性： **CA1502 AvoidExcessiveComplexity** -閾值：超過25的警告

    - 可維護性索引： **CA1505 AvoidUnmaintainableCode** -閾值：小於20的警告

    - 類別結合： **CA1506 AvoidExcessiveClassCoupling** -閾值：超過80的警告（針對某個類別）和超過30個方法

    - 此外，如果您想要違反規則來防止組建，請選取規則描述旁的 [將 **警告視為錯誤** ] 核取方塊。

3. 按一下 [確定]  。 新的簽入原則現在適用于未來的簽入。

## <a name="see-also"></a>另請參閱
 [建立和使用程式碼分析簽入原則](../code-quality/creating-and-using-code-analysis-check-in-policies.md)的程式[代碼計量值](../code-quality/code-metrics-values.md)
