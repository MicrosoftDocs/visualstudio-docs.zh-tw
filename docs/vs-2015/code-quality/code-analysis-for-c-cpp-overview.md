---
title: 程式碼分析，如 C + + 的概觀 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 27
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 42de573efcc44437eddf0e7d098681d05c094131
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222036"
---
# <a name="code-analysis-for-cc-overview"></a>C/C++ 程式碼分析概觀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C/C++ 程式碼分析工具會將其 C/C++ 原始程式碼中可能的缺失相關資訊提供給開發人員。 這個工具所報告的常見程式碼撰寫錯誤包括緩衝區滿溢、未初始化的記憶體、Null 指標取值以及記憶體和資源流失。  
  
## <a name="ide-integrated-development-environment-integration"></a>IDE (整合式開發環境) 整合  
 為了更方便的開發人員分析工具的用法，它完全整合在[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]IDE。 在建置過程中，所產生的原始碼的警告會出現在 錯誤清單。 您可以瀏覽至造成警告的原始程式碼，而且您可以檢視的原因和可能的解決方案，此問題的其他資訊。  
  
## <a name="pragma-support"></a>#pragma 支援  
 開發人員可以使用`#pragma`指示詞，以將警告視為錯誤; 啟用或停用警告，並隱藏個別的程式碼行警告。 如需詳細資訊，請參閱 <<c0> [ 如何： 啟用和停用 C/c + + 的特定警告的程式碼分析](http://msdn.microsoft.com/en-us/910b8518-71f1-4b2e-b012-70647795642a)。  
  
## <a name="annotation-support"></a>註釋支援  
 註解改善程式碼分析的正確性。 註釋函式參數上提供前置和後置條件的其他資訊，並傳回型別。 如需詳細資訊，請參閱[How to： 使用 __analysis_assume 指定其他的程式碼資訊](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>簽入原則的一部分執行分析工具  
 您可以在需要所有來源的程式碼簽入都滿足特定的原則。 特別是，您會想要確定步驟中的最新的本機組建已執行分析。 如需啟用程式碼分析簽入原則的詳細資訊，請參閱[建立和使用程式碼分析簽入原則](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Team Build 整合  
 您可以使用建置系統的整合式的功能的步驟執行程式碼分析工具[!INCLUDE[esprtfs](../includes/esprtfs-md.md)]建置程序。 如需詳細資訊，請參閱[建置應用程式](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)。  
  
## <a name="command-line-support"></a>命令列支援  
 除了在開發環境中完整的整合，開發人員也可以使用分析工具，從命令列中，如下列範例所示：  
  
 `C:\>cl /analyze Sample.cpp`



