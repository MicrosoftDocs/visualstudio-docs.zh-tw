---
title: 程式碼度量-繼承深度
ms.date: 1/8/2021
description: 瞭解 Visual Studio 中程式碼度量的繼承度量深度。
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1d6ac085463087fc73aac4429488ab475e91c10f
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2021
ms.locfileid: "109682639"
---
# <a name="code-metrics---depth-of-inheritance-dit"></a>程式碼度量-繼承 (DIT 的深度) 

在本文中，您將瞭解專為物件導向分析而設計的其中一個計量：繼承深度。 繼承深度（也稱為繼承樹狀結構 (DIT) 的深度）定義為「從節點到樹狀結構的根的最大長度」 [CK](#ck)。 您可以使用簡單的範例來查看。 建立新的類別庫專案，在撰寫任何程式碼之前，請選擇 [分析] **> 計算方案的程式碼度量，以** 計算程式碼的度量。

![繼承的深度範例1](media/depth-of-inheritance-example-1.png)

由於所有類別都是繼承自 `System.Object` ，因此目前的深度為1。 如果您繼承自這個類別並檢查新的類別，您可以看到結果：

![繼承深度範例2](media/depth-of-inheritance-example-2.png)

請注意，樹狀結構中的節點越低 (`Class2` 在此案例中) ，繼承深度愈高。 您可以繼續建立子系，並使深度增加到您想要的程度。

## <a name="assumptions"></a>假設

繼承深度的前提在三個基本假設上 [CK](#ck)：

1. 階層中更深入的類別，它可能會繼承的方法數目愈大，這會讓您難以預測其行為。

2. 更深入的樹狀結構牽涉到更大的設計複雜性，因為牽涉到更多類別和方法。

3. 樹狀結構中的更深層類別在重複使用繼承的方法時有更大的潛力。

假設1和2表示深度較高的數位不正確。 如果這是結束的地方，您會是不錯的圖形;不過，假設3表示較高的深度數目適合可能的程式碼重複使用。

## <a name="analysis"></a>分析

以下是您讀取深度度量的方式：

- 深度較低的數位

  較低的深度表示較低的複雜度，但也可以透過繼承減少程式碼重複使用的可能性。

- 深度較高的數位

  較高的深度表示更有可能透過繼承來重複使用程式碼，但在程式碼中的錯誤機率較高時，也會有較高的複雜度。

## <a name="code-analysis"></a>程式碼分析

程式碼分析包含可維護性規則的類別。 如需詳細資訊，請參閱可 [維護性規則](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings)。 使用舊版程式碼分析時，延伸的設計指導方針規則集包含可維護性區域：

![繼承設計指導方針規則集的深度](media/depth-of-inheritance-design-guidelines.png)

在可維護性區域內是繼承的規則：

![繼承可維護性規則的深度](media/depth-of-inheritance-maintainability-rule.png)

當繼承深度達到6（或更高）時，此規則會發出警告，因此這是有助於防止過度繼承的良好規則。 若要深入瞭解規則，請參閱 [CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501)。

## <a name="putting-it-all-together"></a>把它全部放在一起

最高的 DIT 值表示可能發生錯誤的可能性也很高，低值則可減少錯誤的可能性。 最高的 DIT 值表示更有可能透過繼承來重複使用程式碼，低值則透過繼承以利用，建議較少的程式碼重複使用。 由於沒有足夠的資料，因此目前無法接受 DIT 值的標準。 最近所做的研究找不到足夠的資料來判斷可用來作為此計量 [Shatnawi](#shatnawi)標準數位的可用數位。 雖然沒有經驗辨識項可支援它，但有數個資源會建議大約5或6的 DIT 應為上限。 例如，請參閱 [http://www.devx.com/architect/Article/45611](http://www.devx.com/architect/Article/45611) 。

## <a name="citations"></a>引文

### <a name="ck"></a>CK

Chidamber，S. R。 & Kemerer，c. F。  (1994) 。 適用于物件導向設計的計量套件 (軟體工程上的 IEEE 交易，Vol. 20，否。 6) 。 從 Pittsburgh 網站的大學的2011月14日取出： [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="krishnan"></a>Krishnan

Subramanyam、R. & Krishnan、M. S。 (2003)。 針對 Object-Oriented 設計複雜性的 CK 計量經驗分析：軟體缺失 (IEEE 交易的軟體工程 4) 。 從2011月14日取出，最初是從麻塞諸塞州 Dartmouth-hitchcock 網站的大學取得 [https://ieeexplore.ieee.org/abstract/document/1191795](https://ieeexplore.ieee.org/abstract/document/1191795)

### <a name="shatnawi"></a>Shatnawi

Shatnawi， (2010) 。 Open-Source 系統中 Object-Oriented 計量的可接受風險層級的量化調查 (軟體工程上的 IEEE 交易、36、否。 2) 。