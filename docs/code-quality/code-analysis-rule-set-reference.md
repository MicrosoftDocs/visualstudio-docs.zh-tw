---
title: "程式碼分析規則集參考 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f396bb289e7e4288dbb80c6e08990960861e970c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="code-analysis-rule-set-reference"></a>程式碼分析規則集參考
當您設定的程式碼分析 managed 程式碼專案中的[!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]， [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]，或[!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]您會看到一份內建*規則集*。 您可以使用其中一個標準規則集，或您可以自訂規則集以符合您的專案需求。  
  
## <a name="available-rule-sets"></a>可用的規則集  
 下表列出預設的規則集：  
  
|||  
|-|-|  
|[所有規則規則集](../code-quality/all-rules-rule-set.md)|這個規則集包含所有規則。 執行這個規則集可能會導致大量的警告回報。 使用這個規則集以取得從全方位的所有問題的程式碼中。 這可協助您決定哪一個更受關注的規則集是最適合用來執行您的專案。|  
|[適用於 Managed 程式碼的基本正確性規則規則集](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|這些規則的重點在於邏輯錯誤和使用 framework 應用程式開發介面中所做的常見錯誤。 包含這個規則集以擴充的最小建議規則所報告的警告清單。|  
|[適用於 Managed 程式碼的基本設計方針規則規則集](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|這些規則的重點在於強制最佳作法，讓您輕鬆地了解和使用程式碼。 包含這個規則集，如果您的專案包含程式庫程式碼，或如果您想要強制執行的程式碼可輕鬆地維護最佳作法。|  
|[適用於 Managed 程式碼的擴充正確性規則規則集](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|這些規則會擴大基本正確性規則，若要最大化邏輯和 framework 使用錯誤報告。 額外的強調的重點是特定的案例，例如 COM interop 和行動應用程式。 請考慮包含這個規則集如果任一這些案例適用於您的專案或專案中找出其他問題。|  
|[適用於 Managed 程式碼的擴充設計方針規則規則集](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|這些規則會擴大基本設計方針規則，若要最大化的可用性和可維護性問題，會報告。 額外的強調重點是命名指導方針。 請考慮包含這個規則集，如果您的專案包含程式庫程式碼，或如果您想要強制執行最高標準來撰寫容易維護的程式碼。|  
|[適用於 Managed 程式碼的全球化規則規則集](../code-quality/globalization-rules-rule-set-for-managed-code.md)|這些規則的重點在於避免用於不同的語言、 地區設定中和文化特性時會無法正確顯示在應用程式中資料的問題。 包含這個規則集，如果您的應用程式已當地語系化或全球化。|  
|[受管理的最小規則規則集為 managed 程式碼](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|這些規則的重點在於程式碼分析是最精確的程式碼中最關鍵的問題。  這些規則較小的數字和它們僅供在有限的 Visual Studio 版本中執行。  與其他 Visual Studio 版本使用 MinimumRecommendedRules.ruleset。|  
|[適用於 Managed 程式碼的 Managed 建議規則規則集](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|這些規則的重點在於程式碼，包括潛在的安全性漏洞、 應用程式當機，以及其他重要邏輯和設計錯誤中最關鍵的問題。 您應該建立包含這個規則設定任何自訂規則集中您針對您的專案。|  
|[混合最小規則規則集](../code-quality/mixed-minimum-rules-rule-set.md)|這些規則的重點在於支援 Common Language Runtime，包括潛在的安全性漏洞和應用程式損毀的 c + + 專案中最關鍵的問題。 您應該包含您為支援 Common Language Runtime 之 c + + 專案建立這個規則集的任何自訂規則集。|  
|[混合建議規則規則集](../code-quality/mixed-recommended-rules-rule-set.md)|這些規則的重點在於支援 Common Language Runtime，包括潛在的安全性漏洞、 應用程式當機，以及其他重要邏輯和設計錯誤的 c + + 專案中最常用及最重要的問題。 您應該包含您為支援 Common Language Runtime 之 c + + 專案建立這個規則集的任何自訂規則集。  這個規則集被設計來與 Visual Studio Professional 版及更高版本設定。|  
|[原生最小規則規則集](../code-quality/native-minimum-rules-rule-set.md)|這些規則的重點在於機器碼，包括潛在的安全性漏洞和應用程式損毀中最關鍵的問題。 您應該在為原生專案建立的任何自訂規則集中，包含此規則集。|  
|[原生建議規則規則集](../code-quality/native-recommended-rules-rule-set.md)|這些規則的重點在於機器碼，包括潛在的安全性漏洞和應用程式損毀中最關鍵且常見的問題。  您應該在為原生專案建立的任何自訂規則集中，包含此規則集。  這個規則集被設計來搭配 Visual Studio Professional 版與更高版本。|  
|[適用於 Managed 程式碼的安全性規則規則集](../code-quality/security-rules-rule-set-for-managed-code.md)|這個規則集包含所有 Microsoft 安全性規則。 包含這個規則集至所報告的潛在安全性問題數目最大化。|
