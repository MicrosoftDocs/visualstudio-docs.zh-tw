---
title: C/C++ 程式碼分析概觀
ms.date: 04/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: ea576ba794350e6cee6b20f8ef9adb62f82a9c51
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="code-analysis-for-cc-overview"></a>程式碼分析 C/c + + 的概觀

C/c + + 程式碼分析工具會提供您的 C/c + + 程式碼中可能的缺失相關資訊。 這個工具所報告的常見程式碼錯誤包括：緩衝區滿溢、未初始化的記憶體、Null 指標取值以及記憶體和資源流失。 此工具也可以執行檢查針對[c + + 核心指導方針](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)。

## <a name="ide-integrated-development-environment-integration"></a>IDE （整合式的開發環境） 整合

程式碼分析工具已完全整合在 Visual Studio ide。

建置程序期間所產生的原始碼的警告會出現在錯誤清單。 您可以瀏覽至造成警告的原始程式碼，您可以檢視有關原因和可能的解決方案，問題的其他資訊。

## <a name="command-line-support"></a>命令列支援

您也可以使用分析工具，從命令列中，如下列範例所示：

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 15.7 和更新版本**您可以使用任何包括 CMake 的建置系統從命令列執行此工具。

## <a name="pragma-support"></a>#pragma 支援

您可以使用`#pragma`指示詞，以將警告視為錯誤; 啟用或停用警告，並隱藏個別的程式碼行的警告。 如需詳細資訊，請參閱[How to: C/c + + 專案設定程式碼分析屬性](how-to-set-code-analysis-properties-for-c-cpp-projects.md)。

## <a name="annotation-support"></a>附註支援

註解改善程式碼分析的精確度。 註釋提供前置和後置條件的其他資訊在函式參數和傳回型別。 如需詳細資訊，請參閱[How to： 使用 __analysis_assume 指定其他的程式碼資訊](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>簽入原則的一部分執行分析工具

您可以在需要所有來源的程式碼簽入都滿足特定的原則。 特別是，您會想要確定在步驟中的最新的本機組建已執行分析。 如需啟用程式碼分析簽入原則的詳細資訊，請參閱[建立和使用程式碼分析簽入原則](../code-quality/creating-and-using-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Team Build 整合

您可以使用建置系統的整合式的功能的步驟執行程式碼分析工具[!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]建置程序。 如需詳細資訊，請參閱[建置及發行](/vsts/build-release/index)。

## <a name="see-also"></a>另請參閱

- [快速入門： C/c + + 程式碼分析](quick-start-code-analysis-for-c-cpp.md)
- [逐步解說： 分析 C/c + + 程式碼的缺失](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [C/C++ 程式碼分析警告](code-analysis-for-c-cpp-warnings.md)
- [使用 C++ Core Guidelines 檢查工具](using-the-cpp-core-guidelines-checkers.md)
- [C + + 核心指導方針檢查程式參考](code-analysis-for-cpp-corecheck.md)
- [使用規則集來指定要執行的 C++ 規則](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [使用程式碼分析工具分析驅動程式品質](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [程式碼分析驅動程式警告](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
