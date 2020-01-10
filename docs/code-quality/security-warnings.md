---
title: 安全性警告
ms.date: 10/02/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.securityrules
helpviewer_keywords:
- security [Visual Studio ALM], Enterprise Templates
- security warnings
- managed code analysis warnings, security warnings
- warnings, security
ms.assetid: 60d4e8ea-230a-494f-aa6a-b91db77540e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 004f10600df3ed2f9c1f62557e0915638482877e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587208"
---
# <a name="security-warnings"></a>安全性警告

支援更安全之程式庫和應用程式的安全性警告。 這些警告有助於防止在程式中出現安全性問題。 如果停用這些警告中的任一個，則您應該清楚地在程式碼中標示理由，同時也要通知指定的安全主管有關您的開發專案。

## <a name="in-this-section"></a>本節內容

|規則|描述|
|----------|-----------------|
|[CA2100：必須檢閱 SQL 查詢中是否有安全性弱點](../code-quality/ca2100.md)|方法會使用透過字串引數所建置的字串，將 System.Data.IDbCommand.CommandText 屬性設定為方法。 這項規則假設字串引數包含使用者輸入。 從使用者輸入所建置的 SQL 命令字串很容易遭到 SQL 插入攻擊。|
|[CA2102：必須使用一般處理常式攔截非 CLSCompliant 例外狀況](../code-quality/ca2102.md)|組件中不是以 RuntimeCompatibilityAttribute 標記或是以 RuntimeCompatibility(WrapNonExceptionThrows = false) 標記的成員包含處理 System.Exception 的 catch 區塊，同時不包含緊接其後的一般 catch 區塊。|
|[CA2103：必須檢閱命令式安全性](../code-quality/ca2103.md)|方法會使用命令式安全性，而且可能會利用因要求正在使用中而可能變更的狀態資訊或傳回值建構使用權限。 請盡可能使用宣告式安全性。|
|[CA2104：不要宣告唯讀的可變動參考類型](../code-quality/ca2104.md)|外部可見類型包含了可變動參考類型的外部可見唯讀欄位。 可變動類型是可以修改執行個體資料的類型。|
|[CA2105：陣列欄位不應該為唯讀](../code-quality/ca2105.md)|當您將唯讀 (在 Visual Basic 中為 ReadOnly) 修飾詞套用至包含陣列的欄位時，欄位就不能變更為參考不同的陣列。 但是，儲存在唯讀欄位的陣列元素則可以變更。|
|[CA2106：必須保護判斷提示](../code-quality/ca2106.md)|方法會判斷提示使用權限，而且不會在呼叫端上執行安全性檢查。 判斷提示安全性權限但未執行任何安全性檢查，會在您的程式碼中留下可能遭利用的安全性弱點。|
|[CA2107：必須檢視 Deny 和 Permit Only 的使用方式](../code-quality/ca2107.md)|使用 PermitOnly 方法和 Codeaccesspermission.deny 時，只能由具有 .NET 安全性之 advanced 知識的安全性動作使用。 而使用這些安全性動作的程式碼應該接受安全性檢閱。|
|[CA2108：必須檢查實值型別上的宣告式安全性](../code-quality/ca2108.md)|公用或受保護的實值類型受到資料存取或連結要求保護。|
|[CA2109：必須檢閱可見的事件處理常式](../code-quality/ca2109.md)|偵測到公用或保護的事件處理方法。 除非有絕對的必要性，否則不應該公開事件處理方法。|
|[CA2111：指標不應該為可見的](../code-quality/ca2111.md)|指標不為私用、內部或唯讀。 惡意的程式碼可變更指標值，進而可能會允許存取記憶體中的任意位置，或是造成應用程式或系統失敗。|
|[CA2112：受保護類型不應該公開欄位](../code-quality/ca2112.md)|公用或受保護的類型包含公用欄位，而且受到連結要求保護。 如果程式碼可存取受連結要求保護的類型執行個體，則程式碼不必滿足連結要求即可存取類型的欄位。|
|[CA2114：方法安全性應該是類型的超集](../code-quality/ca2114.md)|方法不應該同時具有相同動作的方法層級和類型層級宣告式安全性。|
|[CA2115：使用原生資源時必須呼叫 GC.KeepAlive](../code-quality/ca2115.md)|此規則所偵測的錯誤，可能是因為在 Unmanaged 程式碼仍在使用 Unmanaged 資源時，就完成 Unmanaged 資源所致。|
|[CA2116：APTCA 方法應該只呼叫 APTCA 方法](../code-quality/ca2116.md)|當完全信任的組件中出現 APTCA (AllowPartiallyTrustedCallers) 屬性，並且組件在不允許部分信任呼叫端的另一個組件中執行程式碼時，可能會發生安全性弱點攻擊。|
|[CA2117：APTCA 類型應該只擴充 APTCA 基底類型](../code-quality/ca2117.md)|當完全信任的組件中出現 APTCA (AllowPartiallyTrustedCallers) 屬性，並且組件中的類型會繼承自不允許部分信任之呼叫端的類型時，就可能會發生安全性弱點攻擊。|
|[CA2118：檢閱 SuppressUnmanagedCodeSecurityAttribute 使用方法](../code-quality/ca2118.md)|對於執行使用 COM Interop 或平台引動過程之 Unmanaged 程式碼的成員，SuppressUnmanagedCodeSecurityAttribute 會變更安全性系統的預設行為。 這個屬性主要是用於增加效能，不過，效能提升會伴隨顯著的安全性風險。|
|[CA2119：密封方法以滿足私用介面的要求](../code-quality/ca2119.md)|可繼承的公用類型會提供內部 (在 Visual Basic 中為 Friend) 介面的可覆寫方法實作。 若要修正此規則的違規情形，請避免在組件外覆寫方法。|
|[CA2120：必須保護序列化建構函式](../code-quality/ca2120.md)|這個類型有接受 System.Runtime.Serialization.SerializationInfo 物件和 System.Runtime.Serialization.StreamingContext 物件 (序列化建構函式的簽章) 的建構函式。 這個建構函式未受到安全性檢查的保護，但類型中有一個或多個規則建構函式是受到保護的。|
|[CA2121：靜態建構函式應為私用](../code-quality/ca2121.md)|系統會在建立類型的第一個執行個體或參考任何靜態成員之前呼叫靜態建構函式。 如果靜態建構函式不是私用的，則可由系統以外的程式碼呼叫。 視建構函式中執行的作業而定，這會造成非預期的行為。|
|[CA2122：不要間接公開具有連結要求的方法](../code-quality/ca2122.md)|公用或受保護的成員具有連結要求，而且是由未執行任何安全性檢查的成員所呼叫。 連結要求只會檢查立即呼叫端的使用權限。|
|[CA2123：覆寫連結要求應該與基底相同](../code-quality/ca2123.md)|這項規則會使方法符合它的基底方法，即另一個類型中的介面或虛擬方法，然後比較每個方法上的連結要求。 如果違反這項規則，則惡意呼叫端只需呼叫不安全的方法，就可以略過連結要求。|
|[CA2124：必須將有弱點的 finally 子句包裝在外層 try 中](../code-quality/ca2124.md)|公用或受保護的方法包含 try/finally 區塊。 finally 區塊似乎會重設安全性狀態，而且不會封入 finally 區塊中。|
|[CA2126：必須同時具有類型連結要求和繼承要求](../code-quality/ca2126.md)|公用 unsealed 類型受到連結要求保護，並且具有可以覆寫的方法。 此類型或方法都不是以繼承要求保護的。|
|[CA2130：安全性關鍵常數應該是透明的](../code-quality/ca2130.md)|因為編譯器內嵌常數的值，所以沒有針對常數值強制透明度，因此在執行階段不需要查詢。 常數欄位應該具備安全性透明，程式碼檢閱者才不會假設透明程式碼無法存取常數。|
|[CA2131：安全性關鍵類型可能未參與類型等價](../code-quality/ca2131.md)|類型會參與類型等價，而類型本身或類型的成員或欄位會以 SecurityCriticalAttribute 屬性標記。 此規則會引發任何關鍵的類型或包含參與類型等價之關鍵方法或欄位的類型。 當 CLR 偵測到這種類型時，它便無法載入此類型，而且會在執行階段發生 TypeLoadException。 通常，只有在使用者手動實作類型等價，而不是依賴 tlbimp 和編譯器進行類型等價時，就會引發這項規則。|
|[CA2132：預設建構函式至少必須和基底類型的預設建構函式一樣關鍵](../code-quality/ca2132.md)|Silverlight 應用程式的程式碼不能使用內含 SecurityCriticalAttribute 的類型和成員。 重視安全性的類型以及成員，只能夠由 .NET Framework for Silverlight 類別庫中的受信任程式碼使用。 由於衍生類別中的公用或受保護建構所具有的透明度必須大於或等於其基底類別，因此應用程式中的類別不可衍生自標記為 SecurityCritical 的類別。|
|[CA2133：委派必須繫結至具有一致透明度的方法](../code-quality/ca2133.md)|當方法會將使用 SecurityCriticalAttribute 標記的委派繫結到透明方法，或繫結到使用 SecuritySafeCriticalAttribute 標記的方法時，就會針對此方法引發警告。 此警告也會引發將透明或安全關鍵性的委派繫結至關鍵方法的方法。|
|[CA2134：覆寫基底方法時，方法必須保持一致的透明度](../code-quality/ca2134.md)|當使用 SecurityCriticalAttribute 標記的方法覆寫透明方法，或覆寫使用 SecuritySafeCriticalAttribute 標記的方法時，就會引發此規則。 當透明或使用 SecuritySafeCriticalAttribute 標記的方法覆寫使用 SecurityCriticalAttribute 標記的方法時，也會引發此規則。 覆寫虛擬方法或實作介面時會套用此規則。|
|[CA2135：層級 2 組件不應該包含 LinkDemand](../code-quality/ca2135.md)|LinkDemand 在層級 2 安全性規則集中已被取代。 不使用 LinkDemand 在 Just-In-Time (JIT) 編譯時期強制執行安全性，改為使用 SecurityCriticalAttribute 屬性來標記方法、類型和欄位。|
|[CA2136：成員不應該具有衝突的透明度註釋](../code-quality/ca2136.md)|透明度屬性會從較大範圍的程式碼項目套用至較小範圍的項目。 範圍較大之程式碼項目的透明度屬性優先於第一個項目中所包含之程式碼項目的透明度屬性。 例如，使用 SecurityCriticalAttribute 屬性來標記的類別不得包含使用 SecuritySafeCriticalAttribute 屬性來標記的方法。|
|[CA2137：透明方法必須只包含可驗證的 IL](../code-quality/ca2137.md)|方法包含無法驗證的程式碼，或以傳址方式傳回類型。 當安全性透明程式碼嘗試執行無法驗證的 MSIL (Microsoft Intermediate Language) 時，就會引發此規則。 不過，此規則不包含完整的 IL 驗證器，並是使用啟發式來擷取多數的 MSIL 驗證違規情形。|
|[CA2138：透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法](../code-quality/ca2138.md)|安全性透明方法會呼叫使用 SuppressUnmanagedCodeSecurityAttribute 屬性標記的方法。|
|[CA2139：透明方法不能使用 HandleProcessCorruptingExceptions 屬性](../code-quality/ca2139.md)|此規則會在任何透明的方法上引發，並嘗試使用 HandleProcessCorruptedStateExceptionsAttribute 屬性來處理進程損毀例外狀況。 進程損毀例外狀況是 CLR 版本4.0 例外狀況分類，例如 <xref:System.AccessViolationException>。 HandleProcessCorruptedStateExceptionsAttribute 屬性只能供安全性關鍵方法使用，若套用至透明方法則會被忽略。|
|[CA2140：透明程式碼不可以參考安全性關鍵項目](../code-quality/ca2140.md)|以 SecurityTransparentAttribute 標記的方法可呼叫標記為 SecurityCritical 的非公用成員。 此規則會分析混合透明和重要之元件中的所有方法和類型，並將任何透明程式碼的呼叫標記為未標記為 SecurityTreatAsSafe 的非公用關鍵程式碼。|
|[CA2141：透明方法不可以滿足 LinkDemand](../code-quality/ca2141.md)|安全性透明方法會呼叫未使用 AllowPartiallyTrustedCallersAttribute (APTCA) 屬性標記之組件中的方法，或是安全性透明方法會滿足類型或方法的 LinkDemand。|
|[CA2142：透明程式碼不可以使用 LinkDemand 加以保護](../code-quality/ca2142.md)|需要 LinkDemand 才能存取的透明方法會引發這個規則。 安全性透明程式碼不應負責驗證作業的安全性，因此不應要求權限。|
|[CA2143：透明方法不可以使用安全性要求](../code-quality/ca2143.md)|安全性透明程式碼不應負責驗證作業的安全性，因此不應要求權限。 安全性透明程式碼應使用完整的要求做出安全性決策，而且安全關鍵程式碼不應依賴透明程式碼提出完全要求。|
|[CA2144：透明程式碼不可以從位元組陣列載入組件](../code-quality/ca2144.md)|透明程式碼的安全性檢閱不如關鍵性程式碼的安全性檢閱徹底，因為透明程式碼無法執行安全性敏感動作。 透明程式碼中可能不會注意到從位元組陣列載入的組件，而該位元組陣列可能包含需要稽核之重大或更重要的安全關鍵性程式碼。|
|[CA2145：透明方法不可以使用 SuppressUnmanagedCodeSecurityAttribute 來裝飾](../code-quality/ca2145.md)|以 SuppressUnmanagedCodeSecurityAttribute 屬性裝飾的方法會在任何方法呼叫它時放置隱含的 LinkDemand。 這個 LinkDemand 會要求呼叫程式碼具備安全性關鍵。 使用 SecurityCriticalAttribute 屬性來標記使用 SuppressUnmanagedCodeSecurity 的方法會使方法呼叫端的這個需求更為明顯。|
|[CA2146：類型至少必須和基底類型與介面一樣關鍵](../code-quality/ca2146.md)|當衍生類型有安全性透明屬性，且該屬性的重要性不如基底類型或已實作之介面時，就會引發這個規則。 只有關鍵類型可以衍生自關鍵基底類型或實作關鍵介面，而且只有關鍵或安全關鍵類型可以衍生自安全關鍵基底類型或實作安全關鍵介面。|
|[CA2147：透明方法不可以使用安全性判斷提示](../code-quality/ca2147.md)|此規則會分析完全透明或混合透明/關鍵之組件中的所有方法和類型，並將 Assert 的任何宣告式或必要用法加上旗標。|
|[CA2149：透明方法不可以呼叫機器碼](../code-quality/ca2149.md)|此規則會在直接呼叫機器碼（例如透過 P/Invoke）的任何透明方法上引發。 違反此規則會導致層級 2 透明度模型出現 MethodAccessException，而在層級 1 透明度模型會出現對 UnmanagedCode 的完整要求。|
|[CA2151：具有關鍵類型的欄位應為安全性關鍵](../code-quality/ca2151.md)|若要使用安全性關鍵類型，參考該類型的程式碼必須是安全性關鍵或安全性安全關鍵。 即使是間接參考也是如此。 因此，使用安全性透明或安全性安全關鍵欄位容易發生錯誤，因為透明程式碼仍然無法存取該欄位。|
|[CA2153：避免處理損毀狀態例外狀況](../code-quality/ca2153.md)|[損毀狀態例外狀況 (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) 指出您的處理序中有記憶體損毀的狀況。 如果攻擊者將攻擊放入損毀的記憶體區域，則攔截這些處理序而非讓它們損毀，會導致安全性弱點。|
|[CA2300：不要使用不安全的還原序列化 BinaryFormatter](../code-quality/ca2300.md)|還原序列化不受信任的資料時，不安全的還原序列化程式會受到攻擊。 攻擊者可以修改序列化資料，使其包含非預期的類型，以插入具有惡意副作用的物件。|
|[CA2301：請勿呼叫 BinaryFormatter，而不先設定 BinaryFormatter。](../code-quality/ca2301.md)|還原序列化不受信任的資料時，不安全的還原序列化程式會受到攻擊。 攻擊者可以修改序列化資料，使其包含非預期的類型，以插入具有惡意副作用的物件。|
|[CA2302：請先確定已設定 BinaryFormatter，再呼叫 BinaryFormatter。還原序列化](../code-quality/ca2302.md)|還原序列化不受信任的資料時，不安全的還原序列化程式會受到攻擊。 攻擊者可以修改序列化資料，使其包含非預期的類型，以插入具有惡意副作用的物件。|
|[CA2305：不要使用不安全的還原序列化 LosFormatter](../code-quality/ca2305.md)|還原序列化不受信任的資料時，不安全的還原序列化程式會受到攻擊。 攻擊者可以修改序列化資料，使其包含非預期的類型，以插入具有惡意副作用的物件。|
|[CA2310：不要使用不安全的還原序列化 NetDataContractSerializer](../code-quality/ca2310.md)|還原序列化不受信任的資料時，不安全的還原序列化程式會受到攻擊。 攻擊者可以修改序列化資料，使其包含非預期的類型，以插入具有惡意副作用的物件。|
|[CA2311：不先設定 NetDataContractSerializer 就不要還原序列化](../code-quality/ca2311.md)|還原序列化不受信任的資料時，不安全的還原序列化程式會受到攻擊。 攻擊者可以修改序列化資料，使其包含非預期的類型，以插入具有惡意副作用的物件。|
|[CA2312：確定已在還原序列化之前設定 NetDataContractSerializer](../code-quality/ca2312.md)|還原序列化不受信任的資料時，不安全的還原序列化程式會受到攻擊。 攻擊者可以修改序列化資料，使其包含非預期的類型，以插入具有惡意副作用的物件。|
|[CA2315：不要使用不安全的還原序列化 ObjectStateFormatter](../code-quality/ca2315.md)|還原序列化不受信任的資料時，不安全的還原序列化程式會受到攻擊。 攻擊者可以修改序列化資料，使其包含非預期的類型，以插入具有惡意副作用的物件。|
|[CA2321：不要使用 SimpleTypeResolver 還原序列化 JavaScriptSerializer](../code-quality/ca2321.md)|還原序列化不受信任的資料時，不安全的還原序列化程式會受到攻擊。 攻擊者可以修改序列化資料，使其包含非預期的類型，以插入具有惡意副作用的物件。|
|[CA2322：確保在還原序列化之前，JavaScriptSerializer 不會以 SimpleTypeResolver 初始化](../code-quality/ca2322.md)|還原序列化不受信任的資料時，不安全的還原序列化程式會受到攻擊。 攻擊者可以修改序列化資料，使其包含非預期的類型，以插入具有惡意副作用的物件。|
|[CA2326：不使用 None 以外的 TypeNameHandling 值](../code-quality/ca2326.md)|還原序列化不受信任的資料時，不安全的還原序列化程式會受到攻擊。 攻擊者可以修改序列化資料，使其包含非預期的類型，以插入具有惡意副作用的物件。|
|[CA2327：不要使用不安全的 JsonSerializerSettings](../code-quality/ca2327.md)|還原序列化不受信任的資料時，不安全的還原序列化程式會受到攻擊。 攻擊者可以修改序列化資料，使其包含非預期的類型，以插入具有惡意副作用的物件。|
|[CA2328：確保 JsonSerializerSettings 是安全的](../code-quality/ca2328.md)|還原序列化不受信任的資料時，不安全的還原序列化程式會受到攻擊。 攻擊者可以修改序列化資料，使其包含非預期的類型，以插入具有惡意副作用的物件。|
|[CA2329：請勿使用不安全的設定來還原序列化 JsonSerializer](../code-quality/ca2329.md)|還原序列化不受信任的資料時，不安全的還原序列化程式會受到攻擊。 攻擊者可以修改序列化資料，使其包含非預期的類型，以插入具有惡意副作用的物件。|
|[CA2330：在還原序列化時，確保 JsonSerializer 具有安全設定](../code-quality/ca2330.md)|還原序列化不受信任的資料時，不安全的還原序列化程式會受到攻擊。 攻擊者可以修改序列化資料，使其包含非預期的類型，以插入具有惡意副作用的物件。|
|[CA3001：審查 SQL 插入式弱點的程式碼](../code-quality/ca3001.md)|使用不受信任的輸入和 SQL 命令時，請留意 SQL 插入式攻擊。 SQL 插入式攻擊可能會執行惡意的 SQL 命令，因而危及應用程式的安全性和完整性。|
|[CA3002：審查 XSS 弱點的程式碼](../code-quality/ca3002.md)|使用來自 web 要求的未受信任輸入時，請留意跨網站腳本（XSS）攻擊。 XSS 攻擊會將不受信任的輸入插入原始 HTML 輸出中，讓攻擊者能夠執行惡意腳本或惡意修改網頁中的內容。|
|[CA3003：檢查檔案路徑插入弱點的程式碼](../code-quality/ca3003.md)|當您使用來自 web 要求的未受信任輸入時，請留意在指定檔案路徑時使用使用者控制的輸入。|
|[CA3004：審查程式碼中的資訊洩漏弱點](../code-quality/ca3004.md)|公開例外狀況資訊可讓攻擊者深入瞭解應用程式的內部，以協助攻擊者找出其他弱點來入侵。|
|[CA3006：審查程式命令插入弱點的程式碼](../code-quality/ca3006.md)|使用不受信任的輸入時，請注意命令插入式攻擊。 命令插入式攻擊可以在基礎作業系統上執行惡意命令，因而危及伺服器的安全性和完整性。|
|[CA3007：檢查開啟重新導向弱點的程式碼](../code-quality/ca3007.md)|使用不受信任的輸入時，請留意開啟的重新導向弱點。 攻擊者可以利用開啟的重新導向弱點，使用您的網站提供合法 URL 的外觀，但是將不受歡迎的訪客重新導向至網路釣魚或其他惡意網頁。|
|[CA3008：檢查 XPath 插入弱點的程式碼](../code-quality/ca3008.md)|使用不受信任的輸入時，請注意 XPath 插入式攻擊。 使用不受信任的輸入來建立 XPath 查詢，可能會讓攻擊者惡意地操作查詢，以傳回非預期的結果，而且可能會洩漏所查詢 XML 的內容。|
|[CA3009：審查 XML 插入式弱點的程式碼](../code-quality/ca3009.md)|使用不受信任的輸入時，請留意 XML 插入式攻擊。|
|[CA3010：審查 XAML 插入式弱點的程式碼](../code-quality/ca3010.md)|使用不受信任的輸入時，請注意 XAML 插入式攻擊。 XAML 是直接表示物件執行個體化和執行的標記語言。 這表示在 XAML 中建立的元素可以與系統資源（例如，網路存取和檔案系統 IO）互動。|
|[CA3011：檢查 DLL 插入弱點的程式碼](../code-quality/ca3011.md)|使用不受信任的輸入時，請注意載入不受信任的程式碼。 如果您的 web 應用程式載入不受信任的程式碼，攻擊者可能可以將惡意 Dll 插入您的進程，並執行惡意程式碼。|
|[CA3012：查看 RegEx 插入弱點的程式碼](../code-quality/ca3012.md)|使用不受信任的輸入時，請注意 RegEx 插入式攻擊。 攻擊者可以使用 RegEx 插入來惡意修改正則運算式，讓 RegEx 符合非預期的結果，或讓 RegEx 耗用過多的 CPU，因而導致阻絕服務攻擊。|
|[CA3061：不要依 URL 新增架構](../code-quality/ca3061.md)|請勿使用 Add 方法的 unsafe 多載，因為它可能會導致危險的外部參考。|
|[CA3075：不安全的 DTD 處理](../code-quality/ca3075.md)|如果您使用不安全的 DTDProcessing 執行個體或參考外部實體來源，剖析器可能會接受未受信任的輸入，而將機密資訊洩漏給攻擊者。|
|[CA3076：不安全的 XSLT 指令碼執行](../code-quality/ca3076.md)|如果您在 .NET 應用程式中以不安全的方式執行 Extensible Stylesheets Language Transformations (XSLT) (可延伸樣式表語言轉換 (XSLT))，處理器可能會解析不受信任的 URI 參考，而這些參考可能會將機密資訊洩漏給攻擊者，導致拒絕服務和跨網站攻擊。|
|[CA3077：API 設計、XML 文件和 XML 文字讀取器中的不安全處理](../code-quality/ca3077.md)|針對衍生自 XMLDocument 和 XMLTextReader 的 API 進行設計時，請留意 DtdProcessing。 若在參考或解析外部實體來源時使用不安全的 DTDProcessing 執行個體，或在 XML 中設定不安全的值，都可能會導致資訊洩漏。|
|[CA3147：使用 ValidateAntiForgeryToken 標記動詞處理常式](../code-quality/ca3147.md)|在設計 ASP.NET MVC 控制器時，請注意跨網站偽造要求攻擊。 跨網站要求偽造攻擊可能會將來自已驗證使用者的惡意要求傳送至您的 ASP.NET MVC 控制器。|
|[CA5122 P-Invoke 宣告不應為安全關鍵](../code-quality/ca5122.md)|在執行安全性敏感作業時，會將方法標記為 SecuritySafeCritical，但透明程式碼也能安全地使用。 透明程式碼不可直接透過 P/Invoke 呼叫機器碼。 因此，即使將 P/Invoke 標示為安全性安全關鍵，透明程式碼仍然不能呼叫它，而且會導致安全性分析錯誤。|
|[CA5361：不要停用安全加密的 SChannel 使用](../code-quality/ca5361.md)|將 `Switch.System.Net.DontEnableSchUseStrongCrypto` 設定為 `true` 削弱用於傳出傳輸層安全性（TLS）連線的密碼編譯。 較弱的密碼編譯可能會危害您的應用程式與伺服器之間的通訊機密性，讓攻擊者更容易竊聽敏感性資料。|
|[CA5363：不要停用要求驗證](../code-quality/ca5363.md)|要求驗證是 ASP.NET 中的一項功能，可檢查 HTTP 要求，並判斷它們是否包含可能會導致插入式攻擊的潛在危險內容，包括跨網站腳本。|
|[CA5364：不要使用已淘汰的安全性通訊協定](../code-quality/ca5364.md)|傳輸層安全性（TLS）可保護電腦之間的通訊，最常見的方式是使用超文字安全傳輸通訊協定（HTTPS）。 舊版的 TLS 通訊協定版本比 TLS 1.2 和 TLS 1.3 低，而且更有可能會有新的弱點。 避免較舊的通訊協定版本，將風險降至最低。|
|[CA5369：使用 XmlReader 進行還原序列化](../code-quality/ca5369.md)|處理不受信任的 DTD 和 XML 架構可能會啟用載入危險的外部參考，這應該使用具有安全解析程式的 XmlReader，或停用 DTD 和 XML 內嵌架構處理來加以限制。|
|[CA5370：使用 XmlReader 來驗證讀取器](../code-quality/ca5370.md)|處理不受信任的 DTD 和 XML 架構可能會啟用載入危險的外部參考。 這項危險的載入可以藉由使用具有安全解析程式的 XmlReader，或在停用 DTD 和 XML 內嵌架構處理的情況下受到限制。|
|[CA5371：使用 XmlReader 讀取架構](../code-quality/ca5371.md)|處理不受信任的 DTD 和 XML 架構可能會啟用載入危險的外部參考。 使用具有安全解析程式的 XmlReader，或已停用 DTD 和 XML 內嵌架構處理時，會限制這種情況。|
|[CA5372：針對 XPathDocument 使用 XmlReader](../code-quality/ca5372.md)|從不受信任的資料處理 XML 可能會載入危險的外部參考，這可以透過使用具有安全解析程式的 XmlReader 或停用 DTD 處理來加以限制。|
|[CA5373：不要使用過時的金鑰衍生函式](../code-quality/ca5373.md)|此規則會偵測 <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> 和 `Rfc2898DeriveBytes.CryptDeriveKey`的弱式金鑰衍生方法調用。 <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> 使用弱式演算法 PBKDF1。|
|[CA5378：不要停用 ServicePointManagerSecurityProtocols](../code-quality/ca5378.md)|將 `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` 設定為 `true` 會限制使用 TLS 1.0 的 Windows Communication Framework （WCF）傳輸層安全性（TLS）連線。 該 TLS 版本將會被取代。|
|[CA5380：不要將憑證新增至根存放區](../code-quality/ca5380.md)|此規則會偵測將憑證新增至「信任的根憑證授權單位」憑證存放區的程式碼。 根據預設，「信任的根憑證授權單位」憑證存放區是以一組已符合「Microsoft 根憑證計畫」需求的公用 Ca 來設定。|
|[CA5381：確保憑證不會新增至根存放區](../code-quality/ca5381.md)|此規則會偵測可能將憑證新增至「信任的根憑證授權單位」憑證存放區的程式碼。 根據預設，信任的根憑證授權單位憑證存放區是以一組已符合 Microsoft 根憑證計畫需求的公開憑證授權單位單位（Ca）來設定。|
|[CA5386：避免硬式編碼 Securityprotocoltype.tls11 值](../code-quality/ca5386.md)|傳輸層安全性（TLS）可保護電腦之間的通訊，最常見的方式是使用超文字安全傳輸通訊協定（HTTPS）。 Tls 1.0 和 TLS 1.1 的通訊協定版本已被取代，而 TLS 1.2 和 TLS 1.3 是最新的。 未來，TLS 1.2 和 TLS 1.3 可能會被取代。 若要確保您的應用程式保持安全，請避免硬式編碼通訊協定版本，並以至少 .NET Framework v 4.7.1 為目標。|
|[CA5389：不要將封存專案的路徑新增至目的檔案系統路徑](../code-quality/ca5389.md)|檔案路徑可以是相對的，而且可能會導致檔案系統存取預期的檔案系統目標路徑，使惡意的設定變更和遠端程式碼執行都透過「程式設計」和「等候」技術。|
|[CA5397：不要使用已被取代的 SslProtocols 值](../code-quality/ca5397.md)|ransport 層安全性（TLS）可保護電腦之間的通訊，最常見的方式是使用超文字安全傳輸通訊協定（HTTPS）。 舊版的 TLS 通訊協定版本比 TLS 1.2 和 TLS 1.3 低，而且更有可能會有新的弱點。 避免較舊的通訊協定版本，將風險降至最低。|
|[CA5398：避免硬式編碼 SslProtocols 值](../code-quality/ca5398.md)|傳輸層安全性（TLS）可保護電腦之間的通訊，最常見的方式是使用超文字安全傳輸通訊協定（HTTPS）。 Tls 1.0 和 TLS 1.1 的通訊協定版本已被取代，而 TLS 1.2 和 TLS 1.3 是最新的。 未來，TLS 1.2 和 TLS 1.3 可能會被取代。 若要確保您的應用程式保持安全，請避免硬式編碼通訊協定版本。|
