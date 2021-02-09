---
title: 程式碼計量-類別結合
ms.date: 1/8/2021
description: 瞭解 Visual Studio 中程式碼度量的類別結合計量。
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f8320c460faf7532887364693080d38c0ff6baa6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860512"
---
# <a name="code-metrics---class-coupling"></a>程式碼計量-類別結合

類別結合也會以物件之間的名稱結合 (CBO) ，如同 [CK94](#ck94)的原始定義。 基本上，類別結合是單一類別使用的類別數目的量值。 較高的數位很差，而且此計量通常很適合使用較低的數位。 類別結合已顯示為軟體失敗的精確預測，而最近的研究顯示，上限值9是最有效率的 [S2010](#s2010)。

根據 Microsoft 檔，「類別結合」會透過參數、區域變數、傳回型別、方法呼叫、泛型或樣板具現化、基類、介面實現、在外部類型上定義的欄位，以及屬性裝飾來測量與唯一類別的結合。 良好的軟體設計會指出類型和方法應該具有高一致性和低耦合。 高度結合表示很難重複使用和維護的設計，因為它在其他類型上有許多相關性。」

結合和一致性的概念清楚相關。 為了在主題中進行這段討論，除了從 [KKLS2000](#kkls2000)提供短暫的定義外，我們也不會深入瞭解一致性：

「Module 一致性是由 Yourdon 和 Constantine 所引進，「模組的內部元素緊密系結或相關的內部元素彼此之間的緊密系結」 [YC79](#yc79)。 如果模組只代表一個工作 [...]，且其所有元素都參與這個單一工作，則模組具有強式一致性。 它們會將一致性描述為設計的屬性，而非程式碼，以及可用來預測重複使用性、可維護性和 changeability 的屬性。

## <a name="class-coupling-example"></a>類別結合範例

讓我們來看看類別結合的作用。 首先，建立新的主控台應用程式，並建立名為 Person 的新類別，並在其中建立一些屬性，然後立即計算程式碼度量：

![類別結合範例1](media/class-coupling-example-1.png)

請注意，類別結合性是0，因為此類別不會使用任何其他類別。 現在，使用可建立 Person 實例並設定屬性值的方法，建立另一個名為 PersonStuff 的類別。 再次計算程式碼度量：

![類別結合範例2](media/class-coupling-example-2.png)

查看類別結合值的運作方式為何？ 也請注意，無論您設定多少屬性，類別結合值只會出現1，而不是其他值。 類別結合量值只會針對此計量測量每個類別一次，不論使用的數量為何。 此外，您可以看到它的值是1，但函式的 `DoSomething()` `PersonStuff()` 值是0嗎？ 目前，使用另一個類別的函式中沒有任何程式碼。

如果您將程式碼放在使用另一個類別的函式中，該怎麼辦？ 以下是您取得的內容：

![類別結合範例3](media/class-coupling-example-3.png)

現在，此函式清楚地有使用另一個類別的程式碼，而類別結合性度量則顯示此事實。 同樣地，您可以看到的整體類別結合為 `PersonStuff()` 1，而且 `DoSomething()` 也是1來顯示，無論您有多少內部程式碼使用它，都只會使用一個外部類別。

接下來，建立另一個新類別。 提供此類別的一些名稱，並在其中建立一些屬性：

![類別結合範例-加入新類別](media/class-coupling-example-add-new-class.png)

現在會在類別內的方法中取用類別 `DoSomething()` `PersonStuff` ，然後再次計算程式碼度量：

![類別結合範例4](media/class-coupling-example-4.png)

如您所見，PersonStuff 類別的類別結合程度最高可達2，而如果您向下切入至類別，您可以看到該 `DoSomething()` 方法在其中有最多的聯繫性，但是此函式仍只取用1個類別。  您可以使用這些計量來查看指定類別的整體最大數目，並深入瞭解每個成員的詳細資料。

## <a name="the-magic-number"></a>魔術數位

如同迴圈複雜度，沒有適合所有組織的限制。 不過， [S2010](#s2010) 會指出限制為9的最佳：

「因此，我們考慮臨界值 [...]最有效的。  (單一成員) 的這些閾值是 CBO = 9 [...]。  (強調新增) 

## <a name="code-analysis"></a>程式碼分析

程式碼分析包含可維護性規則的類別。 如需詳細資訊，請參閱可 [維護性規則](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings)。 使用舊版程式碼分析時，延伸的設計指導方針規則集包含可維護性區域：

![類別結合擴充設計指導方針規則](media/class-coupling-extended-design-guideline-rules.png)

可維護性區域內的規則適用于類別結合：

![類別結合規則](media/class-coupling-maintainability-area-rules.png)

當類別結合過度時，此規則會發出警告。 如需詳細資訊，請參閱 [CA1506：避免過度的類別](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)結合。

如需這項規則的描述，請參閱「封存的程式碼分析」 blog 文章：在80的「 [簽入原則](/archive/blogs/codeanalysis/code-metrics-as-check-in-policy) 」和「在上的臨界值描述警告」（適用于類別），以及 *高於30的方法*。  這些值看起來很高，但至少提供極大的上限。 如果您遇到這個警告，就表示有一些問題。

## <a name="citations"></a>引文

### <a name="ck94"></a>CK94

Chidamber，S. R。 & Kemerer，c. F。  (1994) 。 適用于物件導向設計的計量套件 (軟體工程上的 IEEE 交易，Vol. 20，否。 6) 。 從 Pittsburgh 網站的大學的2011月14日取出： [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="kkls2000"></a>KKLS2000

Kabaili、.H、Keller、R.、Lustman、F 和聖 Denis、g. (2000) 。 一致性的課堂研究：業界系統的經驗研究 (在 Object-Oriented 軟體工程) 的量化方法上進行的調查。 從 Université de Montréal 網站取出2011年5月20日 [http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf](http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf)

### <a name="sk2003"></a>SK2003

Subramanyam、R. & Krishnan、M. S。 (2003)。 針對 Object-Oriented 設計複雜性的 CK 計量經驗分析：軟體缺失 (IEEE 交易的軟體工程 4) 。 從麻塞諸塞州 Dartmouth-hitchcock 網站的大學（2011）取出 [http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf](http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf)

### <a name="s2010"></a>S2010

Shatnawi， (2010) 。 Open-Source 系統中 Object-Oriented 計量的可接受風險層級的量化調查 (軟體工程上的 IEEE 交易、36、否。 2) 。

### <a name="yc79"></a>YC79

Edward Yourdon 和 Larry L. Constantine。 結構化設計。 Prentice 廳、Englewood 懸崖、N.J.、1979。