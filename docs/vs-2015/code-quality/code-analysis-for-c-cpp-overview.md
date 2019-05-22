---
title: C-C++ 程式碼分析概觀 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
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
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: fce0fb33f6c536386754b10b11e724a603f0a2a6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698007"
---
# <a name="code-analysis-for-cc-overview"></a>C/C++ 程式碼分析概觀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C/C++ 程式碼分析工具會將其 C/C++ 原始程式碼中可能的缺失相關資訊提供給開發人員。 這個工具所報告的常見程式碼撰寫錯誤包括緩衝區滿溢、未初始化的記憶體、Null 指標取值以及記憶體和資源流失。  
  
## <a name="ide-integrated-development-environment-integration"></a>IDE (整合式開發環境) 整合  
 為了讓開發人員自然地使用分析工具，它已完全整合到 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 中。 在建置程序期間，任何針對原始程式碼所產生的警告都會出現在 [錯誤清單] 中。 您可以巡覽至造成警告的原始程式碼，也可以檢視問題原因和可能解決方法的其他資訊。  
  
## <a name="pragma-support"></a>#pragma 支援  
 開發人員可以使用 `#pragma` 指示詞來將警告視為錯誤、啟用或停用警告，以及隱藏個別程式碼行的警告。 如需詳細資訊，請參閱[如何：Enable and Disable Code Analysis for Specific C/C++ Warnings](https://msdn.microsoft.com/910b8518-71f1-4b2e-b012-70647795642a) (如何：啟用和停用特定 C/C++ 警告的程式碼分析)。  
  
## <a name="annotation-support"></a>註釋支援  
 註釋可改善程式碼分析的正確性。 註釋提供函式參數和傳回型別上前置和後置條件的其他資訊。 如需詳細資訊，請參閱[如何：使用 __analysis_assume 來指定其他程式碼資訊](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>執行分析工具作為簽入原則的一部分  
 您可能想要所有原始程式碼簽入都要滿足特定的原則。 尤其您會想要確認在最新本機建置步驟中已執行分析。 如需啟用程式碼分析簽入原則的詳細資訊，請參閱[建立和使用程式碼分析簽入原則](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Team Build 整合  
 您可以使用組建系統的整合式功能，在 [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] 建置程序的步驟中執行程式碼分析工具。 如需詳細資訊，請參閱[建置應用程式](https://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)。  
  
## <a name="command-line-support"></a>命令列支援  
 除了開發環境內的完整支援，開發人員也可以從命令列使用分析工具，如下列範例所示：  
  
 `C:\>cl /analyze Sample.cpp`
