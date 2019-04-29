---
title: HOW TO：以程式碼分析簽入原則來強制程式碼的可維護性
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7139c952b40957a564fcd4074b1c931817dfb851
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62815814"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>HOW TO：強制維護的程式碼的程式碼分析簽入原則

開發人員可以使用程式碼度量資訊工具來測量的複雜度和維護的程式碼，但您無法簽入原則的一部分叫用程式碼度量資訊。 不過，您可以啟用驗證的程式碼度量資訊的標準，符合您的程式碼的程式碼分析規則，並強制執行透過簽入原則的規則。 如需程式碼度量的詳細資訊，請參閱[程式碼度量值](../code-quality/code-metrics-values.md)。

您可以啟用繼承深度、 類別結合程度、 可維護性指數和複雜度規則來強制執行容易維護的程式碼，透過程式碼分析簽入原則。 全部四個欄位，這些規則的程式碼分析原則編輯器中，找到 [可維護性規則] 類別下。

Team foundation 版本控制的系統管理員可以將程式碼分析可維護性規則加入簽入原則需求。 這些簽入原則會要求執行程式碼分析簽入初始化之前，根據這些規則變更的開發人員。

## <a name="to-open-the-code-analysis-policy-editor"></a>若要開啟 程式碼分析原則編輯器

1. 在  **Team Explorer**，以滑鼠右鍵按一下專案，按一下**專案設定**，然後按一下 **原始檔控制**。

     **原始檔控制** 對話方塊隨即出現。

2. 在 **簽入原則**索引標籤，然後按一下**新增**。

     **新增簽入原則** 對話方塊隨即出現。

3. 在 **簽入原則**清單中，選取**程式碼分析**核取方塊，然後按一下**確定**。

     **程式碼分析原則編輯器** 對話方塊隨即出現。

## <a name="to-enable-code-analysis-maintainability-rules"></a>若要啟用程式碼分析可維護性規則

1. 在 **程式碼分析原則編輯器**對話方塊的 **規則設定**，展開**維護性規則**節點。

2. 選取核取方塊，如下列規則：

   - 繼承深度：**CA1501 AvoidExcessiveInheritance** -臨界值：警告層級的深度超過 5

   - 複雜度：**CA1502 AvoidExcessiveComplexity** -臨界值：在多個 25 的警告

   - 可維護性指數：**CA1505 AvoidUnmaintainableCode** - Threshold:在少於 20 的警告

   - 類別結合程度：**CA1506 AvoidExcessiveClassCoupling** -臨界值：在多個類別的 80 和多個方法的 30 的警告

     此外，如果您想避免成功的組建將規則違規時，請選取**將警告視為錯誤**規則描述旁邊的核取方塊。

3. 按一下 [確定] 。 新的簽入原則現在適用於未來的簽入。

## <a name="see-also"></a>另請參閱

- [程式碼度量值](../code-quality/code-metrics-values.md)
- [建立和使用程式碼分析簽入原則](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)