---
title: 使用程式碼分析工具來分析應用程式品質 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c0b46c8efb681a067d5a9e74369ed73c43f1568f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671096"
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>使用程式碼分析工具進行應用程式品質分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在本節中，分析受控碼的[managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)Visual Studio 程式碼分析會提供 managed 元件的相關資訊，例如違反 Microsoft .NET Framework 設計中所設定的程式設計和設計規則。規定. 警告訊息會識別任何相關的程式設計和設計問題，並且在可能的時候，提供如何修正問題的資訊。

 [使用程式碼C++分析來分析 c/程式碼品質：](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md) c/C++程式碼分析工具可為開發人員提供有關其 CC++ /原始程式碼可能缺失的資訊。 這個工具所報告的常見程式碼撰寫錯誤包括緩衝區滿溢、未初始化的記憶體、Null 指標取值以及記憶體和資源流失。

 [使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)選取並建立要套用至專案的*規則集*。

 [程式碼分析應用程式錯誤](../code-quality/code-analysis-application-errors.md)修正程式碼分析功能中的錯誤。

 [使用 Team 專案簽入原則強化程式碼品質](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)當您使用 Team Foundation 版本控制（TFVC）時，您可以為 Team 專案建立簽入原則，強制執行會導致更好的程式碼和更有效率的群組開發的做法。 簽入原則是在 Team 專案層級設定的規則，而且會在允許程式碼簽入之前，於開發人員電腦上強制執行。

### <a name="code-analysis-for-drivers"></a>驅動程式程式碼分析
 程式碼分析工具可以協助改進您的驅動程式的穩定性和可靠性，方法是有系統地分析驅動程式原始程式碼。

 [使用程式碼分析工具分析驅動程式品質](/windows-hardware/drivers/devtest/tools-for-verifying-drivers)驅動程式的程式碼分析是一個編譯時期靜態驗證工具，它會偵測 C 和C++程式中的基本編碼錯誤，並包含專門設計的模組，可在（主要是）核心模式驅動程式程式碼中偵測到錯誤。 靜態驅動程式驗證器 (SDV) 是一種靜態驗證工具，有系統地分析 Windows 核心模式驅動程式的原始程式碼。 SDV 會判斷驅動程式是否正確地與 Windows 作業系統核心互動。

 [驅動程式的程式碼分析警告](http://go.microsoft.com/fwlink/?LinkId=225920)描述當驅動程式在偵測到驅動程式代碼中可能發生的錯誤時，所報告的程式碼分析警告。

## <a name="related-tasks"></a>相關工作
 [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)在此插入描述。

 [對程式碼進行單元測試](../test/unit-test-your-code.md)在此插入描述。
