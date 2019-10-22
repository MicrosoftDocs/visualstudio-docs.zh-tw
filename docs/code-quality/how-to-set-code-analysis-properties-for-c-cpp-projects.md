---
title: 如何：為 C/C++ 專案設定程式碼分析屬性
ms.date: 11/04/2016
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
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 27f3d68d28b8d1799c52fcf83c6a00dc5f81f48a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448912"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>如何：為 C/C++ 專案設定程式碼分析屬性

您可以設定程式碼分析工具使用哪些規則來分析專案的每個設定中的程式碼。 此外，您可以指示程式碼分析，將警告從由協力廠商工具產生並新增至專案的程式碼隱藏。

## <a name="code-analysis-property-page"></a>程式碼分析屬性頁

[程式**代碼分析**] 屬性頁包含 MSBuild 專案的所有程式碼分析設定。 若要在**方案總管**中開啟專案的 [程式碼分析] 屬性頁，請以滑鼠右鍵按一下專案，然後按一下 [**屬性**]。 接下來，展開 [設定**屬性**]，然後選取 [程式**代碼分析**] 索引標籤。

## <a name="project-configuration-and-platform"></a>專案設定和平臺

視窗頂端的 [設定清單] 和 [**平臺** **] 清單可**讓您將不同的程式碼分析設定套用至不同的 [專案設定] 和 [平臺] 組合。 例如，您可以指示程式碼分析，將一組規則套用至您的專案，以用於 debug 組建，以及針對發行組建使用不同的集合。

## <a name="enabling-code-analysis"></a>啟用程式碼分析

您可以藉由切換 [**啟用 Microsoft 程式碼分析**] 和 [**啟用 Clang** ] 選項來啟用專案的程式碼分析，並藉由選取 [**在組建上啟用程式碼分析**]，進一步設定是否在組建上執行。 例如，您可以將與設定清單結合，以決定停用 debug **build 的程式**代碼分析，並針對發行組建加以啟用。

程式碼分析是設計用來協助您改善程式碼的品質，並避免常見的陷阱。 因此，請仔細考慮是否要停用程式碼分析。 通常最好是停用您不想要套用至專案的規則集、個別規則或個別檢查。

## <a name="cmake-configuration"></a>CMake 設定

在 CMake projects 中，變更 `CMakeSettings.json` 內 `enableMicrosoftCodeAnalysis` 和 `enableClangTidyCodeAnalysis` 索引鍵的值，以啟用或停用程式碼分析。 如需詳細資訊，請參閱[在 Visual Studio 中使用 Clang-整齊](../code-quality/clang-tidy.md)。

## <a name="see-also"></a>請參閱

- [分析 Managed 程式碼品質](../code-quality/code-analysis-for-managed-code-overview.md)
- [C/C++ 程式碼分析警告](../code-quality/code-analysis-for-c-cpp-warnings.md)
- [程式碼的C++規則集](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [使用 Clang-整齊](../code-quality/clang-tidy.md)
