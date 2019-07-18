---
title: C/C++ 程式碼分析概觀
ms.date: 04/28/2018
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
ms.openlocfilehash: 5c4221783768f1e579ecad74fdfaf6e74214edfd
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226141"
---
# <a name="code-analysis-for-cc-overview"></a>C/C++ 程式碼分析概觀

C /C++程式碼分析工具會提供可能的缺失，C 中的資訊 /C++原始程式碼。 這個工具所報告的常見程式碼錯誤包括：緩衝區滿溢、未初始化的記憶體、Null 指標取值以及記憶體和資源流失。 此工具也可以執行檢查，針對[ C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)。

## <a name="ide-integrated-development-environment-integration"></a>IDE （整合式的開發環境） 整合

程式碼分析工具已完全整合在 Visual Studio IDE 中。

在建置程序期間，任何針對原始程式碼所產生的警告都會出現在 [錯誤清單] 中。 您可以巡覽至造成警告的原始程式碼，也可以檢視問題原因和可能解決方法的其他資訊。

## <a name="command-line-support"></a>命令列支援

您也可以使用分析工具，從命令列中，如下列範例所示：

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 15.7 版及更新版本**您可以從命令列執行工具，以包括 CMake 任何組建系統。

## <a name="pragma-support"></a>#pragma 支援

您可以使用`#pragma`指示詞，以將警告視為錯誤; 啟用或停用警告，並隱藏個別的程式碼行警告。 如需詳細資訊，請參閱 [Pragma 指示詞和 __Pragma 關鍵字](https://docs.microsoft.com/cpp/preprocessor/pragma-directives-and-the-pragma-keyword)。

## <a name="annotation-support"></a>註釋支援

註釋可改善程式碼分析的正確性。 註釋提供函式參數和傳回型別上前置和後置條件的其他資訊。 如需詳細資訊，請參閱 <<c0> [ 使用 SAL 註釋減少 C /C++程式碼缺失</c0>](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>執行分析工具作為簽入原則的一部分

您可能想要所有原始程式碼簽入都要滿足特定的原則。 尤其您會想要確認在最新本機建置步驟中已執行分析。 如需啟用程式碼分析簽入原則的詳細資訊，請參閱[建立和使用程式碼分析簽入原則](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Team Build 整合

您可以使用組建系統的整合式功能，在 [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] 建置程序的步驟中執行程式碼分析工具。 如需詳細資訊，請參閱 [Azure Pipelines](/azure/devops/pipelines/index?view=vsts)。

## <a name="see-also"></a>另請參閱

- [快速入門：適用於 C 的程式碼分析 /C++](quick-start-code-analysis-for-c-cpp.md)
- [逐步解說：分析 C /C++程式碼的缺失](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [C/C++ 程式碼分析警告](code-analysis-for-c-cpp-warnings.md)
- [使用 C++ Core Guidelines 檢查工具](using-the-cpp-core-guidelines-checkers.md)
- [C++核心指南檢查工具參考](code-analysis-for-cpp-corecheck.md)
- [使用規則集來指定要執行的 C++ 規則](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [使用程式碼分析工具分析驅動程式品質](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [程式碼分析驅動程式警告](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
