---
title: 程式碼分析規則集參考 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a3c0b347f186c5adee6cf86a0e1720ebfa80f253
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670108"
---
# <a name="code-analysis-rule-set-reference"></a>程式碼分析規則集參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您為 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]、[!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] 或 [!INCLUDE[vsPro](../includes/vspro-md.md)]you 中的 managed 程式碼專案設定程式碼分析時，會顯示內建*規則集*清單。 您可以使用其中一個標準規則集，也可以自訂規則集以符合您的專案需求。

## <a name="available-rule-sets"></a>可用的規則集
 下表列出預設的規則集：

|||
|-|-|
|[所有規則規則集](../code-quality/all-rules-rule-set.md)|此規則集包含所有規則。 執行此規則集可能會導致報告大量的警告。 使用此規則集可完整瞭解程式碼中的所有問題。 這可協助您決定哪一個更專注的規則集最適合針對您的專案執行。|
|[適用於 Managed 程式碼的基本正確性規則規則集](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|這些規則著重于邏輯錯誤，以及使用 framework Api 時所發生的常見錯誤。 包含此規則集，以展開最小建議規則所報告的警告清單。|
|[適用於 Managed 程式碼的基本設計方針規則規則集](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|這些規則的重點在於強制執行最佳作法，讓您的程式碼更容易瞭解和使用。 如果您的專案包含程式庫程式碼，或如果您想要強制執行可輕鬆維護程式碼的最佳作法，請包含此規則集。|
|[適用於 Managed 程式碼的擴充正確性規則規則集](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|這些規則會擴充基本的正確性規則，以最大化所報告的邏輯和架構使用錯誤。 額外的強調會放在特定案例中，例如 COM Interop 和行動應用程式。 如果其中一個案例適用于您的專案，或在您的專案中找出其他問題，請考慮包含這個規則集。|
|[適用於 Managed 程式碼的擴充設計方針規則規則集](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|這些規則會擴充基本的設計指導方針規則，以最大化所報告的可用性和可維護性問題。 額外的強調會放在命名指導方針上。 如果您的專案包含程式庫程式碼，或者您想要強制執行最高的標準來撰寫可維護的程式碼，請考慮包含這個規則集。|
|[適用於 Managed 程式碼的全球化規則規則集](../code-quality/globalization-rules-rule-set-for-managed-code.md)|這些規則著重于在不同語言、地區設定和文化特性中使用時，導致應用程式中的資料無法正確顯示的問題。 如果您的應用程式已當地語系化或全球化，請包含這個規則集。|
|[適用於 Managed 程式碼的 Managed 最小規則規則集](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|這些規則的重點在於程式碼中最重要的問題，那就是最精確的程式碼分析。  這些規則的數目很小，而且僅適用于在有限的 Visual Studio 版本中執行。  使用 MinimumRecommendedRules 搭配其他 Visual Studio 版本。|
|[適用於 Managed 程式碼的 Managed 建議規則規則集](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|這些規則的重點在於程式碼中最嚴重的問題，包括潛在的安全性漏洞、應用程式當機，以及其他重要的邏輯和設計錯誤。 您應該將此規則集包含在您為專案建立的任何自訂規則集中。|
|[混合最小規則規則集](../code-quality/mixed-minimum-rules-rule-set.md)|這些規則的重點在於支援 Common Language Runtime 之C++專案中最嚴重的問題，包括潛在的安全性漏洞和應用程式損毀。 您應該將此規則集包含在您為支援 Common Language Runtime 之C++專案所建立的任何自訂規則集中。|
|[混合建議規則規則集](../code-quality/mixed-recommended-rules-rule-set.md)|這些規則著重于您C++的專案中，支援 Common Language Runtime 的最常見和重大問題，包括潛在的安全性漏洞、應用程式損毀，以及其他重要的邏輯和設計錯誤。 您應該將此規則集包含在您為支援 Common Language Runtime 之C++專案所建立的任何自訂規則集中。  此規則集的設計目的是要使用 Visual Studio Professional 版和更新版本來設定。|
|[原生最小規則規則集](../code-quality/native-minimum-rules-rule-set.md)|這些規則的重點在於機器碼中最嚴重的問題，包括潛在的安全性漏洞和應用程式損毀。 您應該在為原生專案建立的任何自訂規則集中，包含此規則集。|
|[原生建議規則規則集](../code-quality/native-recommended-rules-rule-set.md)|這些規則的重點在於機器碼中最重要的問題，包括潛在的安全性漏洞和應用程式當機。  您應該在為原生專案建立的任何自訂規則集中，包含此規則集。  這個規則集是設計來搭配 Visual Studio Professional edition 和更新版本使用。|
|[適用於 Managed 程式碼的安全性規則規則集](../code-quality/security-rules-rule-set-for-managed-code.md)|此規則集包含所有 Microsoft 安全性規則。 包含此規則集，可將報告的潛在安全性問題數目最大化。|
