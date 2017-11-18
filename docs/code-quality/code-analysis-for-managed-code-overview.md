---
title: "程式碼分析，Managed 程式碼的概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eebc25b344e603cb66546db6d9179067d5995496
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="code-analysis-for-managed-code-overview"></a>Managed 程式碼的程式碼分析概觀
Managed 程式碼的程式碼分析可以分析 Managed 組件並回報有關組件的資訊，例如是否違反 Microsoft .NET Framework 設計方針所制定的程式設計和設計規則。  
  
 分析工具會將分析期間所做的檢查顯示為警告訊息。 警告訊息會識別任何相關的程式設計和設計問題，並且在可能的時候，提供如何修正問題的資訊。  
  
## <a name="ide-integrated-development-environment-integration"></a>IDE (整合式開發環境) 整合  
 開發人員可以對專案自動執行程式碼分析，或者也可以手動執行分析。  
  
 若要建立專案時，您每次執行程式碼分析，您選取**啟用建置程式碼分析 （定義 CODE_ANALYSIS 常數）**專案屬性頁上。 如需詳細資訊，請參閱[How to： 啟用和停用自動程式碼分析](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)。  
  
 若要程式碼手動執行分析專案，在**分析**功能表上，按一下 **上執行程式碼分析***ProjectName*。 如需詳細資訊，請參閱[How to： 啟用和停用自動程式碼分析](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)。  
  
## <a name="rule-sets"></a>規則集  
 Managed 程式碼的程式碼分析規則分組為*規則集*。 您可以使用其中一個 Microsoft 標準規則集，或建立自訂規則集來滿足特定需求。 如需詳細資訊，請參閱[使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)。  
  
## <a name="in-source-suppression"></a>原始檔中隱藏項目  
 最大的用途是指出某個警告不適用。 這會通知程式開發人員和其他稍後可能會檢閱程式碼的人員，指出您已經調查此警告並且隱藏或忽略它。  
  
 警告的「原始檔中隱藏項目」是透過自訂屬性來實作。 若要隱藏警告，請將 `SuppressMessage` 屬性加入至原始程式碼，如下列範例所示：  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 如需詳細資訊，請參閱[使用 SuppressMessage 屬性所隱藏的警告](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)。  
  
## <a name="run-code-analysis-as-part-of-check-in-policy"></a>執行程式碼分析做為簽入原則的一部分  
 從組織的角度來看，您可能想指定所有的簽入都要滿足特定的原則， 尤其您會想要確認您已經確實遵循這些原則：  
  
-   所簽入的程式碼中沒有建置錯誤。  
  
-   已執行程式碼分析做為最新組建的一部分。  
  
 您可以指定簽入原則，達成上述要求。 如需詳細資訊，請參閱[使用 Team 專案簽入原則強化程式碼品質](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)。  
  
## <a name="team-build-integration"></a>Team Build 整合  
 您可以使用建置系統的整合式功能，執行分析工具做為建置流程的一部分。 如需詳細資訊，請參閱[建置應用程式](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)。  
  
## <a name="see-also"></a>另請參閱  
 [使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [如何： 啟用和停用自動程式碼分析](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)