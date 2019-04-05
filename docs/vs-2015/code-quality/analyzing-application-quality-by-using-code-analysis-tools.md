---
title: 使用程式碼分析工具分析應用程式品質 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.analysisresults
helpviewer_keywords:
- application quality, analyzing
- code analysis
- team-based development, analyzing application quality
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 83fbe8b372d021e0cec4faccfd0b22fcaa8af30d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "59000544"
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>使用程式碼分析工具進行應用程式品質分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本節內容  
 [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)  
 Managed 程式碼的 Visual Studio 程式碼分析會提供 Managed 組件的相關資訊，例如是否違反 Microsoft .NET Framework 設計方針所制定的程式設計和設計規則。 警告訊息會識別任何相關的程式設計和設計問題，並且在可能的時候，提供如何修正問題的資訊。  
  
 [使用程式碼分析進行 C/C++ 程式碼品質分析](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md)  
 C/C++ 程式碼分析工具會將其 C/C++ 原始程式碼中可能的缺失相關資訊提供給開發人員。 這個工具所報告的常見程式碼撰寫錯誤包括緩衝區滿溢、未初始化的記憶體、Null 指標取值以及記憶體和資源流失。  
  
 [使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)  
 選取和建立*規則集*来套用至您的專案。  
  
 [程式碼分析應用程式錯誤](../code-quality/code-analysis-application-errors.md)  
 修正程式碼分析功能中的錯誤。  
  
 [使用 Team 專案簽入原則強化程式碼品質](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)  
 當您使用 Team Foundation 版本控制 (TFVC) 時，您可以針對 Team 專案建立簽入原則，該原則會強制執行做法，導致更好的程式碼和更有效率的群組開發。 簽入原則是在 Team 專案層級設定的規則，而且會在允許程式碼簽入之前，於開發人員電腦上強制執行。  
  
### <a name="code-analysis-for-drivers"></a>驅動程式程式碼分析  
 程式碼分析工具可以協助改進您的驅動程式的穩定性和可靠性，方法是有系統地分析驅動程式原始程式碼。  
  
 [使用程式碼分析工具程式驅動程式品質分析](/windows-hardware/drivers/devtest/tools-for-verifying-drivers)  
 驅動程式的程式碼分析是編譯時間靜態驗證工具，可偵測的基本程式碼在 C 和 c + + 程式中的錯誤，並包含特殊的模組是設計用來偵測 （主要） 核心模式驅動程式程式碼中的錯誤。 靜態驅動程式驗證器 (SDV) 是一種靜態驗證工具，有系統地分析 Windows 核心模式驅動程式的原始程式碼。 SDV 會判斷驅動程式是否正確地與 Windows 作業系統核心互動。  
  
 [程式碼分析驅動程式警告](http://go.microsoft.com/fwlink/?LinkId=225920)  
 描述驅動程式之程式碼分析在偵測到驅動程式程式碼中可能阿生的錯誤時，所報告的警告。  
  
## <a name="related-tasks"></a>相關工作  
 [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)  
 在這裡插入說明。  
  
 [對程式碼進行單元測試](../test/unit-test-your-code.md)  
 在這裡插入說明。
