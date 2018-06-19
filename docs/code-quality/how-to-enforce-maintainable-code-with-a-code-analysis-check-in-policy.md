---
title: 如何：以程式碼分析簽入原則強制程式碼的可維護性
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6269b4839c552fa6a1e982226bbb311cb7d5e9d9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921123"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>如何： 強制執行維護的程式碼與程式碼分析簽入原則

開發人員可以使用程式碼度量資訊工具來測量的複雜度和維護的程式碼，但您無法將程式碼度量叫用做為簽入原則的一部分。 不過，您可以啟用程式碼分析規則，以驗證您的程式碼的相容性程式碼度量資訊的標準，並強制執行規則，透過簽入原則。 如需程式碼度量的詳細資訊，請參閱[程式碼度量值](../code-quality/code-metrics-values.md)。

您可以啟用的繼承深度、 類別結合程度、 可維護性指數和複雜性規則來強制執行維護的程式碼，透過程式碼分析簽入原則。 這些規則的所有四個程式碼分析原則編輯器中，找到 [可維護性規則] 類別底下。

Team foundation 版本控制系統管理員可以加入程式碼分析可維護性規則的簽入原則需求。 這些簽入原則需要開發人員執行程式碼分析簽入初始化之前，根據這些規則變更。

## <a name="to-open-the-code-analysis-policy-editor"></a>若要開啟程式碼分析原則編輯器

1. 在**Team Explorer**、 team 專案上按一下滑鼠右鍵、 按一下**Team 專案設定**，然後按一下 **原始檔控制**。

     **原始檔控制** 對話方塊隨即出現。

2. 在**簽入原則**索引標籤，然後按一下**新增**。

     **新增簽入原則** 對話方塊隨即出現。

3. 在**簽入原則**清單中，選取**程式碼分析**核取方塊，然後**確定**。

     **程式碼分析原則編輯器** 對話方塊隨即出現。

## <a name="to-enable-code-analysis-maintainability-rules"></a>若要啟用程式碼分析可維護性規則

1. 在**程式碼分析原則編輯器**對話方塊的 **規則設定**，依序展開**可維護性規則**節點。

2. 選取核取方塊，下列規則：

    -   繼承深度： **CA1501 AvoidExcessiveInheritance** -臨界值： 警告位於層級的深度超過 5

    -   複雜度： **CA1502 AvoidExcessiveComplexity** -臨界值： 在多個 25 警告

    -   可維護性指數： **ca1505 應 AvoidUnmaintainableCode** -臨界值： 警告少於 20

    -   結合的類別： **CA1506 AvoidExcessiveClassCoupling** -臨界值： 警告位於多個類別 80 和超過 30 方法

    此外，如果您想要阻礙建置成功對規則違規時，選取**將警告視為錯誤**規則說明旁邊的核取方塊。

3. 按一下 [確定 **Deploying Office Solutions**]。 新的簽入原則現在會套用至未來的簽入。

## <a name="see-also"></a>另請參閱

- [程式碼度量值](../code-quality/code-metrics-values.md)
- [建立和使用程式碼分析簽入原則](../code-quality/creating-and-using-code-analysis-check-in-policies.md)