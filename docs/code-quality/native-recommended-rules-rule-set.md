---
title: 原生建議規則規則集
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b39d47348a4587d53dbfd29cd83ce474e8848a5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070691"
---
# <a name="native-recommended-rules-rule-set"></a>原生建議規則規則集

原生建議規則的重點的最重要且常見的問題，您的原生程式碼，包括潛在的安全性漏洞和應用程式損毀。 您應該在為原生專案建立的任何自訂規則集中，包含此規則集。

|規則|描述|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|使用尚未初始化的記憶體|
|[C6011](../code-quality/c6011.md)|取值的指標為 NULL|
|[C6029](../code-quality/c6029.md)|未經確認值的使用|
|[C6031](../code-quality/c6031.md)|已忽略傳回值|
|[C6053](../code-quality/c6053.md)|呼叫中的零結尾|
|[C6054](../code-quality/c6054.md)|遺漏零結尾|
|[C6059](../code-quality/c6059.md)|不正確的串連|
|[C6063](../code-quality/c6063.md)|遺漏格式函式的字串引數|
|[C6064](../code-quality/c6064.md)|遺漏格式函式的整數引數|
|[C6066](../code-quality/c6066.md)|遺漏格式函式的指標引數|
|[C6067](../code-quality/c6067.md)|遺漏格式函式的字串指標引數|
|[C6101](../code-quality/c6101.md)|傳回未初始化的記憶體|
|[C6200](../code-quality/c6200.md)|索引超出緩衝區上限|
|[C6201](../code-quality/c6201.md)|索引超出堆疊緩衝區上限|
|[C6214](../code-quality/c6214.md)|無效的轉型為 BOOL 的 HRESULT|
|[C6215](../code-quality/c6215.md)|無效的轉型成 HRESULT 的 BOOL|
|[C6216](../code-quality/c6216.md)|無效的編譯器插入轉換成 HRESULT 的 BOOL|
|[C6217](../code-quality/c6217.md)|以 NOT 測試 HRESULT 無效|
|[C6220](../code-quality/c6220.md)|無效的 HRESULT 比作-1|
|[C6226](../code-quality/c6226.md)|無效的 HRESULT 指派為-1|
|[C6230](../code-quality/c6230.md)|無效的 HRESULT 當做布林值的使用|
|[C6235](../code-quality/c6235.md)|非零的常數，與邏輯層或|
|[C6236](../code-quality/c6236.md)|邏輯層或具有非零常數|
|[C6237](../code-quality/c6237.md)|零與邏輯層和副作用|
|[C6242](../code-quality/c6242.md)|強制區域回溯|
|[C6248](../code-quality/c6248.md)|建立 Null DACL|
|[C6250](../code-quality/c6250.md)|未釋放的位址描述元|
|[C6255](../code-quality/c6255.md)|未受保護的使用 alloca 不|
|[C6258](../code-quality/c6258.md)|使用終止執行緒|
|[C6259](../code-quality/c6259.md)|停止位元地在程式碼-或有限的交換器|
|[C6260](../code-quality/c6260.md)|使用位元組算術的|
|[C6262](../code-quality/c6262.md)|過度堆疊使用|
|[C6263](../code-quality/c6263.md)|使用 Alloca 迴圈|
|[C6268](../code-quality/c6268.md)|轉換中遺漏括號|
|[C6269](../code-quality/c6269.md)|指標取值 （dereference) 略過|
|[C6270](../code-quality/c6270.md)|遺漏格式函式的浮點引數|
|[C6271](../code-quality/c6271.md)|格式函式的多餘引數|
|[C6272](../code-quality/c6272.md)|格式函式的非浮點引數|
|[C6273](../code-quality/c6273.md)|格式函式的非整數引數|
|[C6274](../code-quality/c6274.md)|格式函式的非字元引數|
|[C6276](../code-quality/c6276.md)|無效的字串轉型|
|[C6277](../code-quality/c6277.md)|無效的 CreateProcess 呼叫|
|[C6278](../code-quality/c6278.md)|新陣列 array-new Scalar-delete 不符|
|[C6279](../code-quality/c6279.md)|純量新 scalar-new Array-delete 不符|
|[C6280](../code-quality/c6280.md)|記憶體 Allocation-deallocation 不符|
|[C6281](../code-quality/c6281.md)|位元關係優先順序|
|[C6282](../code-quality/c6282.md)|指派取代測試|
|[C6283](../code-quality/c6283.md)|基本的陣列新 array-new Scalar-delete 不符|
|[C6284](../code-quality/c6284.md)|格式函式的物件引數無效|
|[C6285](../code-quality/c6285.md)|邏輯層或常數|
|[C6286](../code-quality/c6286.md)|非零邏輯層或遺失的副作用|
|[C6287](../code-quality/c6287.md)|多餘的測試|
|[C6288](../code-quality/c6288.md)|互容的情況下使用邏輯層和為 False|
|[C6289](../code-quality/c6289.md)|透過邏輯互斥-或為 True|
|[C6290](../code-quality/c6290.md)|邏輯 NOT 位元 AND 優先順序|
|[C6291](../code-quality/c6291.md)|邏輯 NOT 位元 OR 優先順序|
|[C6292](../code-quality/c6292.md)|迴圈會從最大值向上|
|[C6293](../code-quality/c6293.md)|迴圈從最小值向下計數|
|[C6294](../code-quality/c6294.md)|永遠不會執行迴圈主體|
|[C6295](../code-quality/c6295.md)|無限的迴圈|
|[C6296](../code-quality/c6296.md)|只執行一次的迴圈|
|[C6297](../code-quality/c6297.md)|位移的結果轉換成較大的大小|
|[C6299](../code-quality/c6299.md)|布林比較的位元欄位|
|[C6302](../code-quality/c6302.md)|格式函式的字元字串引數無效|
|[C6303](../code-quality/c6303.md)|格式函式的寬字元字串引數無效|
|[C6305](../code-quality/c6305.md)|大小和計數用法不符|
|[C6306](../code-quality/c6306.md)|不正確的變數引數函式呼叫|
|[C6308](../code-quality/c6308.md)|Realloc 流失|
|[C6310](../code-quality/c6310.md)|不合法的例外狀況篩選條件常數|
|[C6312](../code-quality/c6312.md)|例外狀況繼續執行迴圈|
|[C6314](../code-quality/c6314.md)|位元的 Or 優先順序|
|[C6317](../code-quality/c6317.md)|不是否定補數|
|[C6318](../code-quality/c6318.md)|例外狀況繼續搜尋|
|[C6319](../code-quality/c6319.md)|被逗號忽略|
|[C6324](../code-quality/c6324.md)|字串複製，而不是字串比較|
|[C6328](../code-quality/c6328.md)|引數類型可能不符|
|[C6331](../code-quality/c6331.md)|VirtualFree 無效旗標|
|[C6332](../code-quality/c6332.md)|VirtualFree 無效參數|
|[C6333](../code-quality/c6333.md)|VirtualFree 無效大小|
|[C6335](../code-quality/c6335.md)|流失處理序控制代碼|
|[C6381](../code-quality/c6381.md)|遺漏關閉資訊|
|[C6383](../code-quality/c6383.md)|項目計數位元組-計數緩衝區滿溢|
|[C6384](../code-quality/c6384.md)|指標大小除數|
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
|[C6527](../code-quality/c6527.md)|無效的附註：'NeedsRelease' 屬性不能用於 void 類型的值|
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
|[C26100](../code-quality/c26100.md)|競爭情形|
|[C26101](../code-quality/c26101.md)|若要正確使用連鎖的作業失敗|
|[C26110](../code-quality/c26110.md)|呼叫端無法保留鎖定|
|[C26111](../code-quality/c26111.md)|呼叫端無法釋放鎖定|
|[C26112](../code-quality/c26112.md)|呼叫端無法保留任何鎖定|
|[C26115](../code-quality/c26115.md)|無法釋放鎖定|
|[C26116](../code-quality/c26116.md)|無法取得，或保留鎖定|
|[C26117](../code-quality/c26117.md)|釋放未保留的鎖定|
|[C26140](../code-quality/c26140.md)|並行 SAL 註釋錯誤|
|[C26441](../code-quality/c26441.md)|NO_UNNAMED_GUARDS|
|[C26444](../code-quality/c26444.md)|NO_UNNAMED_RAII_OBJECTS|
|[C26498](../code-quality/c26498.md)|USE_CONSTEXPR_FOR_FUNCTIONCALL|
|[C28020](../code-quality/c28020.md)|運算式不是在此呼叫，則為 true|
|[C28021](../code-quality/c28021.md)|所標註的參數必須是指標|
|[C28022](../code-quality/c28022.md)|函式類別，這個函式上的不符合定義它所用之 typedef 上的函式類別。|
|[C28023](../code-quality/c28023.md)|要指派或傳遞的函式應有\_函式\_類別\_至少一個類別的註釋|
|[C28024](../code-quality/c28024.md)|要指派的函式指標並未包含在函式類別清單的函式類別，附註。|
|[C28039](../code-quality/c28039.md)|實際的參數類型應完全符合類型|
|[C28112](../code-quality/c28112.md)|透過 Interlocked 函式時，必須一律存取透過 Interlocked 函式存取的變數。|
|[C28113](../code-quality/c28113.md)|存取區域變數透過 Interlocked 函式|
|[C28125](../code-quality/c28125.md)|Try / except 區塊內，必須從呼叫函式|
|[C28137](../code-quality/c28137.md)|變數引數應改成 （常值） 常數|
|[C28138](../code-quality/c28138.md)|常數的引數應該改為變數|
|[C28159](../code-quality/c28159.md)|請考慮改用其他函式。|
|[C28160](../code-quality/c28160.md)|Error 註釋|
|[C28163](../code-quality/c28163.md)|呼叫函式應該永遠不會從 try / except 區塊內|
|[C28164](../code-quality/c28164.md)|引數已傳遞至需要的物件 （而非指標的指標） 的指標的函式|
|[C28182](../code-quality/c28182.md)|取值的指標為 NULL。 指標所包含的 NULL 值與另一個指標相同。|
|[C28183](../code-quality/c28183.md)|引數可以是一個值，並在指標中找到之值的複本|
|[C28193](../code-quality/c28193.md)|變數持有必須檢查的值|
|[C28196](../code-quality/c28196.md)|未滿足需求。 （運算式不會評估為 true。）|
|[C28202](../code-quality/c28202.md)|非靜態成員的參考不合法|
|[C28203](../code-quality/c28203.md)|類別成員的參考模稜兩可。|
|[C28205](../code-quality/c28205.md)|\_成功\_或是\_上\_失敗\_不合法的內容中使用|
|[C28206](../code-quality/c28206.md)|左運算元指向結構，請使用 '->'|
|[C28207](../code-quality/c28207.md)|左運算元是結構，請使用 '.'|
|[C28209](../code-quality/c28209.md)|符號的宣告有衝突的宣告|
|[C28210](../code-quality/c28210.md)|_On_failure_ 內容的註釋不能在明確 pre context 中|
|[C28211](../code-quality/c28211.md)|SAL_context 需要靜態內容名稱|
|[C28212](../code-quality/c28212.md)|註釋需要指標運算式|
|[C28213](../code-quality/c28213.md)|\_使用\_decl-modifier\_註釋\_註解必須用來參考，不需修改之前的宣告。|
|[C28214](../code-quality/c28214.md)|屬性參數名稱必須是 p1...p9|
|[C28215](../code-quality/c28215.md)|typefix 不能套用到已經有 typefix 的參數|
|[C28216](../code-quality/c28216.md)|checkReturn 註釋只適用於特定函式參數的後置條件。|
|[C28217](../code-quality/c28217.md)|對於函式，註釋的參數數目不符合檔案中找到的參數數目|
|[C28218](../code-quality/c28218.md)|函式參數，註釋的參數不符合找到的檔案|
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
|[C28244](../code-quality/c28244.md)|函式的註釋具有無法剖析的參數/外部註釋|
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
|[C28275](../code-quality/c28275.md)|參數\_巨集\_值\_為 null|
|[C28279](../code-quality/c28279.md)|找到符號的 'begin'，但沒有相符的 'end'|
|[C28280](../code-quality/c28280.md)|找到符號的 'end'，但沒有相符的 'begin'|
|[C28282](../code-quality/c28282.md)|格式字串必須在前置條件中|
|[C28285](../code-quality/c28285.md)|對於函式，參數中有語法錯誤|
|[C28286](../code-quality/c28286.md)|對於函式，結尾附近發生語法錯誤|
|[C28287](../code-quality/c28287.md)|函式的 \_At\_() 註釋中有語法錯誤 (無法辨認的參數名稱)|
|[C28288](../code-quality/c28288.md)|函式的 \_At\_() 註釋中有語法錯誤 (無效的參數名稱)|
|[C28289](../code-quality/c28289.md)|函式：ReadableTo 或 WritableTo 沒有規格做為參數|
|[C28290](../code-quality/c28290.md)|函式的註釋包含比實際參數數目還多的外部|
|[C28291](../code-quality/c28291.md)|位於 deref 層級 0 的 post null/notnull 對函式是無意義的。|
|[C28300](../code-quality/c28300.md)|運算子的運算式運算元類型不相容|
|[C28301](../code-quality/c28301.md)|函式的第一個宣告沒有註釋。|
|[C28302](../code-quality/c28302.md)|在註釋中發現額外的 \_Deref\_ 運算子。|
|[C28303](../code-quality/c28303.md)|在註釋發現模擬兩可的 \_Deref\_ 運算子。|
|[C28304](../code-quality/c28304.md)|發現有位置不正確的 \_Notref\_ 運算子套用至語彙基元。|
|[C28305](../code-quality/c28305.md)|剖析語彙基元時發現錯誤。|
|[C28306](../code-quality/c28306.md)|參數上的註釋已廢棄|
|[C28307](../code-quality/c28307.md)|參數上的註釋已廢棄|
|[C28350](../code-quality/c28350.md)|註釋描述了條件不適用的狀況。|
|[C28351](../code-quality/c28351.md)|註釋描述條件中不可以使用動態值 (變數)。|