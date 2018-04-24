---
title: C/C++ 程式碼分析概觀
ms.date: 11/04/2016
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
ms.openlocfilehash: 4068b4956d0337a3b3c46693b54b0df165439a7f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="code-analysis-for-cc-overview"></a>程式碼分析 C/c + + 的概觀

C/C++ 程式碼分析工具會將其 C/C++ 原始程式碼中可能的缺失相關資訊提供給開發人員。 這個工具所報告的常見程式碼撰寫錯誤包括緩衝區滿溢、未初始化的記憶體、Null 指標取值以及記憶體和資源流失。

## <a name="ide-integrated-development-environment-integration"></a>IDE (整合式開發環境) 整合
 若要讓自然適用於開發人員分析工具的用法，它會完整地整合在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]IDE。 建置程序期間所產生的原始碼的警告會出現在錯誤清單。 您可以瀏覽至造成警告的原始程式碼，您可以檢視有關原因和可能的解決方案，問題的其他資訊。

## <a name="pragma-support"></a>#pragma 支援
 開發人員可以使用`#pragma`指示詞，以將警告視為錯誤; 啟用或停用警告，並隱藏個別的程式碼行的警告。 如需詳細資訊，請參閱[How to: C/c + + 專案設定程式碼分析屬性](how-to-set-code-analysis-properties-for-c-cpp-projects.md)。

## <a name="annotation-support"></a>附註支援
 註解改善程式碼分析的精確度。 註釋提供前置和後置條件的其他資訊在函式參數和傳回型別。 如需詳細資訊，請參閱[How to： 使用 __analysis_assume 指定其他的程式碼資訊](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>簽入原則的一部分執行分析工具
 您可以在需要所有來源的程式碼簽入都滿足特定的原則。 特別是，您會想要確定在步驟中的最新的本機組建已執行分析。 如需啟用程式碼分析簽入原則的詳細資訊，請參閱[建立和使用程式碼分析簽入原則](../code-quality/creating-and-using-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Team Build 整合
 您可以使用建置系統的整合式的功能的步驟執行程式碼分析工具[!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]建置程序。 如需詳細資訊，請參閱[建置及發行](/vsts/build-release/index)。

## <a name="command-line-support"></a>命令列支援
 除了在開發環境中完整的整合，開發人員也可以使用分析工具，從命令列中，如下列範例所示：

 `C:\>cl /analyze Sample.cpp`

## <a name="see-also"></a>另請參閱

[使用程式碼分析工具進行驅動程式品質](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
[驅動程式警告的程式碼分析](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)