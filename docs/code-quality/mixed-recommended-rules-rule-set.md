---
title: 混合建議規則規則集
ms.date: 11/04/2016
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ce28a8c1dd5c9ec510e4bf30b6e710b2b4dbc2a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "81649327"
---
# <a name="mixed-recommended-rules-rule-set"></a>混合建議規則規則集

Microsoft 混合的建議規則會將焦點放在 c + + 專案中支援 Common Language Runtime 的最常見和重大問題，包括潛在的安全性漏洞、應用程式損毀，以及其他重要的邏輯和設計錯誤。 此規則集會包含「 [混合的最小規則](mixed-minimum-rules-rule-set.md) 」規則集中的所有規則。

在您為支援 Common Language Runtime 的 c + + 專案所建立的任何自訂規則集中包含此規則集。

|規則|說明|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|使用尚未初始化的記憶體|
|[C6011](../code-quality/c6011.md)|取值的指標為 NULL|
|[C6029](../code-quality/c6029.md)|未經確認值的使用|
|[C6031](../code-quality/c6031.md)|已忽略傳回值|
|[C6053](../code-quality/c6053.md)|呼叫中的零結尾|
|[C6054](../code-quality/c6054.md)|遺漏零終止|
|[C6059](../code-quality/c6059.md)|不正確的串連|
|[C6063](../code-quality/c6063.md)|遺漏格式函式的字串引數|
|[C6064](../code-quality/c6064.md)|遺漏格式函式的整數引數|
|[C6066](../code-quality/c6066.md)|遺漏格式函式的指標引數|
|[C6067](../code-quality/c6067.md)|遺漏格式函式的字串指標引數|
|[C6101](../code-quality/c6101.md)|傳回未初始化的記憶體|
|[C6200](../code-quality/c6200.md)|索引超出緩衝區上限|
|[C6201](../code-quality/c6201.md)|索引超出堆疊緩衝區上限|
|[C6214](../code-quality/c6214.md)|不正確轉換 HRESULT 至 BOOL|
|[C6215](../code-quality/c6215.md)|不正確轉換 BOOL 至 HRESULT|
|[C6216](../code-quality/c6216.md)|編譯器插入了不正確轉換 BOOL 至 HRESULT|
|[C6217](../code-quality/c6217.md)|未使用不正確 HRESULT 測試|
|[C6220](../code-quality/c6220.md)|不正確 HRESULT 與-1 比較|
|[C6226](../code-quality/c6226.md)|對-1 不正確 HRESULT 指派|
|[C6230](../code-quality/c6230.md)|將不正確 HRESULT 用作布林值|
|[C6235](../code-quality/c6235.md)|具有邏輯 Or 的非零常數|
|[C6236](../code-quality/c6236.md)|邏輯或非零的常數|
|[C6237](../code-quality/c6237.md)|零，有邏輯和失去副作用|
|[C6242](../code-quality/c6242.md)|強制執行本機回溯|
|[C6248](../code-quality/c6248.md)|建立 Null DACL|
|[C6250](../code-quality/c6250.md)|未發行位址描述項|
|[C6255](../code-quality/c6255.md)|未受保護的 Alloca 使用|
|[C6258](../code-quality/c6258.md)|使用 Terminate 執行緒|
|[C6259](../code-quality/c6259.md)|位或有限參數中的無作用程式碼|
|[C6260](../code-quality/c6260.md)|使用位元組算術|
|[C6262](../code-quality/c6262.md)|過度使用堆疊|
|[C6263](../code-quality/c6263.md)|在迴圈中使用 Alloca|
|[C6268](../code-quality/c6268.md)|Cast 中缺少括弧|
|[C6269](../code-quality/c6269.md)|已忽略指標取值|
|[C6270](../code-quality/c6270.md)|遺漏格式函式的浮點引數|
|[C6271](../code-quality/c6271.md)|格式函式的多餘引數|
|[C6272](../code-quality/c6272.md)|格式函式的非浮點引數|
|[C6273](../code-quality/c6273.md)|格式函式的非整數引數|
|[C6274](../code-quality/c6274.md)|格式函式的非字元引數|
|[C6276](../code-quality/c6276.md)|無效的字串轉型|
|[C6277](../code-quality/c6277.md)|無效的 CreateProcess 呼叫|
|[C6278](../code-quality/c6278.md)|陣列-新的純量刪除不相符|
|[C6279](../code-quality/c6279.md)|純量新陣列-刪除不相符|
|[C6280](../code-quality/c6280.md)|記憶體配置-解除配置不符|
|[C6281](../code-quality/c6281.md)|位關聯優先順序|
|[C6282](../code-quality/c6282.md)|指派取代測試|
|[C6283](../code-quality/c6283.md)|基本陣列-新的純量刪除不相符|
|[C6284](../code-quality/c6284.md)|格式函式的物件引數無效|
|[C6285](../code-quality/c6285.md)|常數的邏輯 Or|
|[C6286](../code-quality/c6286.md)|非零的邏輯 Or 遺失副作用|
|[C6287](../code-quality/c6287.md)|重複的測試|
|[C6288](../code-quality/c6288.md)|透過邏輯和的相互包含為 False|
|[C6289](../code-quality/c6289.md)|邏輯或為 True 的相互排除|
|[C6290](../code-quality/c6290.md)|邏輯 NOT 位元 AND 優先順序|
|[C6291](../code-quality/c6291.md)|邏輯 NOT 位元 OR 優先順序|
|[C6292](../code-quality/c6292.md)|從最大值的迴圈計數|
|[C6293](../code-quality/c6293.md)|迴圈從最小值向下計數|
|[C6294](../code-quality/c6294.md)|永遠不會執行迴圈主體|
|[C6295](../code-quality/c6295.md)|無限迴圈|
|[C6296](../code-quality/c6296.md)|迴圈只執行一次|
|[C6297](../code-quality/c6297.md)|變換轉換成較大大小的結果|
|[C6299](../code-quality/c6299.md)|位欄位與布林值的比較|
|[C6302](../code-quality/c6302.md)|格式函式的字元字串引數無效|
|[C6303](../code-quality/c6303.md)|格式函式的寬字元字串引數無效|
|[C6305](../code-quality/c6305.md)|大小和計數用法不符|
|[C6306](../code-quality/c6306.md)|不正確的變數引數函式呼叫|
|[C6308](../code-quality/c6308.md)|Realloc 流失|
|[C6310](../code-quality/c6310.md)|不合法的例外狀況篩選準則常數|
|[C6312](../code-quality/c6312.md)|例外狀況繼續執行迴圈|
|[C6314](../code-quality/c6314.md)|位 Or 優先順序|
|[C6317](../code-quality/c6317.md)|不可補數|
|[C6318](../code-quality/c6318.md)|例外狀況繼續搜尋|
|[C6319](../code-quality/c6319.md)|略過逗號|
|[C6324](../code-quality/c6324.md)|字串複製而不是字串比較|
|[C6328](../code-quality/c6328.md)|引數類型可能不符|
|[C6331](../code-quality/c6331.md)|VirtualFree 不正確旗標|
|[C6332](../code-quality/c6332.md)|VirtualFree 不正確參數|
|[C6333](../code-quality/c6333.md)|VirtualFree 不正確大小|
|[C6335](../code-quality/c6335.md)|洩漏進程控制碼|
|[C6381](../code-quality/c6381.md)|遺失關機資訊|
|[C6383](../code-quality/c6383.md)|元素計數位節計數緩衝區溢位|
|[C6384](../code-quality/c6384.md)|指標大小分割|
|[C6385](../code-quality/c6385.md)|讀取滿溢|
|[C6386](../code-quality/c6386.md)|寫入滿溢|
|[C6387](../code-quality/c6387.md)|無效的參數值|
|[C6388](../code-quality/c6388.md)|無效的參數值|
|[C6500](../code-quality/c6500.md)|無效的屬性 (Attribute) 屬性 (Property)|
|[C6501](../code-quality/c6501.md)|衝突的屬性 (Attribute) 屬性 (Property) 值|
|[C6503](../code-quality/c6503.md)|參考不能是 Null|
|[C6504](../code-quality/c6504.md)|非指標上的 Null|
|[C6505](../code-quality/c6505.md)|Void 上的 MustCheck|
|[C6506](../code-quality/c6506.md)|非指標或陣列上的緩衝區大小|
|[C6508](../code-quality/c6508.md)|寫入存取常數|
|[C6509](../code-quality/c6509.md)|先前的條件所用的 Return|
|[C6510](../code-quality/c6510.md)|非指標上的 Null Terminated|
|[C6511](../code-quality/c6511.md)|MustCheck 必須為 Yes 或 No|
|[C6513](../code-quality/c6513.md)|不含緩衝區大小的元素大小|
|[C6514](../code-quality/c6514.md)|緩衝區大小超過陣列大小|
|[C6515](../code-quality/c6515.md)|非指標上的緩衝區大小|
|[C6516](../code-quality/c6516.md)|屬性 (Attribute) 上沒有屬性 (Property)|
|[C6517](../code-quality/c6517.md)|不能讀取的緩衝區上的有效大小|
|[C6518](../code-quality/c6518.md)|不能寫入的緩衝區上的可寫入大小|
|[C6522](../code-quality/c6522.md)|無效的大小字串類型|
|[C6525](../code-quality/c6525.md)|無效的大小字串不可能執行到的位置|
|[C6527](../code-quality/c6527.md)|無效的註釋：'NeedsRelease' 屬性不能用於 void 類型的值|
|[C6530](../code-quality/c6530.md)|無法辨認的格式字串樣式|
|[C6540](../code-quality/c6540.md)|在這個函式上使用屬性註釋會使其所有現有的 __declspec 註釋無效。|
|[C6551](../code-quality/c6551.md)|無效的大小規格: 無法剖析運算式|
|[C6552](../code-quality/c6552.md)|無效的 Deref= 或 Notref=: 無法剖析運算式|
|[C6701](../code-quality/c6701.md)|值不是有效的 Yes/No/Maybe 值|
|[C6702](../code-quality/c6702.md)|值不是字串值|
|[C6703](../code-quality/c6703.md)|值不是數字|
|[C6704](../code-quality/c6704.md)|未預期的註釋運算式錯誤|
|[C6705](../code-quality/c6705.md)|註釋的預期引數數目不符合註釋的實際引數數目|
|[C6706](../code-quality/c6706.md)|註釋發生未預期的註釋錯誤|
|[C6995](../code-quality/c6995.md)|無法儲存 XML 記錄檔|
|[C26100](../code-quality/c26100.md)|競爭條件|
|[C26101](../code-quality/c26101.md)|無法正確使用連鎖操作|
|[C26110](../code-quality/c26110.md)|呼叫端無法保存鎖定|
|[C26111](../code-quality/c26111.md)|呼叫端無法釋放鎖定|
|[C26112](../code-quality/c26112.md)|呼叫端無法保留任何鎖定|
|[C26115](../code-quality/c26115.md)|無法釋放鎖定|
|[C26116](../code-quality/c26116.md)|無法取得或保留鎖定|
|[C26117](../code-quality/c26117.md)|釋放解除未保留鎖定|
|[C26140](../code-quality/c26140.md)|並行 SAL 注釋錯誤|
|[C28020](../code-quality/c28020.md)|此呼叫的運算式不是 true|
|[C28021](../code-quality/c28021.md)|所標註的參數必須是指標|
|[C28022](../code-quality/c28022.md)|這個函式上 (es) 的函式類別，與用來定義它的 typedef 上的函數類別 (es) 不相符。|
|[C28023](../code-quality/c28023.md)|要指派或傳遞的函式，至少要有一個類別的函式 \_ \_ 類別 \_ 注釋 (es) |
|[C28024](../code-quality/c28024.md)|指派給的函式指標會以函式類別來標注，該函式類別不包含在函數類別 (es) 清單中。|
|[C28039](../code-quality/c28039.md)|實際參數的類型應該與類型完全相符|
|[C28112](../code-quality/c28112.md)|透過連鎖函數存取的變數必須一律透過連鎖函式存取。|
|[C28113](../code-quality/c28113.md)|透過連鎖函數存取本機變數|
|[C28125](../code-quality/c28125.md)|函數必須從 try/except 區塊內呼叫|
|[C28137](../code-quality/c28137.md)|變數引數應改為 (常值) 常數|
|[C28138](../code-quality/c28138.md)|常數引數應改為變數|
|[C28159](../code-quality/c28159.md)|請考慮改為使用其他函數。|
|[C28160](../code-quality/c28160.md)|Error 註釋|
|[C28163](../code-quality/c28163.md)|永遠不應該從 try/except 區塊內呼叫函式|
|[C28164](../code-quality/c28164.md)|將引數傳遞至函式，而該函式需要物件的指標， (不是指標的指標) |
|[C28182](../code-quality/c28182.md)|取值的指標為 NULL。 指標所包含的 NULL 值與另一個指標相同。|
|[C28183](../code-quality/c28183.md)|引數可以是一個值，而且是在指標中找到之值的複本。|
|[C28193](../code-quality/c28193.md)|變數會保留必須檢查的值|
|[C28196](../code-quality/c28196.md)|未滿足需求。  (運算式未評估為 true。 ) |
|[C28202](../code-quality/c28202.md)|非靜態成員的參考不合法|
|[C28203](../code-quality/c28203.md)|類別成員的參考模稜兩可。|
|[C28205](../code-quality/c28205.md)|\_\_ \_ \_ \_ 在不合法的內容中使用成功或失敗|
|[C28206](../code-quality/c28206.md)|左運算元指向結構，請使用 '->'|
|[C28207](../code-quality/c28207.md)|左運算元是結構，請使用 '.'|
|[C28209](../code-quality/c28209.md)|符號的宣告有衝突的宣告|
|[C28210](../code-quality/c28210.md)|_On_failure_ 內容的註釋不能在明確 pre context 中|
|[C28211](../code-quality/c28211.md)|SAL_context 需要靜態內容名稱|
|[C28212](../code-quality/c28212.md)|註釋需要指標運算式|
|[C28213](../code-quality/c28213.md)|\_使用 \_ decl \_ 注釋 \_ 注釋必須用來參考先前的宣告，而不需要修改。|
|[C28214](../code-quality/c28214.md)|屬性參數名稱必須是 p1...p9|
|[C28215](../code-quality/c28215.md)|typefix 不能套用到已經有 typefix 的參數|
|[C28216](../code-quality/c28216.md)|checkReturn 註釋只適用於特定函式參數的後置條件。|
|[C28217](../code-quality/c28217.md)|對於函式，註釋的參數數目不符合檔案中找到的參數數目|
|[C28218](../code-quality/c28218.md)|針對函式參數，注釋的參數不符合檔案中找到的參數|
|[C28219](../code-quality/c28219.md)|註釋中標註的參數需要列舉的成員|
|[C28220](../code-quality/c28220.md)|註釋中標註的參數需要整數運算式|
|[C28221](../code-quality/c28221.md)|註釋中的參數需要字串運算式|
|[C28222](../code-quality/c28222.md)|註釋需要 __yes、\__no 或 \__maybe|
|[C28223](../code-quality/c28223.md)|找不到註釋參數需要的語彙基元/識別項|
|[C28224](../code-quality/c28224.md)|註釋需要參數|
|[C28225](../code-quality/c28225.md)|找不到註釋中必要參數的正確數目|
|[C28226](../code-quality/c28226.md)|註釋不能也是 PrimOp (在目前宣告中)|
|[C28227](../code-quality/c28227.md)|註釋不能也是 PrimOp (參閱之前的宣告)|
|[C28228](../code-quality/c28228.md)|註釋參數: 不能在註釋中使用類型|
|[C28229](../code-quality/c28229.md)|註釋不支援參數|
|[C28230](../code-quality/c28230.md)|參數的類型沒有成員。|
|[C28231](../code-quality/c28231.md)|註釋只在陣列上有效|
|[C28232](../code-quality/c28232.md)|pre、post 或 deref 未套用至任何註釋|
|[C28233](../code-quality/c28233.md)|pre、post 或 deref 已套用至區塊|
|[C28234](../code-quality/c28234.md)|__at 運算式未套用到目前函式|
|[C28235](../code-quality/c28235.md)|函式不能獨立成為註釋|
|[C28236](../code-quality/c28236.md)|註釋不能用在運算式中|
|[C28237](../code-quality/c28237.md)|不再支援參數上的註釋|
|[C28238](../code-quality/c28238.md)|參數上的註釋具有一個以上的值：stringValue 和 longValue。 請使用 paramn=xxx|
|[C28239](../code-quality/c28239.md)|參數上的註釋具有兩個值，stringValue 或 longValue 以及 paramn=xxx。 請只使用 paramn=xxx|
|[C28240](../code-quality/c28240.md)|參數上的註釋有 param2 但沒有 param1|
|[C28241](../code-quality/c28241.md)|無法辨認參數上的函式之註釋|
|[C28243](../code-quality/c28243.md)|參數上的函式之註釋需要執行的取值比實際標註之類型允許的還多|
|[C28244](../code-quality/c28244.md)|函數的注釋具有無法剖析的參數/外部注釋|
|[C28245](../code-quality/c28245.md)|函式的註釋會在非成員函式上標註 'this'|
|[C28246](../code-quality/c28246.md)|函式的參數註釋不符合參數的類型|
|[C28250](../code-quality/c28250.md)|函式的註釋不一致：之前的執行個體有錯誤。|
|[C28251](../code-quality/c28251.md)|函式的註釋不一致：這個執行個體有錯誤。|
|[C28252](../code-quality/c28252.md)|函式的註釋不一致：參數有這個執行個體的另一個註釋。|
|[C28253](../code-quality/c28253.md)|函式的註釋不一致：參數有這個執行個體的另一個註釋。|
|[C28254](../code-quality/c28254.md)|註釋中不支援 dynamic_cast<>()|
|[C28262](../code-quality/c28262.md)|在函式 (隸屬於註釋) 中找到註釋的語法錯誤|
|[C28263](../code-quality/c28263.md)|找到內建註釋的條件式註釋語法錯誤|
|[C28267](../code-quality/c28267.md)|在函式 (隸屬於註釋) 中找到註釋的語法錯誤。|
|[C28272](../code-quality/c28272.md)|函式參數的註釋在檢查時，與函式宣告不一致|
|[C28273](../code-quality/c28273.md)|對於函式，線索與函式宣告不一致|
|[C28275](../code-quality/c28275.md)|\_宏值的參數 \_ \_ 為 null|
|[C28279](../code-quality/c28279.md)|找到符號的 'begin'，但沒有相符的 'end'|
|[C28280](../code-quality/c28280.md)|找到符號的 'end'，但沒有相符的 'begin'|
|[C28282](../code-quality/c28282.md)|格式字串必須在前置條件中|
|[C28285](../code-quality/c28285.md)|對於函式，參數中有語法錯誤|
|[C28286](../code-quality/c28286.md)|對於函式，結尾附近發生語法錯誤|
|[C28287](../code-quality/c28287.md)|函式的 \_At\_() 註釋中有語法錯誤 (無法辨認的參數名稱)|
|[C28288](../code-quality/c28288.md)|函式的 \_At\_() 註釋中有語法錯誤 (無效的參數名稱)|
|[C28289](../code-quality/c28289.md)|對於函式：ReadableTo 或 WritableTo 沒有有限的規格做為參數|
|[C28290](../code-quality/c28290.md)|函式的註釋包含比實際參數數目還多的外部|
|[C28291](../code-quality/c28291.md)|位於 deref 層級 0 的 post null/notnull 對函式是無意義的。|
|[C28300](../code-quality/c28300.md)|運算子的運算式運算元類型不相容|
|[C28301](../code-quality/c28301.md)|函式的第一個宣告沒有註釋。|
|[C28302](../code-quality/c28302.md)|在註釋中發現額外的 \_Deref\_ 運算子。|
|[C28303](../code-quality/c28303.md)|在註釋發現模擬兩可的 \_Deref\_ 運算子。|
|[C28304](../code-quality/c28304.md)|發現有位置不正確的 \_Notref\_ 運算子套用至語彙基元。|
|[C28305](../code-quality/c28305.md)|剖析語彙基元時發現錯誤。|
|[C28306](../code-quality/c28306.md)|參數上的注釋為 sal|
|[C28307](../code-quality/c28307.md)|參數上的注釋為 sal|
|[C28350](../code-quality/c28350.md)|註釋描述了條件不適用的狀況。|
|[C28351](/cpp/code-quality/c28351)|註釋描述條件中不可以使用動態值 (變數)。|
|[CA1001 具有](../code-quality/ca1001.md)|具有可處置欄位的類型應該為可處置|
|[CA1009](../code-quality/ca1009.md)|事件處理常式必須正確宣告|
|[CA1016](../code-quality/ca1016.md)|組件必須標記 AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033.md)|介面方法應該要可以由子類型呼叫|
|[CA1049](../code-quality/ca1049.md)|具有原生資源的類型應該要可呼叫 Dispose 方法明確釋放資源|
|[CA1060](../code-quality/ca1060.md)|必須將 P/Invokes 移到 NativeMethods 類別|
|[CA1061](../code-quality/ca1061.md)|不要隱藏基底類別方法|
|[CA1063](../code-quality/ca1063.md)|必須正確實作 IDisposable|
|[CA1065](../code-quality/ca1065.md)|不要在非預期的位置中引發例外狀況|
|[CA1301](../code-quality/ca1301.md)|避免使用重複的快速鍵|
|[CA1400](../code-quality/ca1400.md)|P/Invoke 進入點應該要存在|
|[CA1401](../code-quality/ca1401.md)|P/Invokes 不應該為可見的|
|[CA1403](../code-quality/ca1403.md)|自動配置類型不應該是 COM 可見|
|[CA1404](../code-quality/ca1404.md)|必須在 P/Invoke 之後立即呼叫 GetLastError|
|[CA1405](../code-quality/ca1405.md)|COM 可見類型的基底類型應該是 COM 可見|
|[CA1410](../code-quality/ca1410.md)|應該和 COM 註冊方法對應|
|[CA1415](../code-quality/ca1415.md)|P/Invokes 必須正確宣告|
|[CA1821 必須](../code-quality/ca1821.md)|必須移除空的完成項|
|[CA1900](../code-quality/ca1900.md)|實值類型欄位應該為可移植的|
|[CA1901](../code-quality/ca1901.md)|P/Invoke 宣告應該為可移植的|
|[CA2002](../code-quality/ca2002.md)|不要鎖定具有弱式識別的物件|
|[CA2100 必須](../code-quality/ca2100.md)|必須檢閱 SQL 查詢中是否有安全性弱點|
|[CA2101 必須](../code-quality/ca2101.md)|必須指定 P/Invoke 字串引數的封送處理|
|[CA2108](../code-quality/ca2108.md)|必須檢閱實值類型上的宣告式安全性|
|[CA2111](../code-quality/ca2111.md)|指標不應該為可見的|
|[CA2112](../code-quality/ca2112.md)|受保護類型不應該公開欄位|
|[CA2114](../code-quality/ca2114.md)|方法安全性應該是類型的超集|
|[CA2116](../code-quality/ca2116.md)|APTCA 方法應該只呼叫 APTCA 方法|
|[CA2117](../code-quality/ca2117.md)|APTCA 類型應該只擴充 APTCA 基底類型|
|[CA2122](../code-quality/ca2122.md)|不要間接公開具有連結要求的方法|
|[CA2123](../code-quality/ca2123.md)|覆寫連結要求應該與基底相同|
|[CA2124](../code-quality/ca2124.md)|必須將有弱點的 finally 子句包裝在外層 try 中|
|[CA2126](../code-quality/ca2126.md)|必須同時具有類型連結要求和繼承要求|
|[CA2131](../code-quality/ca2131.md)|安全性關鍵類型可能未參與類型等價|
|[CA2132](../code-quality/ca2132.md)|預設建構函式至少必須和基底類型的預設建構函式一樣關鍵|
|[CA2133](../code-quality/ca2133.md)|委派必須繫結至具有一致透明度的方法|
|[CA2134](../code-quality/ca2134.md)|覆寫基底方法時，方法必須保持一致的透明度|
|[CA2137](../code-quality/ca2137.md)|透明方法必須只包含可驗證的 IL|
|[CA2138](../code-quality/ca2138.md)|透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法|
|[CA2140](../code-quality/ca2140.md)|透明程式碼不可以參考安全性關鍵項目|
|[CA2141](../code-quality/ca2141.md)|透明方法不能滿足 Linkdemand|
|[CA2146](../code-quality/ca2146.md)|類型至少必須和基底類型與介面一樣關鍵|
|[CA2147](../code-quality/ca2147.md)|CA2147：透明方法不可以使用安全性判斷提示|
|[CA2149](../code-quality/ca2149.md)|透明方法不可以呼叫機器碼|
|[CA2200](../code-quality/ca2200.md)|必須重新擲回以保存堆疊詳細資料|
|[CA2202](../code-quality/ca2202.md)|不要多次處置物件的 Dispose 方法|
|[CA2207](../code-quality/ca2207.md)|必須將實值類型的靜態欄位內嵌初始化|
|[CA2212](../code-quality/ca2212.md)|不要以 WebMethod 標記 Serviced 元件|
|[CA2213](../code-quality/ca2213.md)|可處置的欄位應該受到處置|
|[CA2214](../code-quality/ca2214.md)|不要呼叫建構函式中的可覆寫方法|
|[CA2216](../code-quality/ca2216.md)|可處置的類型應該宣告完成項|
|[CA2220](../code-quality/ca2220.md)|完成項應該呼叫基底類別完成項|
|[CA2229](../code-quality/ca2229.md)|必須實作序列化建構函式|
|[CA2231](../code-quality/ca2231.md)|在覆寫 ValueType.Equals 上多載等號運算子|
|[CA2232](../code-quality/ca2232.md)|Windows Forms 進入點必須標記 STAThread|
|[CA2235 必須](../code-quality/ca2235.md)|必須標記所有不可序列化的欄位|
|[CA2236 必須](../code-quality/ca2236.md)|必須呼叫 ISerializable 類型上的基底類別方法|
|[CA2237 必須](../code-quality/ca2237.md)|ISerializable 類型必須標記 SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|必須正確實作序列化方法|
|[CA2240 必須](../code-quality/ca2240.md)|必須正確實作 ISerializable|
|[CA2241](../code-quality/ca2241.md)|必須提供格式化方法的正確引數|
|[CA2242](../code-quality/ca2242.md)|必須正確測試 NaN|
