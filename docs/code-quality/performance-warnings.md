---
title: 效能警告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- warnings, performance
- performance warnings
- performance, warnings
- managed code analysis warnings, performance warnings
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3fc631a2a99dd6090893393ee20ecec23945713
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814916"
---
# <a name="performance-warnings"></a>效能警告
效能警告支援高效能程式庫和應用程式。

## <a name="in-this-section"></a>本節內容

| 規則 | 描述 |
| - | - |
| [CA1800:不要執行不必要的轉換](../code-quality/ca1800.md) | 重複轉型會降低效能，尤其是在精簡型態的反覆運算陳述式中執行轉型時。 |
| [CA1801:必須檢閱未使用的參數](../code-quality/ca1801.md) | 方法簽章包括不用於方法主體中的參數； |
| [CA1802:建議在適當時使用常值](../code-quality/ca1802.md) | 欄位會宣告為靜態和唯讀（在中為 Shared 和 ReadOnly [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ），並使用在編譯時期可的值進行初始化。 因為指派給目標欄位的值是在編譯時期可，所以請將宣告變更為 const （Const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ）欄位，以便在編譯時期（而不是在執行時間）計算該值。 |
| [CA1804:必須移除未使用的區域變數](../code-quality/ca1804.md) | 未使用的區域變數和不必要的設定，會增加組件的大小並降低效能。 |
| [CA1805：不必要地初始化](../code-quality/ca1805.md) | 在執行此函式之前，.NET 執行時間會將參考型別的所有欄位初始化為其預設值。 在大部分情況下，將欄位明確初始化為其預設值是多餘的，這會增加維護成本，並可能降低效能（例如，增加元件大小）。 |
| [CA1806:不要忽略方法的結果](../code-quality/ca1806.md) | 已建立但從未使用的新物件，或已呼叫建立並傳回新字串的方法，但從未使用過新字串，或元件物件模型（COM）或 P/Invoke 方法會傳回從未使用的 HRESULT 或錯誤碼。 |
| [CA1809:避免在方法中包含過多區域變數](../code-quality/ca1809.md) | 常見的效能最佳化作法是在處理器暫存器中儲存值，而非記憶體，這稱為「註冊 (Enregistering) 值」。  若要增加所有區域變數都能註冊的機率，請將區域變數的數目限制為 64。 |
| [CA1810:必須將參考類型內部的靜態欄位初始化](../code-quality/ca1810.md) | 當類型宣告明確的靜態建構函式時，Just-In-Time (JIT) 編譯器會將檢查加入至類型的每個靜態方法和執行個體建構函式，確保之前已呼叫該靜態建構函式。 靜態建構函式檢查會降低效能。 |
| [CA1811:避免使用未呼叫的私用程式碼](../code-quality/ca1811.md) | 私用或內部（元件層級）成員在元件中沒有呼叫端，它不是由 common language runtime 叫用，而且不是由委派叫用。 |
| [CA1812:避免使用未執行個體化的內部類別](../code-quality/ca1812.md) | 組件層級類型的執行個體不是由組件中的程式碼所建立。 |
| [CA1813:避免使用非密封屬性](../code-quality/ca1813.md) | .NET 提供用來抓取自訂屬性的方法。 根據預設，這些方法會搜尋屬性繼承階層架構。 密封屬性會減少對整個繼承階層架構的搜尋，並且可以改進效能。 |
| [CA1814:建議使用不規則陣列取代多維陣列](../code-quality/ca1814.md) | 不規則陣列是一種陣列，其元素也是陣列。 組成專案的陣列可以是不同的大小，這可能會導致某些資料集的空間浪費較少。 |
| [CA1815:必須覆寫實值類型上的 Equals 方法和等號比較運算子](../code-quality/ca1815.md) | 對於實值類型而言，Equals 的繼承實作會使用 Reflection 程式庫，並比較所有欄位的內容。 但是 Reflection 相當耗費運算資源，而且可能不需要比較每個欄位是否相等。 如果希望使用者比較或排序執行個體，或是使用執行個體做為雜湊資料表索引鍵，則您的實值類型應實作 Equals。 |
| [CA1816:正確呼叫 GC.SuppressFinalize](../code-quality/ca1816.md) | 執行 Dispose 的方法不會呼叫 GC。Gc.suppressfinalize，或不是 Dispose 呼叫 GC 的方法。Gc.suppressfinalize，或方法會呼叫 GC。Gc.suppressfinalize 並傳遞以外的其他專案（我在中 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ）。 |
| [CA1819:屬性不應該傳回陣列](../code-quality/ca1819.md) | 屬性所傳回的陣列不會受到寫入保護，即使屬性是唯讀也是一樣。 若要保持陣列為防止遭他人修改，屬性必須傳回陣列複本。 一般而言，使用者不了解呼叫這類屬性所造成的不良效能影響。 |
| [CA1820:應該使用字串長度測試空白字串](../code-quality/ca1820.md) | 使用 String.Length 屬性或 String.IsNullOrEmpty 方法比較字串，明顯地會比使用 Equals 還快。 |
| [CA1821:必須移除空的完成項](../code-quality/ca1821.md) | 請盡可能避免使用完成項，因為追蹤物件存留期 (Lifetime) 時將會產生額外的效能負荷。 空的完成項會造成額外的負擔，而不會有任何好處。 |
| [CA1822:將成員標記為 static](../code-quality/ca1822.md) | 不會存取執行個體資料或不會呼叫執行個體方法的成員，可以標記為 static (在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 Shared)。 將方法標記為 static 之後，編譯器將對這些成員發出非虛擬呼叫位置。 這麼做可以讓重視效能的程式碼獲得可觀的效能。 |
| [CA1823:避免包含未使用的私用欄位](../code-quality/ca1823.md) | 偵測到似乎不能在組件內存取的私用欄位。 |
| [CA1824:組件必須標記 NeutralResourcesLanguageAttribute](../code-quality/ca1824.md) | NeutralResourcesLanguage 屬性 (Attribute) 會告知 ResourceManager，用來顯示組件之中性文化特性 (Culture) 資源的語言。 這可改善載入第一個資源的查詢效能，而且可以減少您的工作集。 |
| [CA1825：請避免長度為零的陣列配置](../code-quality/ca1825.md) | 初始化長度為零的陣列會導致不必要的記憶體配置。 相反地，請藉由呼叫來使用靜態配置的空陣列實例 <xref:System.Array.Empty%2A?displayProperty=nameWithType> 。 記憶體配置會在此方法的所有調用之間共用。 |
| [CA1826：請使用屬性，不要使用 Linq Enumerable 方法](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable>LINQ 方法是在支援對等、更有效率的屬性的型別上使用。 |
| [CA1827：不要在可使用 Any 時使用 Count/LongCount](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A><xref:System.Linq.Enumerable.LongCount%2A>使用了或方法，其中 <xref:System.Linq.Enumerable.Any%2A> 方法會更有效率。 |
| [CA1828：不要在可使用 AnyAsync 時使用 CountAsync/LongCountAsync](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A><xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A>使用了或方法，其中 <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> 方法會更有效率。 |
| [CA1829：請使用 Length/Count 屬性，不要使用 Enumerable.Count 方法](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A>LINQ 方法是在支援對等、更有效率或屬性的型別上使用 `Length` `Count` 。 |
| [CA1830：建議在 StringBuilder 上使用強型別 Append 及 Insert 方法多載](../code-quality/ca1830.md) | <xref:System.Text.StringBuilder.Append%2A>和會 <xref:System.Text.StringBuilder.Insert%2A> 提供多載，供 system.string 以外的多種類型之用。  可能的話，偏好使用 ToString （）和以字串為基礎之多載的強型別多載。 |
| [CA1831：在適用情況下，請使用 AsSpan 做為字串，不要使用範圍型的索引子](../code-quality/ca1831.md) | 在字串上使用範圍索引子，並隱含地將值指派給 ReadOnlySpan &lt; char &gt; 類型時， <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> 會使用方法，而不是 <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> ，這會產生字串要求部分的複本。 |
| [CA1832：請使用 AsSpan 或 AsMemory 來取得陣列的 ReadOnlySpan 或 ReadOnlyMemory 部分，不要使用範圍型的索引子](../code-quality/ca1832.md) | 在陣列上使用範圍索引子，並隱含地將值指派給 <xref:System.ReadOnlySpan%601> 或 <xref:System.ReadOnlyMemory%601> 類型時，將會 <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> 使用方法，而不是 <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> ，這會產生陣列所要求部分的複本。 |
| [CA1833：請使用 AsSpan 或 AsMemory 取得陣列的 Span 或 Memory 部分，不要使用範圍型的索引子](../code-quality/ca1833.md) | 在陣列上使用範圍索引子，並隱含地將值指派給 <xref:System.Span%601> 或 <xref:System.Memory%601> 類型時，將會 <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> 使用方法，而不是 <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> ，這會產生陣列所要求部分的複本。 |
| [CA1835：偏好 ' ReadAsync ' 和 ' WriteAsync ' 的以 Memory' 為基礎的多載](../code-quality/ca1835.md) | ' Stream ' 具有 ' ReadAsync ' 多載，其接受 ' Memory &lt; byte &gt; ' 作為第一個引數，而 ' WriteAsync ' 多載接受 ' ReadOnlyMemory &lt; Byte &gt; ' 做為第一個引數。 偏好呼叫以記憶體為基礎的多載，這會更有效率。 |
