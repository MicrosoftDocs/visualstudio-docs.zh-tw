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
ms.openlocfilehash: a40273c3230854e4b1d1a11a3fd02de54d5df745
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2020
ms.locfileid: "89599969"
---
# <a name="security-warnings"></a>安全性警告

支援更安全之程式庫和應用程式的安全性警告。 這些警告有助於防止在程式中出現安全性問題。 如果停用這些警告中的任一個，則您應該清楚地在程式碼中標示理由，同時也要通知指定的安全主管有關您的開發專案。

## <a name="in-this-section"></a>本節內容

|規則|說明|
|----------|-----------------|
|[CA2100:必須檢閱 SQL 查詢中是否有安全性弱點](../code-quality/ca2100.md)|方法會使用透過字串引數所建置的字串，將 System.Data.IDbCommand.CommandText 屬性設定為方法。 這項規則假設字串引數包含使用者輸入。 從使用者輸入所建置的 SQL 命令字串很容易遭到 SQL 插入攻擊。|
|[CA2109:必須檢閱可見的事件處理常式](../code-quality/ca2109.md)|偵測到公用或保護的事件處理方法。 除非有絕對的必要性，否則不應該公開事件處理方法。|
|[CA2119:密封方法以滿足私用介面的要求](../code-quality/ca2119.md)|可繼承的公用類型會提供內部 (在 Visual Basic 中為 Friend) 介面的可覆寫方法實作。 若要修正此規則的違規情形，請避免在組件外覆寫方法。|
|[CA2153:避免處理損毀狀態例外狀況](../code-quality/ca2153.md)|[損毀狀態例外狀況 (CSE)](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions) 指出您的處理序中有記憶體損毀的狀況。 如果攻擊者將攻擊放入損毀的記憶體區域，則攔截這些處理序而非讓它們損毀，會導致安全性弱點。|
|[CA2300：請勿使用不安全的還原序列化程式 BinaryFormatter](../code-quality/ca2300.md)|在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。|
|[CA2301：未先設定 BinaryFormatter.Binder 之前，請勿呼叫 BinaryFormatter.Deserialize](../code-quality/ca2301.md)|在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。|
|[CA2302：呼叫 BinaryFormatter.Deserialize 之前，請務必先設定 BinaryFormatter.Binder](../code-quality/ca2302.md)|在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。|
|[CA2305：請勿使用不安全的還原序列化程式 LosFormatter](../code-quality/ca2305.md)|在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。|
|[CA2310：請勿使用不安全的還原序列化程式 NetDataContractSerializer](../code-quality/ca2310.md)|在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。|
|[CA2311：未先設定 NetDataContractSerializer.Binder 之前，請勿還原序列化](../code-quality/ca2311.md)|在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。|
|[CA2312：還原序列化之前，請務必先設定 NetDataContractSerializer.Binder](../code-quality/ca2312.md)|在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。|
|[CA2315：請勿使用不安全的還原序列化程式 ObjectStateFormatter](../code-quality/ca2315.md)|在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。|
|[CA2321：請勿使用 SimpleTypeResolver 搭配 JavaScriptSerializer 來還原序列化](../code-quality/ca2321.md)|在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。|
|[CA2322：還原序列化之前，請確定不會使用 SimpleTypeResolver 來將 JavaScriptSerializer 初始化](../code-quality/ca2322.md)|在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。|
|[CA2326:請勿使用「無」以外的 TypeNameHandling 值](../code-quality/ca2326.md)|在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。|
|[CA2327:請勿使用不安全的 JsonSerializerSettings](../code-quality/ca2327.md)|在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。|
|[CA2328:確定 JsonSerializerSettings 安全](../code-quality/ca2328.md)|在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。|
|[CA2329:請勿使用不安全的組態來還原序列化 JsonSerializer](../code-quality/ca2329.md)|在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。|
|[CA2330:在還原序列化時，請確認 JsonSerializer 有安全的組態](../code-quality/ca2330.md)|在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。|
|[CA2350：請確認 DataTable.ReadXml() 的輸入是受信任的](ca2350.md)|<xref:System.Data.DataTable>使用不受信任的輸入還原序列化時，攻擊者可以製作惡意輸入來執行阻斷服務攻擊。 可能有未知的遠端程式碼執行弱點。|
|[CA2351：請確認 DataSet.ReadXml() 的輸入是受信任的](ca2351.md)|<xref:System.Data.DataSet>使用不受信任的輸入還原序列化時，攻擊者可以製作惡意輸入來執行阻斷服務攻擊。 可能有未知的遠端程式碼執行弱點。|
|[CA2352：可序列化類型中的不安全 DataSet 或 DataTable 可能容易受到遠端程式碼執行攻擊](ca2352.md)|標記為的類別或結構 <xref:System.SerializableAttribute> 包含 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 欄位或屬性，而且沒有 <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> 。|
|[CA2353：可序列化類型中的不安全 DataSet 或 DataTable](ca2353.md)|以 XML 序列化屬性（attribute）或資料合約屬性（attribute）標記的類別或結構包含 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 欄位或屬性（property）。|
|[CA2354：還原序列化物件圖中的不安全 DataSet 或 DataTable 可能容易受到遠端程式碼執行攻擊](ca2354.md)|使用序列化還原序列化 <xref:System.Runtime.Serialization.IFormatter?displayProperty=nameWithType> ，而轉換類型的物件圖形可以包含 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 。|
|[CA2355：還原序列化物件圖中的不安全 DataSet 或 DataTable](ca2355.md)|在轉換或指定類型的物件圖形可以包含或時還原 <xref:System.Data.DataSet> 序列化 <xref:System.Data.DataTable> 。|
|[CA2356： web 還原序列化物件圖形中不安全的資料集或 DataTable](ca2356.md)|具有或的方法 <xref:System.Web.Services.WebMethodAttribute?displayProperty=nameWithType> <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> 具有可參考或的參數 <xref:System.Data.DataSet> <xref:System.Data.DataTable> 。|
|[CA2361：確認不會搭配不受信任的資料使用包含 DataSet.ReadXml() 的自動產生類別](ca2361.md)|<xref:System.Data.DataSet>使用不受信任的輸入還原序列化時，攻擊者可以製作惡意輸入來執行阻斷服務攻擊。 可能有未知的遠端程式碼執行弱點。|
|[CA2362：自動產生之可序列化型別中不安全的 DataSet 或 DataTable，容易受到遠端程式碼執行攻擊](ca2362.md)|當還原序列化未受信任的輸入，而且還原序列化 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 的物件圖形包含 <xref:System.Data.DataSet> 或時 <xref:System.Data.DataTable> ，攻擊者可以製作惡意的內容來執行遠端程式碼執行攻擊。|
|[CA3001：檢閱程式碼是否有 SQL 插入式攻擊弱點](../code-quality/ca3001.md)|使用不受信任的輸入和 SQL 命令時，請注意 SQL 插入式攻擊。 SQL 插入式攻擊可能會執行惡意的 SQL 命令，而危及應用程式的安全性和完整性。|
|[CA3002：檢閱程式碼是否有 XSS 弱點](../code-quality/ca3002.md)|從 web 要求處理不受信任的輸入時，請注意跨網站腳本 (XSS) 攻擊。 XSS 攻擊會將不受信任的輸入插入原始 HTML 輸出，讓攻擊者可以執行惡意腳本或惡意地修改您網頁中的內容。|
|[CA3003：檢閱程式碼是否有檔案路徑插入式攻擊弱點](../code-quality/ca3003.md)|使用來自 web 要求的未受信任輸入時，請留意在指定檔案路徑時使用使用者控制的輸入。|
|[CA3004：檢閱程式碼是否有資訊洩漏弱點](../code-quality/ca3004.md)|洩漏例外狀況資訊可讓攻擊者深入瞭解您的應用程式內部，這可協助攻擊者找出其他弱點來進行攻擊。|
|[CA3006：檢閱程式碼是否有處理序命令插入式攻擊弱點](../code-quality/ca3006.md)|使用不受信任的輸入時，請注意命令插入式攻擊。 命令插入式攻擊可在基礎作業系統上執行惡意命令，而危及伺服器的安全性和完整性。|
|[CA3007：檢閱程式碼是否有開放式重新導向弱點](../code-quality/ca3007.md)|使用不受信任的輸入時，請留意開放式重新導向弱點。 攻擊者可以利用開放式重新導向弱點，使用您的網站提供合法 URL 的外觀，但將不受信任的訪客重新導向至網路釣魚或其他惡意網頁。|
|[CA3008：檢閱程式碼是否有 XPath 插入式攻擊弱點](../code-quality/ca3008.md)|使用不受信任的輸入時，請注意 XPath 插入式攻擊。 使用不受信任的輸入來建立 XPath 查詢，可能會讓攻擊者惡意地操作查詢以傳回非預期的結果，而且可能會洩漏所查詢 XML 的內容。|
|[CA3009：檢閱程式碼是否有 XML 插入式攻擊弱點](../code-quality/ca3009.md)|使用不受信任的輸入時，請注意 XML 插入式攻擊。|
|[CA3010：檢閱程式碼是否有 XAML 插入式攻擊弱點](../code-quality/ca3010.md)|使用不受信任的輸入時，請注意 XAML 插入式攻擊。 XAML 是直接表示物件執行個體化和執行的標記語言。 這表示在 XAML 中建立的元素可以與系統資源互動 (例如，網路存取和檔案系統 IO) 。|
|[CA3011：檢閱程式碼是否有 DLL 插入式攻擊弱點](../code-quality/ca3011.md)|使用不受信任的輸入時，請注意載入未受信任的程式碼。 如果您的 web 應用程式載入未受信任的程式碼，攻擊者可能會將惡意 Dll 插入您的進程，並執行惡意程式碼。|
|[CA3012：檢閱程式碼是否有 regex 插入式攻擊弱點](../code-quality/ca3012.md)|使用不受信任的輸入時，請注意 RegEx 插入式攻擊。 攻擊者可以使用 RegEx 插入來惡意地修改正則運算式、讓 RegEx 符合非預期的結果，或讓 RegEx 耗用過多的 CPU，造成阻絕服務攻擊。|
|[CA3061：請勿透過 URL 新增結構描述](../code-quality/ca3061.md)|請勿使用 Add 方法的 unsafe 多載，因為它可能會造成危險的外部參考。|
|[CA3075:不安全的 DTD 處理](../code-quality/ca3075.md)|如果您使用不安全的 DTDProcessing 執行個體或參考外部實體來源，剖析器可能會接受未受信任的輸入，而將機密資訊洩漏給攻擊者。|
|[CA3076:不安全的 XSLT 指令碼執行](../code-quality/ca3076.md)|如果您在 .NET 應用程式, 中執行 (XSLT) 的可延伸樣式表語言轉換，處理器可能會解析可能洩漏機密資訊給攻擊者的不受信任 URI 參考，進而導致阻絕服務和跨網站攻擊。|
|[CA3077:API 設計、XML 文件和 XML 文字讀取器中的不安全處理](../code-quality/ca3077.md)|針對衍生自 XMLDocument 和 XMLTextReader 的 API 進行設計時，請留意 DtdProcessing。 若在參考或解析外部實體來源時使用不安全的 DTDProcessing 執行個體，或在 XML 中設定不安全的值，都可能會導致資訊洩漏。|
|[CA3147:使用 ValidateAntiForgeryToken 標示動詞處理常式](../code-quality/ca3147.md)|設計 ASP.NET MVC 控制器時，請留意跨網站偽造要求的攻擊。 跨網站偽造要求攻擊可以將來自已驗證使用者的惡意要求傳送到您的 ASP.NET MVC 控制器。|
|[CA5350：請勿使用弱式密碼編譯演算法](../code-quality/ca5350.md)|現今，弱式加密演算法和雜湊函式用於多種原因，但它們不應該用來保證所保護資料的機密性或完整性。 此規則會在它在程式碼中發現 TripleDES、SHA1 或 RIPEMD160 演算法時觸發。|
|[CA5351：不使用中斷的密碼編譯演算法](../code-quality/ca5351.md)|中斷的密碼編譯演算法較不安全，強烈建議您不要使用它們。 此規則會在它在程式碼中發現 MD5 雜湊演算法或 DES 或 RC2 加密演算法時觸發。|
|[CA5358:不要使用不安全的 Cipher 模式](../code-quality/ca5358.md)|不要使用不安全的 Cipher 模式|
|[CA5359：請勿停用憑證驗證](../code-quality/ca5359.md)|憑證可協助驗證服務器的身分識別。 用戶端應該驗證伺服器憑證，以確保會將要求傳送給預定的伺服器。 如果 ServerCertificateValidationCallback 一律 `true` 會傳回，任何憑證都會通過驗證。|
|[CA5360：請勿在還原序列化時呼叫危險的方法](../code-quality/ca5360.md)|不安全的還原序列化是在未受信任的資料用來濫用應用程式邏輯、對拒絕服務 (DoS) 攻擊，或甚至在還原序列化時執行任意程式碼時，就會發生的弱點。 當應用程式將受信任的資料還原序列化時，惡意使用者通常可能會濫用這些還原序列化功能。 具體而言，在還原序列化的過程中叫用危險的方法。 成功的不安全還原序列化攻擊可能會讓攻擊者執行攻擊，例如 DoS 攻擊、驗證略過，以及遠端程式碼執行。|
|[CA5361:請勿為安全通道停用強式密碼編譯](../code-quality/ca5361.md)|設定 `Switch.System.Net.DontEnableSchUseStrongCrypto` 以 `true` 削弱輸出傳輸層安全性中使用的密碼編譯 (TLS) 連接。 較弱的密碼編譯可能會危及應用程式與伺服器之間通訊的機密性，讓攻擊者更容易竊聽敏感性資料。|
|[CA5362：還原序列化物件圖中的可能參考循環](../code-quality/ca5362.md)|如果還原序列化不受信任的資料，則任何處理已還原序列化之物件圖形的程式碼都必須處理參考迴圈，而不會進入無限迴圈。 這包括屬於還原序列化回呼一部分的程式碼，以及完成還原序列化之後處理物件圖形的程式碼。 否則，攻擊者可能會使用包含參考週期的惡意資料來執行阻斷服務攻擊。|
|[CA5363：請勿停用要求驗證](../code-quality/ca5363.md)|要求驗證是 ASP.NET 中的一項功能，可檢查 HTTP 要求，並判斷它們是否包含可能會導致插入式攻擊的潛在危險內容，包括跨網站腳本。|
|[CA5364:請勿使用已取代的安全性通訊協定](../code-quality/ca5364.md)|傳輸層安全性 (TLS) 保護電腦之間的通訊安全，最常見的方式是使用超文字傳輸通訊協定安全 (HTTPS) 。 舊版的 TLS 通訊協定版本比 TLS 1.2 和 TLS 1.3 更不安全，而且可能會有新的弱點。 避免較舊的通訊協定版本，以將風險降至最低。|
|[CA5365：請勿停用 HTTP 標頭檢查](../code-quality/ca5365.md)|HTTP 標頭檢查可針對在回應標頭中找到的換行字元和分行符號（\r 和 \n）進行編碼。 這種編碼方式有助於避免利用應用程式回應標頭所含之不受信任資料的插入式攻擊。|
|[CA5366：請使用 XmlReader 為 DataSet 讀取 XML](../code-quality/ca5366.md)|使用 <xref:System.Data.DataSet> 來讀取具有不受信任資料的 XML 可能會載入危險的外部參考，而這些參考應透過使用 <xref:System.Xml.XmlReader> 安全解析程式或停用 DTD 處理來限制。|
|[CA5367：請勿將具有指標欄位的類型序列化](../code-quality/ca5367.md)|此規則會檢查是否有具有指標欄位或屬性的可序列化類別。 無法序列化的成員可以是指標，例如以標記的靜態成員或欄位 <xref:System.NonSerializedAttribute> 。|
|[CA5368：為衍生自頁面的類別設定 ViewStateUserKey](../code-quality/ca5368.md)|設定此 <xref:System.Web.UI.Page.ViewStateUserKey> 屬性可讓您將識別碼指派給個別使用者的 view state 變數，讓攻擊者無法使用變數來產生攻擊，藉此協助您防止應用程式的攻擊。 否則，將會有跨網站要求偽造的弱點。|
|[CA5369：請使用 XmlReader 進行還原序列化](../code-quality/ca5369.md)|處理不受信任的 DTD 和 XML 架構可能會啟用載入危險的外部參考，應使用具有安全解析程式的 XmlReader，或停用 DTD 和 XML 內嵌架構處理來限制。|
|[CA5370：請使用 XmlReader 驗證讀取器](../code-quality/ca5370.md)|處理不受信任的 DTD 和 XML 架構可能會啟用載入危險的外部參考。 您可以使用具有安全解析程式的 XmlReader，或是停用 DTD 和 XML 內嵌架構處理，來限制這個危險的載入。|
|[CA5371：請使用 XmlReader 讀取結構描述](../code-quality/ca5371.md)|處理不受信任的 DTD 和 XML 架構可能會啟用載入危險的外部參考。 使用具有安全解析程式的 XmlReader，或已停用 DTD 和 XML 內嵌架構處理的 XmlReader 會限制這一點。|
|[CA5372：請為 XPathDocument 使用 XmlReader](../code-quality/ca5372.md)|處理來自不受信任資料的 XML 可能會載入危險的外部參考，可以使用具有安全解析程式或停用 DTD 處理的 XmlReader 來限制。|
|[CA5373：不使用已過時的金鑰衍生函式](../code-quality/ca5373.md)|此規則會偵測弱式金鑰衍生方法和的調用 <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> `Rfc2898DeriveBytes.CryptDeriveKey` 。 <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> 使用弱式演算法 PBKDF1。|
|[CA5374：請勿使用 XslTransform](../code-quality/ca5374.md)|這 <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> 項規則會檢查程式碼中是否具現化。 <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> 現在已過時，不應該使用。|
|[CA5375：請勿使用帳戶共用存取簽章](../code-quality/ca5375.md)|帳戶 SAS 可將存取權委派給服務 SAS 不允許的 blob 容器、資料表、佇列和檔案共用的讀取、寫入和刪除作業。 不過，它不支援容器層級的原則，而且對授與的許可權不會有更大的彈性和控制權。 惡意使用者取得之後，您的儲存體帳戶將會很容易遭到入侵。|
|[CA5376：請使用 SharedAccessProtocol HttpsOnly](../code-quality/ca5376.md)|SAS 是無法在 HTTP 上以純文字傳輸的機密資料。|
|[CA5377：請使用容器層級存取原則](../code-quality/ca5377.md)|您可以隨時修改或撤銷容器層級的存取原則。 它對授與的許可權提供更大的彈性和控制權。|
|[CA5378:請勿停用 ServicePointManagerSecurityProtocols](../code-quality/ca5378.md)|將設定 `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` 為 `true` 限制 Windows Communication Framework 的 (WCF) 傳輸層安全性 (tls) 使用 tls 1.0 的連接。 該版本的 TLS 將會被取代。|
|[CA5379：請勿使用弱式金鑰衍生函數 (Key Derivation Function) 演算法](../code-quality/ca5379.md)|<xref:System.Security.Cryptography.Rfc2898DeriveBytes>類別預設會使用此 <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> 演算法。 您應該在具有 <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> 或更高版本的函式的某些多載中，指定要使用的雜湊演算法。 請注意， <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> 屬性只有一個 `get` 存取子，而且沒有 `overriden` 修飾詞。|
|[CA5380：不新增憑證至根存放區](../code-quality/ca5380.md)|此規則會偵測將憑證新增至「信任的根憑證授權單位」憑證存放區中的程式碼。 根據預設，「受信任的根憑證授權單位」憑證存放區會使用符合「Microsoft 根憑證計畫」需求的一組公用 Ca 進行設定。|
|[CA5381：確保憑證不新增至根存放區](../code-quality/ca5381.md)|此規則會偵測可能將憑證新增至「信任的根憑證授權單位」憑證存放區中的程式碼。 根據預設，「受信任的根憑證授權單位」憑證存放區會設定一組公開憑證授權單位單位， (CAs) 符合「Microsoft 根憑證計畫」的需求。|
|[CA5382：在 ASP.Net Core 中使用安全的 Cookie](../code-quality/ca5382.md)|透過 HTTPS 提供的應用程式必須使用安全 cookie，這會向瀏覽器指出 cookie 只應使用傳輸層安全性 (TLS) 來傳輸。|
|[CA5383：請確認在 ASP.Net Core 中使用安全的 Cookie](../code-quality/ca5383.md)|透過 HTTPS 提供的應用程式必須使用安全 cookie，這會向瀏覽器指出 cookie 只應使用傳輸層安全性 (TLS) 來傳輸。|
|[CA5384：請勿使用數位簽章演算法 (DSA)](../code-quality/ca5384.md)|DSA 是弱式非對稱式加密演算法。|
|[CA5385：使用有足夠金鑰大小的 Rivest–Shamir–Adleman (RSA) 加密演算法](../code-quality/ca5385.md)|小於2048位的 RSA 金鑰更容易遭受暴力密碼破解攻擊。|
|[CA5386:避免將 SecurityProtocolType 值寫入程式碼](../code-quality/ca5386.md)|傳輸層安全性 (TLS) 保護電腦之間的通訊安全，最常見的方式是使用超文字傳輸通訊協定安全 (HTTPS) 。 通訊協定版本 TLS 1.0 和 TLS 1.1 已被取代，而 TLS 1.2 和 TLS 1.3 是最新的。 未來，TLS 1.2 和 TLS 1.3 可能已被取代。 為了確保您的應用程式保持安全，請避免硬式編碼通訊協定版本，並以至少 .NET Framework v 4.7.1 為目標。|
|[CA5387：請勿使用反覆項目數不足的弱式金鑰衍生函數 (Key Derivation Function)](../code-quality/ca5387.md)|這項規則會檢查密碼編譯金鑰是否 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> 以小於100000的反復專案計數產生。 較高的反復專案計數有助於減輕嘗試猜測產生的密碼編譯金鑰的字典攻擊。|
|[CA5388：使用弱式金鑰衍生函數 (Key Derivation Function) 時，請確保反覆項目數足夠](../code-quality/ca5388.md)|這項規則會檢查是否有產生密碼編譯金鑰 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> ，且反覆運算計數可能小於100000。 較高的反復專案計數有助於減輕嘗試猜測產生的密碼編譯金鑰的字典攻擊。|
|[CA5389：不將封存項目路徑新增至目標檔案系統路徑](../code-quality/ca5389.md)|檔案路徑可以是相對路徑，而且可能會導致檔案系統在預期的檔案系統目標路徑以外存取，進而導致惡意的設定變更，以及透過配置和等候技術執行遠端程式碼。|
|[CA5390：請勿使用硬式編碼加密金鑰](../code-quality/ca5390.md)|若要讓對稱演算法成功，秘密金鑰必須只有傳送者和接收者才知道。 當金鑰硬式編碼時，很容易就能找到。 即使是已編譯的二進位檔，惡意使用者也很容易將其解壓縮。 一旦私密金鑰遭到入侵，就可以直接解密加密文字，而不會再受到保護。|
|[CA5391：請在 ASP.NET Core MVC 控制器中使用防偽權杖](../code-quality/ca5391.md)|處理 `POST` 、 `PUT` 、 `PATCH` 或 `DELETE` 要求而不驗證 antiforgery token，可能很容易受到跨網站偽造要求攻擊。 跨網站偽造要求攻擊可以將來自已驗證使用者的惡意要求傳送到您的 ASP.NET Core MVC 控制器。|
|[CA5392：請對 P/Invokes 使用 DefaultDllImportSearchPaths 屬性](../code-quality/ca5392.md)|根據預設，P/Invoke 函式使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 探查許多目錄，包括要載入之程式庫的目前工作目錄。 這可能是某些應用程式的安全性問題，因而導致 DLL 劫持。|
|[CA5393：請勿使用不安全的 DllImportSearchPath 值](../code-quality/ca5393.md)|預設 DLL 搜尋目錄和元件目錄中可能有惡意的 DLL。 或者，根據執行應用程式的位置而定，應用程式的目錄中可能會有惡意的 DLL。|
|[CA5394：請勿使用不安全的隨機性](../code-quality/ca5394.md)|使用密碼編譯弱式虛擬亂數產生器可能會讓攻擊者預測將產生的安全性敏感性值。|
|[CA5395：遺漏動作方法的 HttpVerb 屬性](../code-quality/ca5395.md)|建立、編輯、刪除或以其他方式修改資料的所有動作方法，都必須使用 antiforgery 屬性來保護，以防止跨網站偽造要求攻擊。 執行 GET 作業應該是安全的作業，不會有副作用，也不會修改您的保存資料。|
|[CA5396：將 HttpCookie 的 HttpOnly 設為 true](../code-quality/ca5396.md)|作為深度防禦措施，請確定安全性敏感的 HTTP cookie 已標示為 HttpOnly。 這表示網頁瀏覽器不允許腳本存取 cookie。 插入的惡意腳本是竊取 cookie 的常見方式。|
|[CA5397：請勿使用已過時的 SslProtocols 通訊協定](../code-quality/ca5397.md)|傳輸層安全性 (TLS) 保護電腦之間的通訊安全，最常見的方式是使用超文字傳輸通訊協定安全 (HTTPS) 。 舊版的 TLS 通訊協定版本比 TLS 1.2 和 TLS 1.3 更不安全，而且可能會有新的弱點。 避免較舊的通訊協定版本，以將風險降至最低。|
|[CA5398：避免以硬式編碼方式寫入 SslProtocols 值](../code-quality/ca5398.md)|傳輸層安全性 (TLS) 保護電腦之間的通訊安全，最常見的方式是使用超文字傳輸通訊協定安全 (HTTPS) 。 通訊協定版本 TLS 1.0 和 TLS 1.1 已被取代，而 TLS 1.2 和 TLS 1.3 是最新的。 未來，TLS 1.2 和 TLS 1.3 可能已被取代。 為了確保您的應用程式保持安全，請避免硬式編碼通訊協定版本。|
|[CA5399：確認停用 HttpClient 憑證撤銷清單檢查](../code-quality/ca5399.md)|撤銷的憑證不再受到信任。 攻擊者可以使用它來傳遞某些惡意資料，或竊取 HTTPS 通訊中的敏感性資料。|
|[CA5400：確認未停用 HttpClient 憑證撤銷清單檢查](../code-quality/ca5400.md)|撤銷的憑證不再受到信任。 攻擊者可以使用它來傳遞某些惡意資料，或竊取 HTTPS 通訊中的敏感性資料。|
|[CA5401：請勿使用具有非預設 IV 的 CreateEncryptor](../code-quality/ca5401.md)|對稱式加密應該一律使用不可重複的初始化向量來防止字典攻擊。|
|[CA5402：使用具有預設 IV 的 CreateEncryptor](../code-quality/ca5402.md)|對稱式加密應該一律使用不可重複的初始化向量來防止字典攻擊。|
|[CA5403:不要硬式編碼憑證](../code-quality/ca5403.md)|`data`或函式的或 `rawData` 參數 <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 是硬式編碼。|
