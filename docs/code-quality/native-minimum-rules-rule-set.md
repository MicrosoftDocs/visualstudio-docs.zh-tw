---
title: 原生最小規則規則集
ms.date: 11/04/2016
description: 瞭解 Visual Studio 中的原生最小規則規則集。 請參閱機器碼的安全性、穩定性和其他重大問題的規則描述。
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 2d898bc4-fba5-472e-8f09-b0c6b511c5a3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e029e0127a361bc133c008cef36d4426617c83b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867824"
---
# <a name="native-minimum-rules-rule-set"></a>原生最小規則規則集

Microsoft 原生最小規則著重于機器碼中最嚴重的問題，包括潛在的安全性漏洞和應用程式當機。

在您為原生專案建立的任何自訂規則集中包含此規則集。

|規則|Description|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|使用尚未初始化的記憶體|
|[C6011](/cpp/code-quality/c6011)|取值的指標為 NULL|
|[C6029](/cpp/code-quality/c6029)|未經確認值的使用|
|[C6053](/cpp/code-quality/c6053)|呼叫中的零結尾|
|[C6059](/cpp/code-quality/c6059)|不正確的串連|
|[C6063](/cpp/code-quality/c6063)|遺漏格式函式的字串引數|
|[C6064](/cpp/code-quality/c6064)|遺漏格式函式的整數引數|
|[C6066](/cpp/code-quality/c6066)|遺漏格式函式的指標引數|
|[C6067](/cpp/code-quality/c6067)|遺漏格式函式的字串指標引數|
|[C6101](/cpp/code-quality/c6101)|傳回未初始化的記憶體|
|[C6200](/cpp/code-quality/c6200)|索引超出緩衝區上限|
|[C6201](/cpp/code-quality/c6201)|索引超出堆疊緩衝區上限|
|[C6270](/cpp/code-quality/c6270)|遺漏格式函式的浮點引數|
|[C6271](/cpp/code-quality/c6271)|格式函式的多餘引數|
|[C6272](/cpp/code-quality/c6272)|格式函式的非浮點引數|
|[C6273](/cpp/code-quality/c6273)|格式函式的非整數引數|
|[C6274](/cpp/code-quality/c6274)|格式函式的非字元引數|
|[C6276](/cpp/code-quality/c6276)|無效的字串轉型|
|[C6277](/cpp/code-quality/c6277)|無效的 CreateProcess 呼叫|
|[C6284](/cpp/code-quality/c6284)|格式函式的物件引數無效|
|[C6290](/cpp/code-quality/c6290)|邏輯 NOT 位元 AND 優先順序|
|[C6291](/cpp/code-quality/c6291)|邏輯 NOT 位元 OR 優先順序|
|[C6302](/cpp/code-quality/c6302)|格式函式的字元字串引數無效|
|[C6303](/cpp/code-quality/c6303)|格式函式的寬字元字串引數無效|
|[C6305](/cpp/code-quality/c6305)|大小和計數用法不符|
|[C6306](/cpp/code-quality/c6306)|不正確的變數引數函式呼叫|
|[C6328](/cpp/code-quality/c6328)|引數類型可能不符|
|[C6385](/cpp/code-quality/c6385)|讀取滿溢|
|[C6386](/cpp/code-quality/c6386)|寫入滿溢|
|[C6387](/cpp/code-quality/c6387)|無效的參數值|
|[C6500](/cpp/code-quality/c6500)|無效的屬性 (Attribute) 屬性 (Property)|
|[C6501](/cpp/code-quality/c6501)|衝突的屬性 (Attribute) 屬性 (Property) 值|
|[C6503](/cpp/code-quality/c6503)|參考不能是 Null|
|[C6504](/cpp/code-quality/c6504)|非指標上的 Null|
|[C6505](/cpp/code-quality/c6505)|Void 上的 MustCheck|
|[C6506](/cpp/code-quality/c6506)|非指標或陣列上的緩衝區大小|
|[C6508](/cpp/code-quality/c6508)|寫入存取常數|
|[C6509](/cpp/code-quality/c6509)|先前的條件所用的 Return|
|[C6510](/cpp/code-quality/c6510)|非指標上的 Null Terminated|
|[C6511](/cpp/code-quality/c6511)|MustCheck 必須為 Yes 或 No|
|[C6513](/cpp/code-quality/c6513)|不含緩衝區大小的元素大小|
|[C6514](/cpp/code-quality/c6514)|緩衝區大小超過陣列大小|
|[C6515](/cpp/code-quality/c6515)|非指標上的緩衝區大小|
|[C6516](/cpp/code-quality/c6516)|屬性 (Attribute) 上沒有屬性 (Property)|
|[C6517](/cpp/code-quality/c6517)|不能讀取的緩衝區上的有效大小|
|[C6518](/cpp/code-quality/c6518)|不能寫入的緩衝區上的可寫入大小|
|[C6522](/cpp/code-quality/c6522)|無效的大小字串類型|
|[C6525](/cpp/code-quality/c6525)|無效的大小字串不可能執行到的位置|
|[C6527](/cpp/code-quality/c6527)|無效的註釋：'NeedsRelease' 屬性不能用於 void 類型的值|
|[C6530](/cpp/code-quality/c6530)|無法辨認的格式字串樣式|
|[C6540](/cpp/code-quality/c6540)|在這個函式上使用屬性註釋會使其所有現有的 __declspec 註釋無效。|
|[C6551](/cpp/code-quality/c6551)|無效的大小規格: 無法剖析運算式|
|[C6552](/cpp/code-quality/c6552)|無效的 Deref= 或 Notref=: 無法剖析運算式|
|[C6701](/cpp/code-quality/c6701)|值不是有效的 Yes/No/Maybe 值|
|[C6702](/cpp/code-quality/c6702)|值不是字串值|
|[C6703](/cpp/code-quality/c6703)|值不是數字|
|[C6704](/cpp/code-quality/c6704)|未預期的註釋運算式錯誤|
|[C6705](/cpp/code-quality/c6705)|註釋的預期引數數目不符合註釋的實際引數數目|
|[C6706](/cpp/code-quality/c6706)|註釋發生未預期的註釋錯誤|
|[C26450](/cpp/code-quality/C26450)|RESULT_OF_ARITHMETIC_OPERATION_PROVABLY_LOSSY|
|[C26451](/cpp/code-quality/C26451)|RESULT_OF_ARITHMETIC_OPERATION_CAST_TO_LARGER_SIZE|
|[C26452](/cpp/code-quality/C26452)|SHIFT_COUNT_NEGATIVE_OR_TOO_BIG|
|[C26453](/cpp/code-quality/C26453)|LEFTSHIFT_NEGATIVE_SIGNED_NUMBER|
|[C26454](/cpp/code-quality/C26454)|RESULT_OF_ARITHMETIC_OPERATION_NEGATIVE_UNSIGNED|
|[C26495](/cpp/code-quality/C26495)|MEMBER_UNINIT|
|[C28021](/cpp/code-quality/c28021)|所標註的參數必須是指標|
|[C28182](/cpp/code-quality/c28182)|取值的指標為 NULL。 指標所包含的 NULL 值與另一個指標相同。|
|[C28202](/cpp/code-quality/c28202)|非靜態成員的參考不合法|
|[C28203](/cpp/code-quality/c28203)|類別成員的參考模稜兩可。|
|[C28205](/cpp/code-quality/c28205)|\_\_ \_ \_ \_ 在不合法的內容中使用成功或失敗|
|[C28206](/cpp/code-quality/c28206)|左運算元指向結構，請使用 '->'|
|[C28207](/cpp/code-quality/c28207)|左運算元是結構，請使用 '.'|
|[C28210](/cpp/code-quality/c28210)|_On_failure_ 內容的註釋不能在明確 pre context 中|
|[C28211](/cpp/code-quality/c28211)|SAL_context 需要靜態內容名稱|
|[C28212](/cpp/code-quality/c28212)|註釋需要指標運算式|
|[C28213](/cpp/code-quality/c28213)|\_使用 \_ decl \_ 注釋 \_ 注釋必須用來參考先前的宣告，而不需要修改。|
|[C28214](/cpp/code-quality/c28214)|屬性參數名稱必須是 p1...p9|
|[C28215](/cpp/code-quality/c28215)|typefix 不能套用到已經有 typefix 的參數|
|[C28216](/cpp/code-quality/c28216)|checkReturn 註釋只適用於特定函式參數的後置條件。|
|[C28217](/cpp/code-quality/c28217)|對於函式，註釋的參數數目不符合檔案中找到的參數數目|
|[C28218](/cpp/code-quality/c28218)|針對函式參數，注釋的參數不符合檔案中找到的參數|
|[C28219](/cpp/code-quality/c28219)|註釋中標註的參數需要列舉的成員|
|[C28220](/cpp/code-quality/c28220)|註釋中標註的參數需要整數運算式|
|[C28221](/cpp/code-quality/c28221)|註釋中的參數需要字串運算式|
|[C28222](/cpp/code-quality/c28222)|註釋需要 __yes、\__no 或 \__maybe|
|[C28223](/cpp/code-quality/c28223)|找不到註釋參數需要的語彙基元/識別項|
|[C28224](/cpp/code-quality/c28224)|註釋需要參數|
|[C28225](/cpp/code-quality/c28225)|找不到註釋中必要參數的正確數目|
|[C28226](/cpp/code-quality/c28226)|註釋不能也是 PrimOp (在目前宣告中)|
|[C28227](/cpp/code-quality/c28227)|註釋不能也是 PrimOp (參閱之前的宣告)|
|[C28228](/cpp/code-quality/c28228)|註釋參數: 不能在註釋中使用類型|
|[C28229](/cpp/code-quality/c28229)|註釋不支援參數|
|[C28230](/cpp/code-quality/c28230)|參數的類型沒有成員。|
|[C28231](/cpp/code-quality/c28231)|註釋只在陣列上有效|
|[C28232](/cpp/code-quality/c28232)|pre、post 或 deref 未套用至任何註釋|
|[C28233](/cpp/code-quality/c28233)|pre、post 或 deref 已套用至區塊|
|[C28234](/cpp/code-quality/c28234)|__at 運算式未套用到目前函式|
|[C28235](/cpp/code-quality/c28235)|函式不能獨立成為註釋|
|[C28236](/cpp/code-quality/c28236)|註釋不能用在運算式中|
|[C28237](/cpp/code-quality/c28237)|不再支援參數上的註釋|
|[C28238](/cpp/code-quality/c28238)|參數上的註釋具有一個以上的值：stringValue 和 longValue。 請使用 paramn=xxx|
|[C28239](/cpp/code-quality/c28239)|參數上的註釋具有兩個值，stringValue 或 longValue 以及 paramn=xxx。 請只使用 paramn=xxx|
|[C28240](/cpp/code-quality/c28240)|參數上的註釋有 param2 但沒有 param1|
|[C28241](/cpp/code-quality/c28241)|無法辨認參數上的函式之註釋|
|[C28243](/cpp/code-quality/c28243)|參數上的函式之註釋需要執行的取值比實際標註之類型允許的還多|
|[C28245](/cpp/code-quality/c28245)|函式的註釋會在非成員函式上標註 'this'|
|[C28246](/cpp/code-quality/c28246)|函式的參數註釋不符合參數的類型|
|[C28250](/cpp/code-quality/c28250)|函式的註釋不一致：之前的執行個體有錯誤。|
|[C28251](/cpp/code-quality/c28251)|函式的註釋不一致：這個執行個體有錯誤。|
|[C28252](/cpp/code-quality/c28252)|函式的註釋不一致：參數有這個執行個體的另一個註釋。|
|[C28253](/cpp/code-quality/c28253)|函式的註釋不一致：參數有這個執行個體的另一個註釋。|
|[C28254](/cpp/code-quality/c28254)|註釋中不支援 dynamic_cast<>()|
|[C28262](/cpp/code-quality/c28262)|在函式 (隸屬於註釋) 中找到註釋的語法錯誤|
|[C28263](/cpp/code-quality/c28263)|找到內建註釋的條件式註釋語法錯誤|
|[C28267](/cpp/code-quality/c28267)|在函式 (隸屬於註釋) 中找到註釋的語法錯誤。|
|[C28272](/cpp/code-quality/c28272)|函式參數的註釋在檢查時，與函式宣告不一致|
|[C28273](/cpp/code-quality/c28273)|對於函式，線索與函式宣告不一致|
|[C28275](/cpp/code-quality/c28275)|\_宏值的參數 \_ \_ 為 null|
|[C28279](/cpp/code-quality/c28279)|找到符號的 'begin'，但沒有相符的 'end'|
|[C28280](/cpp/code-quality/c28280)|找到符號的 'end'，但沒有相符的 'begin'|
|[C28282](/cpp/code-quality/c28282)|格式字串必須在前置條件中|
|[C28285](/cpp/code-quality/c28285)|對於函式，參數中有語法錯誤|
|[C28286](/cpp/code-quality/c28286)|對於函式，結尾附近發生語法錯誤|
|[C28287](/cpp/code-quality/c28287)|函式的 \_At\_() 註釋中有語法錯誤 (無法辨認的參數名稱)|
|[C28288](/cpp/code-quality/c28288)|函式的 \_At\_() 註釋中有語法錯誤 (無效的參數名稱)|
|[C28289](/cpp/code-quality/c28289)|對於函式：ReadableTo 或 WritableTo 沒有有限的規格做為參數|
|[C28290](/cpp/code-quality/c28290)|函式的註釋包含比實際參數數目還多的外部|
|[C28291](/cpp/code-quality/c28291)|位於 deref 層級 0 的 post null/notnull 對函式是無意義的。|
|[C28300](/cpp/code-quality/c28300)|運算子的運算式運算元類型不相容|
|[C28301](/cpp/code-quality/c28301)|函式的第一個宣告沒有註釋。|
|[C28302](/cpp/code-quality/c28302)|在註釋中發現額外的 \_Deref\_ 運算子。|
|[C28303](/cpp/code-quality/c28303)|在註釋發現模擬兩可的 \_Deref\_ 運算子。|
|[C28304](/cpp/code-quality/c28304)|發現有位置不正確的 \_Notref\_ 運算子套用至語彙基元。|
|[C28305](/cpp/code-quality/c28305)|剖析語彙基元時發現錯誤。|
|[C28350](/cpp/code-quality/c28350)|註釋描述了條件不適用的狀況。|
|[C28351](/cpp/code-quality/c28351)|註釋描述條件中不可以使用動態值 (變數)。|