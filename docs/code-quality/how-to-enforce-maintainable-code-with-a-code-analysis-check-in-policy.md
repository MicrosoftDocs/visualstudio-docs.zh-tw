---
title: 使用程式碼分析簽入原則
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 883b5e231036c446c1cbf1fbc2fc125a01b3de62
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371855"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>如何：以程式碼分析簽入原則強制維護程式碼

開發人員可以使用程式碼計量工具來測量其程式碼的複雜性和可維護性，但您無法將程式碼計量當做簽入原則的一部分叫用。 不過，您可以啟用程式碼分析規則，以驗證程式代碼是否符合程式碼計量標準，並透過簽入原則強制執行規則。 如需程式碼計量的詳細資訊，請參閱程式[代碼度量值](../code-quality/code-metrics-values.md)。

您可以透過程式碼分析簽入原則，啟用繼承、類別結合、可維護性索引和複雜性規則的深度，以強制執行可維護的程式碼。 這四個規則都可以在 [程式碼分析原則編輯器] 的 [可維護性規則] 類別底下找到。

Team Foundation 版本控制的系統管理員可以將程式碼分析維護性規則新增至簽入原則需求。 這些簽入原則會要求開發人員在起始簽入之前，根據這些規則變更來執行程式碼分析。

## <a name="to-open-the-code-analysis-policy-editor"></a>若要開啟程式碼分析原則編輯器

1. 在**Team Explorer**中，以滑鼠右鍵按一下專案，按一下 [**專案設定**]，然後按一下 [**原始檔控制**]。

     [**原始檔控制**] 對話方塊隨即出現。

2. 在 [**簽入原則**] 索引標籤上，按一下 [**新增**]。

     [**新增簽入原則**] 對話方塊隨即出現。

3. 在 [**簽入原則**] 清單中，選取 [程式**代碼分析**] 核取方塊，然後按一下 **[確定]**。

     [程式**代碼分析原則編輯器**] 對話方塊隨即出現。

## <a name="to-enable-code-analysis-maintainability-rules"></a>啟用程式碼分析可維護性規則

1. 在 [程式**代碼分析原則編輯器**] 對話方塊的 [**規則設定**] 底下，展開 [可**維護性規則**] 節點。

2. 選取下列規則的核取方塊：

   - 繼承深度： **CA1501 AvoidExcessiveInheritance** -臨界值：深度超過5層的警告

   - 複雜度： **CA1502 AvoidExcessiveComplexity** -臨界值：警告超過25

   - 可維護性索引： **CA1505 AvoidUnmaintainableCode** -臨界值：警告少於20

   - 類別結合： **CA1506 AvoidExcessiveClassCoupling** -臨界值：針對類別超過80的警告，針對方法使用超過30

     此外，如果您想要違反規則以防止組建成功，請選取規則描述旁的 [將**警告視為錯誤**] 核取方塊。

3. 按一下 [確定]。 新的簽入原則現在適用于未來的簽入。

## <a name="see-also"></a>另請參閱

- [程式碼度量值](../code-quality/code-metrics-values.md)
- [建立和使用程式碼分析簽入原則](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)
