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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 52ddee2e876576508573fbadedcc407f81703e18
ms.sourcegitcommit: 9f6f63a2d76c6e579b4b67a96ec86faba99ad1df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71933122"
---
# <a name="security-warnings"></a>安全性警告

支援更安全之程式庫和應用程式的安全性警告。 這些警告有助於防止在程式中出現安全性問題。 如果停用這些警告中的任一個，則您應該清楚地在程式碼中標示理由，同時也要通知指定的安全主管有關您的開發專案。

## <a name="in-this-section"></a>本節內容

|規則|描述|
|----------|-----------------|
|[CA2100 必須審查 SQL 查詢是否有安全性弱點](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|方法會使用透過字串引數所建置的字串，將 System.Data.IDbCommand.CommandText 屬性設定為方法。 這項規則假設字串引數包含使用者輸入。 從使用者輸入所建置的 SQL 命令字串很容易遭到 SQL 插入攻擊。|
|[CA2102:在一般處理常式中攔截非 CLSCompliant 例外狀況](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|組件中不是以 RuntimeCompatibilityAttribute 標記或是以 RuntimeCompatibility(WrapNonExceptionThrows = false) 標記的成員包含處理 System.Exception 的 catch 區塊，同時不包含緊接其後的一般 catch 區塊。|
|[CA2103審查命令式安全性](../code-quality/ca2103-review-imperative-security.md)|方法會使用命令式安全性，而且可能會利用因要求正在使用中而可能變更的狀態資訊或傳回值建構使用權限。 請盡可能使用宣告式安全性。|
|[CA2104不要宣告唯讀的可變動參考型別](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|外部可見類型包含了可變動參考類型的外部可見唯讀欄位。 可變動類型是可以修改執行個體資料的類型。|
|[CA2105陣列欄位不應為唯讀](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|當您將唯讀 (在 Visual Basic 中為 ReadOnly) 修飾詞套用至包含陣列的欄位時，欄位就不能變更為參考不同的陣列。 但是，儲存在唯讀欄位的陣列元素則可以變更。|
|[CA2106 必須安全判斷提示](../code-quality/ca2106-secure-asserts.md)|方法會判斷提示使用權限，而且不會在呼叫端上執行安全性檢查。 判斷提示安全性權限但未執行任何安全性檢查，會在您的程式碼中留下可能遭利用的安全性弱點。|
|[CA2107 必須審查拒絕並僅允許使用](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|使用 PermitOnly 方法和 Codeaccesspermission.deny 時，只能由具有 .NET 安全性之 advanced 知識的安全性動作使用。 而使用這些安全性動作的程式碼應該接受安全性檢閱。|
|[CA2108:查看實數值型別的宣告式安全性](../code-quality/ca2108-review-declarative-security-on-value-types.md)|公用或受保護的實值類型受到資料存取或連結要求保護。|
|[CA2109 必須查看可見的事件處理常式](../code-quality/ca2109-review-visible-event-handlers.md)|偵測到公用或保護的事件處理方法。 除非有絕對的必要性，否則不應該公開 (Expose) 事件處理方法。|
|[CA2111指標不應該為可見的](../code-quality/ca2111-pointers-should-not-be-visible.md)|指標不為私用、內部或唯讀。 惡意的程式碼可變更指標值，進而可能會允許存取記憶體中的任意位置，或是造成應用程式或系統失敗。|
|[CA2112受保護的類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|公用或受保護的類型包含公用欄位，而且受到連結要求保護。 如果程式碼可存取受連結要求保護的類型執行個體，則程式碼不必滿足連結要求即可存取類型的欄位。|
|[CA2114方法安全性應該是類型的超集合](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|方法不應該同時具有相同動作的方法層級和類型層級宣告式安全性。|
|[CA2115呼叫 GC。使用原生資源時的 KeepAlive](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|此規則所偵測的錯誤，可能是因為在 Unmanaged 程式碼仍在使用 Unmanaged 資源時，就完成 Unmanaged 資源所致。|
|[CA2116APTCA 方法應該只呼叫 APTCA 方法](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|當完全信任的組件中出現 APTCA (AllowPartiallyTrustedCallers) 屬性，並且組件在不允許部分信任呼叫端的另一個組件中執行程式碼時，可能會發生安全性弱點攻擊。|
|[CA2117APTCA 類型應該只擴充 APTCA 基底類型](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|當完全信任的組件中出現 APTCA (AllowPartiallyTrustedCallers) 屬性，並且組件中的類型會繼承自不允許部分信任之呼叫端的類型時，就可能會發生安全性弱點攻擊。|
|[CA2118:審查 SuppressUnmanagedCodeSecurityAttribute 使用方式](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|對於執行使用 COM Interop 或平台引動過程之 Unmanaged 程式碼的成員，SuppressUnmanagedCodeSecurityAttribute 會變更安全性系統的預設行為。 這個屬性主要是用於增加效能，不過，效能提升會伴隨顯著的安全性風險。|
|[CA2119密封滿足私用介面的方法](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|可繼承的公用類型會提供內部 (在 Visual Basic 中為 Friend) 介面的可覆寫方法實作。 若要修正此規則的違規情形，請避免在組件外覆寫方法。|
|[CA2120 必須安全序列化的函式](../code-quality/ca2120-secure-serialization-constructors.md)|這個類型有接受 System.Runtime.Serialization.SerializationInfo 物件和 System.Runtime.Serialization.StreamingContext 物件 (序列化建構函式的簽章) 的建構函式。 這個建構函式未受到安全性檢查的保護，但類型中有一個或多個規則建構函式是受到保護的。|
|[CA2121靜態建構函式應該為私用的](../code-quality/ca2121-static-constructors-should-be-private.md)|系統會在建立類型的第一個執行個體或參考任何靜態成員之前呼叫靜態建構函式。 如果靜態建構函式不是私用的，則可由系統以外的程式碼呼叫。 視建構函式中執行的作業而定，這會造成非預期的行為。|
|[CA2122不要間接公開具有連結要求的方法](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|公用或受保護的成員具有連結要求，而且是由未執行任何安全性檢查的成員所呼叫。 連結要求只會檢查立即呼叫端的使用權限。|
|[CA2123覆寫連結要求應該與基底相同](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|這項規則會使方法符合它的基底方法，即另一個類型中的介面或虛擬方法，然後比較每個方法上的連結要求。 如果違反這項規則，則惡意呼叫端只需呼叫不安全的方法，就可以略過連結要求。|
|[CA2124:在外部嘗試包裝易受攻擊的 finally 子句](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|公用或受保護的方法包含 try/finally 區塊。 finally 區塊似乎會重設安全性狀態，而且不會封入 finally 區塊中。|
|[CA2126:類型連結要求需要繼承要求](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|公用 unsealed 類型受到連結要求保護，並且具有可以覆寫的方法。 此類型或方法都不是以繼承要求保護的。|
|[CA2130安全性關鍵常數應該是透明的](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|因為編譯器內嵌常數的值，所以沒有針對常數值強制透明度，因此在執行階段不需要查詢。 常數欄位應該具備安全性透明，程式碼檢閱者才不會假設透明程式碼無法存取常數。|
|[CA2131安全性關鍵類型可能未參與類型等價](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|類型會參與類型等價，而類型本身或類型的成員或欄位會以 SecurityCriticalAttribute 屬性標記。 此規則會引發任何關鍵的類型或包含參與類型等價之關鍵方法或欄位的類型。 當 CLR 偵測到這種類型時，它便無法載入此類型，而且會在執行階段發生 TypeLoadException。 通常，只有在使用者手動實作類型等價，而不是依賴 tlbimp 和編譯器進行類型等價時，就會引發這項規則。|
|[CA2132預設的函式至少必須與基底類型的預設函式一樣重要](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Silverlight 應用程式的程式碼不能使用內含 SecurityCriticalAttribute 的類型和成員。 重視安全性的類型以及成員，只能夠由 .NET Framework for Silverlight 類別庫中的受信任程式碼使用。 由於衍生類別中的公用或受保護建構所具有的透明度必須大於或等於其基底類別，因此應用程式中的類別不可衍生自標記為 SecurityCritical 的類別。|
|[CA2133委派必須系結至具有一致透明度的方法](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|當方法會將使用 SecurityCriticalAttribute 標記的委派繫結到透明方法，或繫結到使用 SecuritySafeCriticalAttribute 標記的方法時，就會針對此方法引發警告。 此警告也會引發將透明或安全關鍵性的委派繫結至關鍵方法的方法。|
|[CA2134覆寫基底方法時，方法必須保持一致的透明度](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|當使用 SecurityCriticalAttribute 標記的方法覆寫透明方法，或覆寫使用 SecuritySafeCriticalAttribute 標記的方法時，就會引發此規則。 當透明或使用 SecuritySafeCriticalAttribute 標記的方法覆寫使用 SecurityCriticalAttribute 標記的方法時，也會引發此規則。 覆寫虛擬方法或實作介面時會套用此規則。|
|[CA2135層級2元件不應該包含 Linkdemand](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|LinkDemand 在層級 2 安全性規則集中已被取代。 不使用 LinkDemand 在 Just-In-Time (JIT) 編譯時期強制執行安全性，改為使用 SecurityCriticalAttribute 屬性來標記方法、類型和欄位。|
|[CA2136成員不應該具有衝突的透明度注釋](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|透明度屬性會從較大範圍的程式碼項目套用至較小範圍的項目。 範圍較大之程式碼項目的透明度屬性優先於第一個項目中所包含之程式碼項目的透明度屬性。 例如，使用 SecurityCriticalAttribute 屬性來標記的類別不得包含使用 SecuritySafeCriticalAttribute 屬性來標記的方法。|
|[CA2137透明方法必須只包含可驗證的 IL](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|方法包含無法驗證的程式碼，或以傳址方式傳回類型。 當安全性透明程式碼嘗試執行無法驗證的 MSIL (Microsoft Intermediate Language) 時，就會引發此規則。 不過，此規則不包含完整的 IL 驗證器，並是使用啟發式來擷取多數的 MSIL 驗證違規情形。|
|[CA2138透明方法不能使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|安全性透明方法會呼叫使用 SuppressUnmanagedCodeSecurityAttribute 屬性標記的方法。|
|[CA2139透明方法不能使用 HandleProcessCorruptingExceptions 屬性](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|此規則會在任何透明的方法上引發，並嘗試使用 HandleProcessCorruptedStateExceptionsAttribute 屬性來處理進程損毀例外狀況。 進程損毀例外狀況是 CLR 版本4.0 例外狀況分類（例如 <xref:System.AccessViolationException>）。 HandleProcessCorruptedStateExceptionsAttribute 屬性只能供安全性關鍵方法使用，若套用至透明方法則會被忽略。|
|[CA2140透明程式碼不能參考安全性關鍵專案](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|以 SecurityTransparentAttribute 標記的方法可呼叫標記為 SecurityCritical 的非公用成員。 此規則會分析混合透明和重要之元件中的所有方法和類型，並將任何透明程式碼的呼叫標記為未標記為 SecurityTreatAsSafe 的非公用關鍵程式碼。|
|[CA2141：透明方法不可以滿足 LinkDemand](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|安全性透明方法會呼叫未使用 AllowPartiallyTrustedCallersAttribute (APTCA) 屬性標記之組件中的方法，或是安全性透明方法會滿足類型或方法的 LinkDemand。|
|[CA2142透明程式碼不應使用 Linkdemand 來保護](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|需要 LinkDemand 才能存取的透明方法會引發這個規則。 安全性透明程式碼不應負責驗證作業的安全性，因此不應要求權限。|
|[CA2143透明方法不應使用安全性需求](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|安全性透明程式碼不應負責驗證作業的安全性，因此不應要求權限。 安全性透明程式碼應使用完整的要求做出安全性決策，而且安全關鍵程式碼不應依賴透明程式碼提出完全要求。|
|[CA2144透明程式碼不應該從位元組陣列載入元件](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|透明程式碼的安全性檢閱不如關鍵性程式碼的安全性檢閱徹底，因為透明程式碼無法執行安全性敏感動作。 透明程式碼中可能不會注意到從位元組陣列載入的組件，而該位元組陣列可能包含需要稽核之重大或更重要的安全關鍵性程式碼。|
|[CA2145透明方法不應使用 SuppressUnmanagedCodeSecurityAttribute 裝飾](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|以 SuppressUnmanagedCodeSecurityAttribute 屬性裝飾的方法會在任何方法呼叫它時放置隱含的 LinkDemand。 這個 LinkDemand 會要求呼叫程式碼具備安全性關鍵。 使用 SecurityCriticalAttribute 屬性來標記使用 SuppressUnmanagedCodeSecurity 的方法會使方法呼叫端的這個需求更為明顯。|
|[CA2146類型至少必須與基底類型和介面一樣重要](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|當衍生類型有安全性透明屬性，且該屬性的重要性不如基底類型或已實作之介面時，就會引發這個規則。 只有關鍵類型可以衍生自關鍵基底類型或實作關鍵介面，而且只有關鍵或安全關鍵類型可以衍生自安全關鍵基底類型或實作安全關鍵介面。|
|[CA2147透明方法不能使用安全性判斷提示](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|此規則會分析完全透明或混合透明/關鍵之組件中的所有方法和類型，並將 Assert 的任何宣告式或必要用法加上旗標。|
|[CA2149透明方法不能呼叫原生程式碼](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|此規則會在直接呼叫機器碼（例如透過 P/Invoke）的任何透明方法上引發。 違反此規則會導致層級 2 透明度模型出現 MethodAccessException，而在層級 1 透明度模型會出現對 UnmanagedCode 的完整要求。|
|[CA2151具有關鍵類型的欄位應為安全性關鍵](../code-quality/ca2151-fields-with-critical-types-should-be-security-critical.md)|若要使用安全性關鍵類型，參考該類型的程式碼必須是安全性關鍵或安全性安全關鍵。 即使是間接參考也是如此。 因此，使用安全性透明或安全性安全關鍵欄位容易發生錯誤，因為透明程式碼仍然無法存取該欄位。|
|[CA5122 P-Invoke 宣告不應為安全關鍵](../code-quality/ca5122-p-invoke-declarations-should-not-be-safe-critical.md)|在執行安全性敏感作業時，會將方法標記為 SecuritySafeCritical，但透明程式碼也能安全地使用。 透明程式碼不可直接透過 P/Invoke 呼叫機器碼。 因此，即使將 P/Invoke 標示為安全性安全關鍵，透明程式碼仍然不能呼叫它，而且會導致安全性分析錯誤。|
|[CA2153：避免處理損毀狀態例外狀況 @ no__t-0|[損毀狀態例外狀況 (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) 指出您的處理序中有記憶體損毀的狀況。 如果攻擊者將攻擊放入損毀的記憶體區域，則攔截這些處理序而非讓它們損毀，會導致安全性弱點。|
|[CA3075：不安全的 DTD 處理 @ no__t-0|如果您使用不安全的 DTDProcessing 執行個體或參考外部實體來源，剖析器可能會接受未受信任的輸入，而將機密資訊洩漏給攻擊者。|
|[CA3076：不安全的 XSLT 腳本執行 @ no__t-0|如果您在 .NET 應用程式中以不安全的方式執行可延伸樣式表語言轉換 (XSLT)，處理器可能會解析不受信任的 URI 參考，而這些參考可能會將機密資訊洩漏給攻擊者，導致拒絕服務和跨網站攻擊。|
|[CA3077：API 設計、XML 檔和 XML 文字讀取器 @ no__t 中的不安全處理-0|針對衍生自 XMLDocument 和 XMLTextReader 的 API 進行設計時，請留意 DtdProcessing。 若在參考或解析外部實體來源時使用不安全的 DTDProcessing 執行個體，或在 XML 中設定不安全的值，都可能會導致資訊洩漏。|
|[CA3147：以 ValidateAntiForgeryToken @ no__t-0 標記動詞處理常式|在設計 ASP.NET MVC 控制器時，請注意跨網站偽造要求攻擊。 跨網站要求偽造攻擊可能會將來自已驗證使用者的惡意要求傳送至您的 ASP.NET MVC 控制器。|
|[CA5361：請勿停用安全密碼編譯 @ no__t-0 的 SChannel 使用|設定`Switch.System.Net.DontEnableSchUseStrongCrypto` 以`true`削弱傳出傳輸層安全性（TLS）連線中使用的密碼編譯。 較弱的密碼編譯可能會危害您的應用程式與伺服器之間的通訊機密性，讓攻擊者更容易竊聽敏感性資料。|
|[CA5363：不要停用要求驗證 @ no__t-0|要求驗證是 ASP.NET 中的一項功能，可檢查 HTTP 要求，並判斷它們是否包含可能會導致插入式攻擊的潛在危險內容，包括跨網站腳本。|
|[CA5364:請勿使用已淘汰的安全性通訊協定](../code-quality/ca5364.md)|傳輸層安全性（TLS）可保護電腦之間的通訊，最常見的方式是使用超文字安全傳輸通訊協定（HTTPS）。 舊版的 TLS 通訊協定版本比 TLS 1.2 和 TLS 1.3 低，而且更有可能會有新的弱點。 避免較舊的通訊協定版本，將風險降至最低。|
|[CA5369：使用 XmlReader 來還原序列化 @ no__t-0|處理不受信任的 DTD 和 XML 架構可能會啟用載入危險的外部參考，這應該使用具有安全解析程式的 XmlReader，或停用 DTD 和 XML 內嵌架構處理來加以限制。|
|[CA5370：使用 XmlReader 來驗證讀取器 @ no__t-0|處理不受信任的 DTD 和 XML 架構可能會啟用載入危險的外部參考。 這項危險的載入可以藉由使用具有安全解析程式的 XmlReader，或在停用 DTD 和 XML 內嵌架構處理的情況下受到限制。|
|[CA5371：使用 XmlReader 進行架構讀取 @ no__t-0|處理不受信任的 DTD 和 XML 架構可能會啟用載入危險的外部參考。 使用具有安全解析程式的 XmlReader，或已停用 DTD 和 XML 內嵌架構處理時，會限制這種情況。|
|[CA5372：針對 XPathDocument @ no__t 使用 XmlReader-0|從不受信任的資料處理 XML 可能會載入危險的外部參考，這可以透過使用具有安全解析程式的 XmlReader 或停用 DTD 處理來加以限制。|
|[CA5373：不要使用過時的金鑰衍生函式 @ no__t-0|此規則會偵測弱式金鑰衍生方法<xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName>和`Rfc2898DeriveBytes.CryptDeriveKey`的調用。 <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName>使用弱式演算法 PBKDF1。|
|[CA5378：不要停用 ServicePointManagerSecurityProtocols @ no__t-0|設定`Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` 以`true`限制使用 TLS 1.0 的 Windows Communication Framework （WCF）傳輸層安全性（tls）連線。 該 TLS 版本將會被取代。|
|[CA5380：不要將憑證新增至根存放區 @ no__t-0|此規則會偵測將憑證新增至「信任的根憑證授權單位」憑證存放區的程式碼。 根據預設，「信任的根憑證授權單位」憑證存放區是以一組已符合「Microsoft 根憑證計畫」需求的公用 Ca 來設定。|
|[CA5381：確保憑證不會新增至根存放區 @ no__t-0|此規則會偵測可能將憑證新增至「信任的根憑證授權單位」憑證存放區的程式碼。 根據預設，信任的根憑證授權單位憑證存放區是以一組已符合 Microsoft 根憑證計畫需求的公開憑證授權單位單位（Ca）來設定。|
|[CA5386:避免硬式編碼 Securityprotocoltype.tls11 值](../code-quality/ca5386.md)|傳輸層安全性（TLS）可保護電腦之間的通訊，最常見的方式是使用超文字安全傳輸通訊協定（HTTPS）。 Tls 1.0 和 TLS 1.1 的通訊協定版本已被取代，而 TLS 1.2 和 TLS 1.3 是最新的。 未來，TLS 1.2 和 TLS 1.3 可能會被取代。 若要確保您的應用程式保持安全，請避免硬式編碼通訊協定版本，並以至少 .NET Framework v 4.7.1 為目標。|
|[CA5389：不要將封存專案的路徑新增至目的檔案系統路徑 @ no__t-0|檔案路徑可以是相對的，而且可能會導致檔案系統存取預期的檔案系統目標路徑，使惡意的設定變更和遠端程式碼執行都透過「程式設計」和「等候」技術。|
|[CA5397:請勿使用已被取代的 SslProtocols 值](../code-quality/ca5397.md)|ransport 層安全性（TLS）可保護電腦之間的通訊，最常見的方式是使用超文字安全傳輸通訊協定（HTTPS）。 舊版的 TLS 通訊協定版本比 TLS 1.2 和 TLS 1.3 低，而且更有可能會有新的弱點。 避免較舊的通訊協定版本，將風險降至最低。|
|[CA5398:避免硬式編碼 SslProtocols 值](../code-quality/ca5398.md)|傳輸層安全性（TLS）可保護電腦之間的通訊，最常見的方式是使用超文字安全傳輸通訊協定（HTTPS）。 Tls 1.0 和 TLS 1.1 的通訊協定版本已被取代，而 TLS 1.2 和 TLS 1.3 是最新的。 未來，TLS 1.2 和 TLS 1.3 可能會被取代。 若要確保您的應用程式保持安全，請避免硬式編碼通訊協定版本。|
