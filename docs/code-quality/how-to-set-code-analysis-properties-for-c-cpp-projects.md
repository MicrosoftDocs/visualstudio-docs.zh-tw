---
title: 如何：為 C/C++ 專案設定程式碼分析屬性
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: f2800ce4784f5a8215dfe49b00194925c3cdb588
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920673"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>如何：為 C/C++ 專案設定程式碼分析屬性
您可以設定使用哪些規則程式碼分析工具來分析專案的每個組態中的程式碼。 此外，您可以將程式碼分析，隱藏警告的程式碼與產生及協力廠商工具加入至您的專案。

## <a name="code-analysis-property-page"></a>程式碼分析 屬性頁
 **程式碼分析**屬性頁包含所有專案的程式碼分析組態設定。 若要開啟的專案中的程式碼分析 屬性頁**方案總管 中**，以滑鼠右鍵按一下專案，然後按一下**屬性**。 接下來，依序展開**組態屬性**選取**程式碼分析** 索引標籤。

## <a name="project-configuration-and-platform"></a>專案組態與平台
 **組態**清單和**平台**清單可讓您將不同的程式碼分析設定套用到不同的專案組態和平台組合。 例如，您可以直接將一組規則套用於專案的偵錯的程式碼分析組建和一組不同版本的組建。

## <a name="enabling-code-analysis"></a>啟用程式碼分析
 您可以決定是否要啟用程式碼分析為您的專案選取**啟用程式碼分析的 C/c + + 建置**。 搭配**組態** 清單中，您可以比方說，決定停用偵錯組建，並啟用其發行組建的程式碼分析。

 如果您的專案包含 managed 程式碼，您可以決定是否要啟用或停用選取的程式碼分析**建置時啟用程式碼分析**。

 程式碼分析被設計來協助您改善您的程式碼的品質，並避免常犯的錯誤。 因此，請仔細考慮是否要停用程式碼分析。 它通常會比較好停用規則集，或您不想個別規則套用至您的專案。

## <a name="generated-code"></a>產生的程式碼
 開發人員經常會使用工具，可協助快速開發應用程式。 這些工具可以產生程式碼加入至專案。 您可能想要查看產生的程式碼中發現的程式碼分析規則違規。 不過，您可能不想看到它們如果不想維護的程式碼。

 **隱藏結果從產生的程式碼** 核取方塊**一般**屬性頁面可讓您選取您是否想要看到從協力廠商工具所產生的 managed 程式碼的程式碼分析警告.

## <a name="rule-sets"></a>規則集
 如果您的專案包含 managed 程式碼，您可以選取要藉由選取規則集的程式碼分析中套用的規則**執行此規則集**清單。

## <a name="see-also"></a>另請參閱
 [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) [C/c + + 警告的程式碼分析](../code-quality/code-analysis-for-c-cpp-warnings.md)