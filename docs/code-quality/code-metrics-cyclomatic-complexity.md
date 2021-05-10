---
title: 程式碼度量-迴圈複雜度
ms.date: 5/7/2021
description: 瞭解 Visual Studio 中的程式碼度量的圈複雜度度量。
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1798b0faa1b0cf44ae490f5b27571e5466b82ca9
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2021
ms.locfileid: "109682637"
---
# <a name="code-metrics---cyclomatic-complexity"></a>程式碼度量-迴圈複雜度

使用程式碼度量時，其中一個最不了解的專案似乎是迴圈複雜度。 基本上，在迴圈複雜度的情況下，較高的數位是不良的，而較低的數位則很好 您可以使用迴圈複雜性來瞭解任何程式碼可能測試、維護或疑難排解的難度，以及指出程式碼可能產生錯誤的可能性。 概括而言，我們會計算在原始程式碼中所做的決策數目，藉以判斷迴圈複雜度的價值。 在本文中，您將從簡單的迴圈複雜度範例開始著手，以快速瞭解此概念，然後查看有關實際使用量和建議限制的其他資訊。 最後，有一個引文區段可以用來深入探討這個主題。

## <a name="example"></a>範例

迴圈複雜度的定義是測量「原始程式碼函式中的決策邏輯數量」 [NIST235](#nist235)。 簡單地說，在程式碼中所需的決策愈多，就愈複雜。

讓我們來看看它的運作方式。 建立新的主控台應用程式，並立即計算您的程式碼計量，方法是前往 [ **分析 > 計算方案的程式碼度量**]。

![圈複雜度範例1](media/cyclomatic-complexity-example-1.png)

請注意，迴圈複雜度為 2 (可能的最小值) 。 如果您新增非決策碼，請注意複雜性不會改變：

![圈複雜度範例2](media/cyclomatic-complexity-example-2.png)

如果您加入決策，則圈複雜度值會出現1：

![圈複雜度範例3](media/cyclomatic-complexity-example-3.png)

當您將 if 語句變更為具有4個決策的 switch 語句時，它會從原始的2到6進行轉換：

![迴圈複雜度範例4](media/cyclomatic-complexity-example-4.png)

讓我們看看 (假設) 較大的程式碼基底。

![圈複雜度範例5](media/cyclomatic-complexity-example-5.png)

請注意，當您向下切入 Products_Related 類別時，大部分專案的值為1，但其中有幾個值的複雜度為5。 這可能不是很大的問題，但是假設大部分的其他成員在同一個類別中都有一個1，您應該仔細查看這兩個專案，並查看其中的內容。 您可以用滑鼠右鍵按一下專案，然後從內容功能表中選擇 [ **移至原始程式碼** ]。 請仔細查看 `Product.set(Product)` ：

![圈複雜度範例6](media/cyclomatic-complexity-example-6.png)

假設有所有 if 語句，您就可以看到迴圈複雜度為5的原因。 至此，您可能會決定這是可接受的複雜度層級，或者您可能會重構以降低複雜度。

## <a name="the-magic-number"></a>魔術數位

如同此產業中的許多計量，沒有適用于所有組織的精確圈複雜度限制。 不過， [NIST235](#nist235) 會指出限制為10個良好的起點：

不過，要做為限制的精確數位仍會有點有爭議。 McCabe 所提議的原始限制為10個重要的支援辨識項，但高達15的限制也已成功使用。 超過10個的限制應該保留給有數個作業優勢的專案，例如經驗豐富的員工、正式設計、新式程式設計語言、結構化程式設計、程式碼逐步解說，以及全方位的測試計劃。 換句話說，組織可以挑選大於10的複雜性限制，但只有在確定它知道它的執行情況，而且願意投入更複雜的模組所需的額外測試工作。」 [NIST235](#nist235)

## <a name="cyclomatic-complexity-and-line-numbers"></a>圈複雜度和行號

只要查看程式碼的行數，就能以非常廣泛的方式預測程式碼品質。 有一些基本的概念，就是函式中的程式程式碼越多，就越有可能發生錯誤。 但是，當您將迴圈複雜性與程式程式碼結合時，就會有更清楚的可能發生錯誤的圖片。

如軟體保證技術中心所述 (SATC) NASA：

「SATC 發現最有效的評估是大小和 (圈) 複雜性的組合。 具有高複雜性和大型大小的模組，通常會具有最低的可靠性。 大小低和高複雜性的模組也會有可靠性風險，因為它們通常是非常簡易的程式碼，這很難變更或修改。」 [SATC](#satc)

## <a name="code-analysis"></a>程式碼分析

程式碼分析包含可維護性規則的類別。 如需詳細資訊，請參閱可 [維護性規則](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings)。 使用舊版程式碼分析時，延伸的設計指導方針規則集包含可維護性區域：

![圈複雜度設計指導方針規則集](media/cyclomatic-complexity-design-guidelines.png)

在可維護性區域內是複雜性的規則：

![圈複雜度維護規則](media/cyclomatic-complexity-maintainability-rule.png)

當圈複雜度達到25時，此規則會發出警告，因此可協助您避免過度複雜。 若要深入瞭解規則，請參閱 [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)

## <a name="putting-it-all-together"></a>把它全部放在一起

重點是，高複雜性的數位表示較高的錯誤機率，以及更多的維護和疑難排解時間。 深入瞭解具有高複雜性的函式，並決定是否應重構它們，使其變得較不復雜。

## <a name="citations"></a>引文

### <a name="mccabe5"></a>MCCABE5

McCabe、T. 和 Watson (1994) 、軟體複雜性 (CrossTalk：國防軟體工程) 的日誌。

### <a name="nist235"></a>NIST235

Watson、.H、& McCabe、T. J。  (1996) 。 結構化測試：使用「圈複雜度」度量的測試方法 (NIST 特殊發行 500-235) 。 從 McCabe Software 網站取出的2011：5月14日： [http://www.mccabe.com/pdf/mccabe-nist235r.pdf](http://www.mccabe.com/pdf/mccabe-nist235r.pdf)

### <a name="satc"></a>SATC

Rosenberg、L.、鐵錘、T.、Shaw、J. (1998) 。 軟體可靠性工程) 上 IEEE 國際 Symposium 的軟體計量和可靠性 (訴訟。 從 >penn 州大學網站取出2011：5月14日： [http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf)