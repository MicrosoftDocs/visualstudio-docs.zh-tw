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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a1f91b352da5a41ec2ef81fb6067976073c787ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62576748"
---
# <a name="code-analysis-rule-set-reference"></a>程式碼分析規則集參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您設定的程式碼分析 managed 程式碼專案中的[!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]， [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]，或[!INCLUDE[vsPro](../includes/vspro-md.md)]您會看到一份內建*規則集*。 您可以使用其中一個標準規則集，也可以自訂規則集以符合您的專案需求。  
  
## <a name="available-rule-sets"></a>可用的規則集  
 下表列出預設的規則集：  
  
|||  
|-|-|  
|[所有規則規則集](../code-quality/all-rules-rule-set.md)|這個規則集包含所有規則。 執行此規則集可能會導致大量的警告回報。 使用這個規則集以取得程式碼中的所有問題的完整圖像。 這可協助您決定哪些焦點更為集中的規則集是最適合用來執行您的專案。|  
|[適用於 Managed 程式碼的基本正確性規則規則集](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|這些規則的重點在於邏輯錯誤和架構 Api 的使用方式中所做的常見錯誤。 包含這個規則集以展開 最小建議規則所回報的警告清單。|  
|[適用於 Managed 程式碼的基本設計方針規則規則集](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|這些規則的重點在於強制最佳作法，讓您輕鬆地了解和使用程式碼。 包含這個規則集，如果您的專案包含程式庫程式碼，或如果您想要強制最佳實務以便於維護程式碼。|  
|[適用於 Managed 程式碼的擴充正確性規則規則集](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|這些規則會擴大基本正確性規則的最大化的邏輯和 framework 使用錯誤報告。 額外的重點會放在特定的案例，例如 COM interop 和行動應用程式。 請考慮包含這個規則集如果任一這些案例適用於您的專案或您的專案中找出其他問題。|  
|[適用於 Managed 程式碼的擴充設計方針規則規則集](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|這些規則會擴大基本設計方針規則，以最大化所報告的可用性和可維護性問題。 額外特別強調命名方針。 請考慮包含這個規則集，如果您的專案包含程式庫程式碼，或如果您想要強制執行最高的標準，來撰寫容易維護的程式碼。|  
|[適用於 Managed 程式碼的全球化規則規則集](../code-quality/globalization-rules-rule-set-for-managed-code.md)|這些規則的重點在於使用於不同的語言、 地區設定中和文化特性時會無法正確顯示的應用程式中資料的問題。 包含這個規則集，如果您的應用程式已當地語系化或全球化。|  
|[適用於 Managed 程式碼的 Managed 最小規則規則集](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|這些規則的重點在於程式碼分析的最精確的程式碼中最關鍵的問題。  這些規則是數量很少，它們僅供有限的 Visual Studio 版本中執行。  與其他 Visual Studio 版本使用 MinimumRecommendedRules.ruleset。|  
|[適用於 Managed 程式碼的 Managed 建議規則規則集](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|這些規則的重點包括潛在的安全性漏洞、 應用程式當機，以及其他重要的邏輯和設計錯誤的程式碼中最關鍵的問題。 您應該包含您專案建立的此規則設定任何自訂規則集中。|  
|[混合最小規則規則集](../code-quality/mixed-minimum-rules-rule-set.md)|這些規則的重點在於最關鍵的問題，在您C++支援 Common Language Runtime，包括潛在的安全性漏洞和應用程式損毀的專案。 您應該包含這個規則集建立的任何自訂規則集中您C++支援 Common Language Runtime 的專案。|  
|[混合建議規則規則集](../code-quality/mixed-recommended-rules-rule-set.md)|這些規則的重點在於最一般和重大的問題在您C++支援 Common Language Runtime，包括潛在的安全性漏洞、 應用程式當機，以及其他重要的邏輯和設計錯誤的專案。 您應該包含這個規則集建立的任何自訂規則集中您C++支援 Common Language Runtime 的專案。  此規則被設計來與 Visual Studio Professional 版及更新版本設定。|  
|[原生最小規則規則集](../code-quality/native-minimum-rules-rule-set.md)|這些規則的重點在於您的原生程式碼，包括潛在的安全性漏洞和應用程式損毀最關鍵的問題。 您應該在為原生專案建立的任何自訂規則集中，包含此規則集。|  
|[原生建議規則規則集](../code-quality/native-recommended-rules-rule-set.md)|這些規則的重點在於最關鍵且常見的問題，您的原生程式碼，包括潛在的安全性漏洞和應用程式損毀。  您應該在為原生專案建立的任何自訂規則集中，包含此規則集。  此規則可配合使用 Visual Studio Professional edition 和更新版本。|  
|[適用於 Managed 程式碼的安全性規則規則集](../code-quality/security-rules-rule-set-for-managed-code.md)|這個規則集包含所有的 Microsoft 安全性規則。 包含這個規則集以最大化所報告的潛在安全性問題數目。|
