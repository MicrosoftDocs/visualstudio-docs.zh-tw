---
title: 探索界限 | Microsoft IntelliTest 開發人員測試工具
description: PexSettingsAttributeBase 是以屬性形式設定界限的抽象基底類別。 瞭解如何使用命名屬性來修改設定。
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Exploration bounds
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 713ccf139e4110923f45073308da2c249305eb18
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328895"
---
# <a name="exploration-bounds"></a>探索界限

**PexSettingsAttributeBase** 是以屬性形式設定界限的抽象基底類別。 請參閱[設定瀑布圖](settings-waterfall.md)，以取得 IntelliTest 中設定的概觀。

您可以使用此項目的具名屬性和其衍生屬性來修改設定：

```csharp
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **條件約束求解界限**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime) - [條件約束規劃求解](input-generation.md#constraint-solver)必須探索輸入的秒數，這將導致依循不同的新執行路徑。
  * [MaxConstraintSolverMemory](#maxconstraintsolvermemory) - [條件約束規劃求解](input-generation.md#constraint-solver)可能用來探索輸入的大小，以 MB 為單位。
* **探索路徑界限**
  * [MaxBranches](#maxbranches) - 可以在單一執行路徑中採用的分支數上限。
  * [MaxCalls](#maxcalls) - 可以在單一執行路徑期間發出的呼叫數上限。
  * [MaxStack](#maxstack) - 堆疊在單一執行路徑期間任何時候的大小上限，以使用中呼叫框架數來測量。
  * [MaxConditions](#maxconditions) - 單一執行路徑期間可以對輸入進行檢查的條件數上限。
* **探索界限**
  * [MaxRuns](#maxruns) - 探索期間將嘗試的執行數上限。
  * [MaxRunsWithoutNewTests](#maxrunswithoutnewtests) - 不發出新測試的連續執行數上限。
  * [MaxRunsWithUniquePaths](#maxrunswithuniquepaths) - 探索期間將嘗試唯一執行路徑的執行數上限。
  * [MaxExceptions](#maxexceptions) - 所有探索到之執行路徑的組合可找到的例外狀況數目上限。
* **測試套件程式碼產生設定**
  * [TestExcludePathBoundsExceeded](#testexcludepathboundsexceeded) - 設定為 true 時，會忽略超過任何路徑界限 ([MaxCalls](#maxcalls)、[MaxBranches](#maxbranches)、[MaxStack](#maxstack)、[MaxConditions](#maxconditions)) 的執行路徑。
  * [TestEmissionFilter](#testemissionfilter) - 指出 IntelliTest 應該在哪些情況下發出測試。
  * [TestEmissionBranchHits](#testemissionbranchhits) - 控制 IntelliTest 發出的測試數目。

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

[條件約束規劃求解](input-generation.md#constraint-solver)必須計算輸入的秒數，這將導致採用不同的新執行路徑。 這是 **>pexsettingsattributebase** 和其衍生類型的選項。

IntelliTest 對程式執行路徑探索得越深，IntelliTest 從程式的控制流程和資料流程建置的條件約束系統就會變得越複雜。 根據時間限制，您可以設定此值，以允許 IntelliTest 增加或減少探索新執行路徑的時間。

一般而言，逾時的原因是 IntelliTest 嘗試為其找出方案的條件約束系統沒有方案，但它並未發覺到這項事實。 由於這是發生逾時的最常見原因，因此增加界限可能沒有意義。

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

[條件約束規劃求解](input-generation.md#constraint-solver)必須計算輸入的 MB 數，這將導致採用不同的新執行路徑。 這是 *PexSettingsAttributeBase** 和其衍生類型的選項。

IntelliTest 對程式執行路徑的探索越深，IntelliTest 從程式的控制流程和資料流程建置的條件約束系統就會變得越複雜。 根據電腦可用的記憶體，您可以設定此值，以允許 IntelliTest 處理更複雜的條件約束系統。

一般而言，逾時的原因是 IntelliTest 嘗試為其找出方案的條件約束系統沒有方案，但它並未發覺到這項事實。 由於這是發生記憶體不足狀況的最常見原因，因增加界限可能沒有意義。

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

可以在單一執行路徑中採用的分支數上限。

這項探索界限背後的動機是要限制 IntelliTest 在[輸入產生](input-generation.md)期間探索到之任何執行路徑的長度。 特別是，如果程式進入無限迴圈，它會防止 IntelliTest 變成沒有回應。

每個已執行和受監視程式碼的條件式和無條件分支都會計入此限制，包括與參數化測試輸入不相依的分支。

例如，下列程式碼會依照 100 的順序取用分支：

```csharp
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>MaxCalls

可以在單一執行路徑期間發出的呼叫數上限。

這項探索界限背後的動機是要限制 IntelliTest 在[輸入產生](input-generation.md)期間探索到之任何執行路徑的長度。 特別是，如果程式以遞迴方式呼叫方法無限次數，因而造成 IntelliTest 無法從中復原的堆疊溢位時，它會防止 IntelliTest 變成沒有回應。

已執行和受監視程式碼的每個呼叫 (直接、間接、虛擬、跳躍) 都會計入這項限制。

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

堆疊在單一執行路徑期間任何時候的大小上限，以使用中呼叫框架數來測量。

這項探索界限背後的動機是要限制 IntelliTest 在[輸入產生](input-generation.md)期間探索到之任何執行路徑的堆疊大小。 特別是，它會防止 IntelliTest 使用所有可用的堆疊空間，這會造成 IntelliTest 無法從中復原的堆疊溢位。

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

單一執行路徑期間可以對輸入進行檢查的條件數上限。

這項探索界限的背後動機是要限制 IntelliTest 在[輸入產生](input-generation.md)期間探索到之任何執行路徑的複雜性。 每個與參數化測試輸入相依的條件式分支都會計入這項限制。

例如，下列程式碼中的每個路徑會取用 n + 1 條件：

```csharp
[PexMethod]
void ParameterizedTest(int n)
{
     for (int i=0; i<n; i++) { // conditions are "0<n", "1<n", ..., "!(n<n)"
          ...
     }
     for (int i=0; i<100; i++) { // irrelevant for MaxConditions, since conditions do not depend on input
          ...
     }
}
```

<a name="maxruns"></a>
## <a name="maxruns"></a>MaxRuns

IntelliTest 在測試探索期間將嘗試的執行數上限。

這項探索界限背後的動機是包含迴圈或遞迴的任何程式碼可能含有不限數目的執行路徑，因此 IntelliTest 必須在[輸入產生](input-generation.md)期間加以限制。

**MaxRuns** 和 **MaxRunsWithUniquePaths** 這兩項設定相關，如下所示：

* IntelliTest 將以不同的測試輸入呼叫參數化測試方法最多 **MaxRuns** 次。
* 如果已執行的程式碼具決定性，則 IntelliTest 會每次採用不同的執行路徑。 不過，在某些情況下，已執行的程式碼可能會以不同的輸入且依循它之前已採用的執行路徑。
* IntelliTest 會計算找到的唯一執行路徑數目；此數目是透過 **MaxRunsWithUniquePaths** 選項進行限制。

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

不發出新測試的連續執行數上限。

雖然 IntelliTest 通常在短時間內可以找到許多有趣的測試輸入，但在一段時間後，它找不到其他任何新的測試輸入，因此不再發出單元測試。 此組態選項會限定 IntelliTest 可能會執行的連續嘗試數目，而不發出新的測試。 到達此數目後，它將停止探索。

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

IntelliTest 在探索期間將考慮使用的唯一路徑數目上限。

這項探索界限背後的動機是包含迴圈或遞迴的任何程式碼可能含有不限數目的執行路徑，因此 IntelliTest 必須在[輸入產生](input-generation.md)期間加以限制。

**MaxRuns** 和 **MaxRunsWithUniquePaths** 這兩項設定相關，如下所示：

* IntelliTest 會呼叫參數化測試方法，最多可使用不同的測試輸入 **MaxRuns** 時間。
* 如果已執行的程式碼具決定性，則 IntelliTest 會每次採用不同的執行路徑。 不過，在某些情況下，已執行的程式碼可能會以不同的輸入且依循它之前已採用的執行路徑。
* IntelliTest 會計算找到的唯一執行路徑數目；此數目是透過 **MaxRunsWithUniquePaths** 選項進行限制。

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>MaxExceptions

在探索停止之前可能會遇到的例外狀況數目上限。

這項探索界限背後的動機是要停止探索包含許多錯誤的程式碼。 如果 IntelliTest 發現程式碼中有太多錯誤，即會停止探索。

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

會忽略超過設定的路徑界限 ([MaxCalls](#maxcalls)、[MaxBranches](#maxbranches)、[MaxStack](#maxstack) 和 [MaxConditions](#maxconditions)) 的執行路徑。

這項探索界限背後的動機是要處理 (可能的) 非終止測試。 當 IntelliTest 觸達探索界限 (例如 [MaxCalls](#maxcalls)、[MaxBranches](#maxbranches)、[MaxStack](#maxstack) 或 [MaxConditions](#maxconditions)) 時，它會假設測試不是非終止處理序，而且不會在稍後造成堆疊溢位。 這類測試案例可能會對其他測試架構造成問題，此屬性可用來防止 IntelliTest 發出潛在非終止處理序的測試案例或將造成堆疊溢位的測試案例。

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

指出 IntelliTest 應該發出的測試類型。 可能的值包括：

* **All** - 發出所有項目的測試，包括假設違規。
* **FailuresAndIncreasedBranchHits** (預設) - 針對所有的唯一失敗，以及每次測試案例增加 [TestEmissionBranchHits](#testemissionbranchhits) 所控制的涵蓋範圍時，發出測試。
* **FailuresAndUniquePaths** - 針對 IntelliTest 找到的所有失敗發出測試，同時也針對導致唯一執行路徑的每個測試輸入發出測試。
* **Failures** - 僅針對失敗發出測試。

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

根據目前的 [TestEmissionFilter](#testemissionfilter) 設定，IntelliTest 會在程式中涵蓋之前未涵蓋的分支時，發出新的測試案例。

**TestEmissionBranchHits** 設定可決定 IntelliTest 是否應該只考慮是否完全涵蓋分支 (**TestEmissionBranchHits = 1**)、測試是否涵蓋它一或兩次 (**TestEmissionBranchHits = 2**) 等等。

**TestEmissionBranchHits=1** 會產生非常小的測試套件，以涵蓋 IntelliTest 可能觸達的所有分支。 特別是，此測試套件也會涵蓋它已觸達的所有基本區塊和陳述式。

這個選項的預設值是 **TestEmissionBranchHits = 2**，它會產生更豐富多變的測試套件，同時也更適合用來偵測未來的迴歸錯誤。

## <a name="got-feedback"></a>有人給您意見嗎？

在[開發人員社群](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)上張貼您的意見與功能建議。
