---
title: 如何：設定 C 專案的程式C++代碼分析屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: b2fb3cb81b49fd4b8cc83e0548110d2025c7488d
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277994"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>如何：為 C/C++ 專案設定程式碼分析屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以設定程式碼分析工具使用哪些規則來分析專案的每個設定中的程式碼。 此外，您可以指示程式碼分析，將警告從由協力廠商工具產生並新增至專案的程式碼隱藏。  
  
## <a name="code-analysis-property-page"></a>程式碼分析屬性頁  
 [程式**代碼分析**] 屬性頁包含專案的所有程式碼分析設定。 若要在**方案總管**中開啟專案的 [程式碼分析] 屬性頁，請以滑鼠右鍵按一下專案，然後按一下 [**屬性**]。 接下來，展開 [設定**屬性**]，然後選取 [程式**代碼分析**] 索引標籤。  
  
## <a name="project-configuration-and-platform"></a>專案設定和平臺  
 [設定清單] 和 [**平臺** **] 清單可**讓您將不同的程式碼分析設定套用至不同的專案配置和平臺組合。 例如，您可以指示程式碼分析，將一組規則套用至您的專案，以用於 debug 組建，以及針對發行組建使用不同的集合。  
  
## <a name="enabling-code-analysis"></a>啟用程式碼分析  
 您可以選取 [**啟用 C/C++ on Build 的程式碼分析**]，以決定是否要啟用專案的程式碼分析。 例如，您可以將與設定清單結合，以決定停用 debug **build 的程式**代碼分析，並針對發行組建加以啟用。  
  
 如果您的專案包含 managed 程式碼，您可以選取 [**在組建上啟用程式碼分析**]，以決定是否要啟用或停用程式碼分析。  
  
 程式碼分析是設計用來協助您改善程式碼的品質，並避免常見的陷阱。 因此，請仔細考慮是否要停用程式碼分析。 通常最好是停用您不想要套用至專案的規則集或個別規則。  
  
## <a name="generated-code"></a>產生的程式碼  
 開發人員經常使用工具來協助快速開發應用程式。 這些工具可以產生已加入至專案的程式碼。 您可能想要查看程式碼分析在產生的程式碼中探索到的規則違規。 不過，如果您不想要維護程式碼，您可能不想要查看它們。  
  
 [**一般**屬性] 頁面上的 [**隱藏產生的程式碼的結果**] 核取方塊可讓您選取是否要查看協力廠商工具所產生之 managed 程式碼的程式碼分析警告。  
  
## <a name="rule-sets"></a>規則集  
 如果您的專案包含 managed 程式碼，您可以從 [**執行此規則集**] 清單中選取規則集，以選取要在程式碼分析中套用的規則。  
  
## <a name="see-also"></a>另請參閱  
 [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [C/C++ 程式碼分析警告](../code-quality/code-analysis-for-c-cpp-warnings.md)
