---
title: IntelliTest 參考手冊 | Microsoft 開發人員測試工具
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest Reference Manual, IntelliTest
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c8db2e17f18d96f8d8b6c9eee3261c9329ece0b6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926914"
---
# <a name="intellitest-reference-manual"></a>IntelliTest 參考手冊

## <a name="contents"></a>內容

* **[IntelliTest 概觀](introduction.md)**
  - [IntelliTest 的 Hello World](introduction.md#the-hello-world-of-intellitest)
  - [限制](introduction.md#limitations)
    * [非決定性](introduction.md#nondeterminism)
    * [並行](introduction.md#concurrency)
    * [機器碼](introduction.md#native-code)
    * [平台](introduction.md#platform)
    * [Language](introduction.md#language)
    * [符號推理](introduction.md#symbolic-reasoning)
    * [不正確的堆疊追蹤](introduction.md#incorrect-stack-traces)
  - [進一步閱讀](introduction.md#further-reading)<p>&nbsp;</p>

* **[開始使用 IntelliTest](getting-started.md)**
  - [重要屬性](getting-started.md#important-attributes)
  - [重要靜態協助程式類別](getting-started.md#helper-classes)<p>&nbsp;</p>

* **[測試產生](test-generation.md)**
  - [測試產生](test-generation.md#test-generators)
  - [參數化單元測試](test-generation.md#parameterized-unit-testing)
  - [一般參數化單元測試](test-generation.md#generic-parameterized)
  - [允許例外狀況](test-generation.md#allowing-exceptions)
  - [測試內部類型](test-generation.md#internal-types)
  - [假設和判斷提示](test-generation.md#assumptions-and-assertions)
  - [先決條件](test-generation.md#precondition)
  - [後置條件](test-generation.md#postcondition)
  - [測試失敗](test-generation.md#test-failures)
  - [設定和卸除](test-generation.md#setup-teardown)
  - [進一步閱讀](test-generation.md#further-reading)<p>&nbsp;</p>

* **[輸入產生](input-generation.md)**
  - [限制式求解](input-generation.md#constraint-solver)
  - [動態程式碼涵蓋範圍](input-generation.md#dynamic-code-coverage)
  - [整數與浮點數](input-generation.md#integers-and-floats)
  - [物件](input-generation.md#objects)
  - [現有類別具現化](input-generation.md#existing-classes)
  - [可見度](input-generation.md#visibility)
  - [參數化模擬](input-generation.md#parameterized-mocks)
  - [結構](input-generation.md#structs)
  - [陣列和字串](input-generation.md#arrays-and-strings)
  - [取得其他輸入](input-generation.md#additional-inputs)
  - [進一步閱讀](input-generation.md#further-reading)<p>&nbsp;</p>

* **[探索界限](exploration-bounds.md)**
  - [MaxConstraintSolverTime](exploration-bounds.md#maxconstraintsolvertime)
  - [MaxConstraintSolverMemory](exploration-bounds.md#maxconstraintsolvermemory)
  - [MaxBranches](exploration-bounds.md#maxbranches)
  - [MaxCalls](exploration-bounds.md#maxcalls)
  - [MaxStack](exploration-bounds.md#maxstack)
  - [MaxConditions](exploration-bounds.md#maxconditions)
  - [MaxRuns](exploration-bounds.md#maxruns)
  - [MaxRunsWithoutNewTests](exploration-bounds.md#maxrunswithoutnewtests)
  - [MaxRunsWithUniquePaths](exploration-bounds.md#maxrunswithuniquepaths)
  - [MaxExceptions](exploration-bounds.md#maxexceptions)
  - [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded)
  - [TestEmissionFilter](exploration-bounds.md#testemissionfilter)
  - [TestEmissionBranchHits](exploration-bounds.md#testemissionbranchhits)<p>&nbsp;</p>

* **[屬性字彙](attribute-glossary.md)**
  - [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull)
  - [PexClass](attribute-glossary.md#pexclass)
  - [PexGenericArguments](attribute-glossary.md#pexgenericarguments)
  - [PexMethod](attribute-glossary.md#pexmethod)
  - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)
  - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
  - [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest)
  - [PexInstrumentAssemblyAttribute](attribute-glossary.md#pexinstrumentassemblyattribute)
  - [PexUseType](attribute-glossary.md#pexusetype)
  - [PexAllowedException](attribute-glossary.md#pexallowedexception)
  - [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly)
  - [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype)
  - [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest)<p>&nbsp;</p>

* **[設定瀑布圖](settings-waterfall.md)**

* **[靜態協助程式類別](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)<p>&nbsp;</p>

* **[警告與錯誤](warnings-and-errors.md)**
  - [超過 MaxBranches](warnings-and-errors.md#maxbranches-exceeded)
  - [超過 MaxConstraintSolverTime](warnings-and-errors.md#maxconstraintsolvertime-exceeded)
  - [超過 MaxConditions](warnings-and-errors.md#maxconditions-exceeded)
  - [超過 MaxCalls](warnings-and-errors.md#maxcalls-exceeded)
  - [超過 MaxStack](warnings-and-errors.md#maxstack-exceeded)
  - [超過 MaxRuns](warnings-and-errors.md#maxruns-exceeded)
  - [超過 MaxRunsWithoutNewTests](warnings-and-errors.md#maxrunswithoutnewtests-exceeded)
  - [無法將解決方案實體化](warnings-and-errors.md#cannot-concretize-solution)
  - [需要協助以建構物件](warnings-and-errors.md#help-construct)
  - [需要協助以尋找類型](warnings-and-errors.md#help-types)
  - [猜到可使用的類型](warnings-and-errors.md#usable-type-guessed)
  - [在探索期間發生未預期的失敗](warnings-and-errors.md#unexpected-exploration)
  - [TargetInvocationException](warnings-and-errors.md#targetinvocationexception)
  - [呼叫了未經檢測的方法](warnings-and-errors.md#uninstrumented-method-called)
  - [呼叫了外部方法](warnings-and-errors.md#external-method-called)
  - [呼叫了無法檢測的方法](warnings-and-errors.md#uninstrumentable-method-called)
  - [可測試性問題](warnings-and-errors.md#testability-issue)
  - [限制](warnings-and-errors.md#limitation)
  - [觀察到呼叫不相符](warnings-and-errors.md#observed-call-mismatch)
  - [儲存在靜態欄位的值](warnings-and-errors.md#value-static-field)<p>&nbsp;</p>

## <a name="got-feedback"></a>有任何意見反應嗎？

在[開發人員社群](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)上張貼您的意見與功能建議。