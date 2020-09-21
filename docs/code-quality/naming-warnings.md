---
title: 命名規則
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.namingrules
helpviewer_keywords:
- managed code analysis rules, naming rules
- naming rules
- rules, naming
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2032a66837ef790ce37ef178805a13841f203342
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810190"
---
# <a name="naming-rules"></a>命名規則

命名規則支援遵守 .NET 設計指導方針的命名慣例。

## <a name="in-this-section"></a>本節內容

|規則|描述|
|----------|-----------------|
|[CA1700:不要在列舉值名稱中包含 'Reserved'](../code-quality/ca1700.md)|這項規則假設名稱中包含 "reserved" 的列舉成員目前並未使用，但是在未來版本會是重新命名或移除的替代符號 (Placeholder)。 重新命名或移除成員是中斷變更。|
|[CA1707:識別項名稱不應該包含底線](../code-quality/ca1707.md)|根據慣例，識別項名稱不包含底線 (_) 字元。 此規則會檢查命名空間、類型、成員和參數。|
|[CA1708:識別項名稱不應該只靠大小寫區別](../code-quality/ca1708.md)|因為以通用語言執行平台為目標的語言不需要區分大小寫，因此，命名空間、類型、成員和參數的識別項不能只有大小寫的不同。|
|[CA1710:識別項應該使用正確的後置字元](../code-quality/ca1710.md)|依照慣例，擴充特定基底類型或實作為某些介面的類型名稱，或是從這些類型衍生的類型，其後綴會與基底類型或介面相關聯。|
|[CA1711:識別項名稱不應該使用不正確的後置字元](../code-quality/ca1711.md)|依照慣例，只有擴充特定基底類型或實作特定介面的類型名稱，或是從這些類型衍生的類型名稱，應以特定保留的後置字元結尾。 其他類型名稱不得使用這些保留的後置字元。|
|[CA1712:不要使用類型名稱作為列舉值的前置字元](../code-quality/ca1712.md)|列舉成員的名稱不會加上類型名稱的前置詞，因為開發工具預期會提供類型資訊。|
|[CA1713:事件不應該有 before 或 after 前置字元](../code-quality/ca1713.md)|事件的名稱會以 "Before" 或 "After" 為開頭。 若要命名在特定序列 (Sequence) 中引發的相關事件，請使用現在式或過去式表示動作序列相對的位置。|
|[CA1714:旗標列舉應該使用複數名稱](../code-quality/ca1714.md)|公用列舉具有 FlagsAttribute 屬性，而且其名稱結尾不是 "s"。 標記為 FlagsAttribute 的類型具有複數名稱，因為屬性工作表示可以指定多個值。|
|[CA1715:識別項名稱應該使用正確的前置字元](../code-quality/ca1715.md)|外部可見介面的名稱不是以大寫 "I" 開頭。  外部可見類型或方法上泛型型別參數的名稱不是以大寫 "T" 開頭。|
|[CA1716:識別項名稱不應該和關鍵字相符](../code-quality/ca1716.md)|命名空間 (Namespace) 名稱或類型名稱符合程式語言中的保留關鍵字。 命名空間和類型的識別項不應該符合語言所定義的關鍵字，而這些語言的目標為 Common Language Runtime。|
|[CA1717:只有 FlagsAttribute 列舉應該使用複數名稱](../code-quality/ca1717.md)|依照命名規範的要求，列舉的複數名稱代表可以同時指定多個列舉值。|
|[CA1720:識別項名稱不應該包含類型名稱](../code-quality/ca1720.md)|外部可見成員中的參數名稱包含資料類型名稱，或外部可見成員的名稱包含語言特定的資料類型名稱。|
|[CA1721:屬性名稱不應該和其中有 get 的方法名稱相符](../code-quality/ca1721.md)|公用或保護之成員的名稱是以 "Get" 開頭，否則需符合公用或保護之屬性的名稱。 "Get" 方法和屬性的名稱應該清楚區別其功能。|
|[CA1724:類型名稱不應該和命名空間相符](../code-quality/ca1724.md)|類型名稱不應與 .NET 命名空間的名稱相符。 違規此規則可能會降低程式庫的可用性。|
|[CA1725:參數名稱應該符合基底類型的宣告](../code-quality/ca1725.md)|在覆寫階層架構中一致的參數命名方式，會增加方法覆寫的可用性。 與基底宣告中的名稱不同之衍生方法中的參數名稱，可能會造成方法為基底方法的覆寫或為方法的新多載而混淆。|
