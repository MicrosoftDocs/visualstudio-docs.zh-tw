---
title: SDK 協助程式進行偵錯 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6655b96ed51cd7cce5e94ce96cedf97517f1872a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942407"
---
# <a name="sdk-helpers-for-debugging"></a>適用於偵錯的 SDK 協助程式
這些函式和宣告是實作 c + + 中的 偵錯引擎、 運算式評估工具和符號提供者的全域 helper 函式。  
  
> [!NOTE]
>  此時沒有任何受管理的版本，這些函式和宣告。  
  
## <a name="overview"></a>總覽  
 為了讓偵錯引擎、 運算式評估工具和符號提供者以供 Visual Studio，您必須註冊它們。 這是藉由設定登錄子機碼和項目，亦稱為 「 設定度量 」。 下列全域函式被設計來簡化更新這些計量的程序。 若要了解這些函式會更新每個登錄子機碼的版面配置的登錄位置，請參閱章節。  
  
## <a name="general-metric-functions"></a>一般計量函式  
 這些是偵錯引擎所使用的一般函式。 運算式評估工具針對特製化函式，並稍後詳述符號提供者。  
  
### <a name="getmetric-method"></a>GetMetric 方法  
 從登錄擷取的基準值。  
  
```cpp  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|參數|描述|  
|---------------|-----------------|  
|pszMachine|[in]將寫入其註冊，可能是遠端機器的名稱 (`NULL`表示本機電腦)。|  
|pszType|[in]其中一個計量的類型。|  
|guidSection|[in]特定引擎、 評估工具、 例外狀況等的 GUID。這會指定計量的類型特定的項目底下的子區段。|  
|pszMetric|[in]要取得的計量。 這會對應至特定值的名稱。|  
|pdwValue|[in]儲存體的計量值的位置。 有數種 GetMetric 可傳回 DWORD （如此範例所示）、 BSTR、 GUID 或 Guid 的陣列。|  
|pszAltRoot|[in]若要使用替代的登錄根目錄。 若要設定`NULL`使用預設值。|  
  
### <a name="setmetric-method"></a>SetMetric 方法  
 在登錄中設定指定的度量值。  
  
```cpp  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|參數|描述|  
|---------------|-----------------|  
|pszType|[in]其中一個計量的類型。|  
|guidSection|[in]特定引擎、 評估工具、 例外狀況等的 GUID。這會指定計量的類型特定的項目底下的子區段。|  
|pszMetric|[in]要取得的計量。 這會對應至特定值的名稱。|  
|dwValue|[in]儲存體的位置中計量的值。 有數種 SetMetric 可儲存 （在此範例中） 的 DWORD、 BSTR、 GUID 或 Guid 的陣列。|  
|fUserSpecific|[in]如果計量是特定使用者，而且它應該寫入至使用者的登錄區，而不是本機電腦的 hive，則為 TRUE。|  
|pszAltRoot|[in]若要使用替代的登錄根目錄。 若要設定`NULL`使用預設值。|  
  
### <a name="removemetric-method"></a>RemoveMetric 方法  
 從登錄中移除指定的計量。  
  
```cpp  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|參數|描述|  
|---------------|-----------------|  
|pszType|[in]其中一個計量的類型。|  
|guidSection|[in]特定引擎、 評估工具、 例外狀況等的 GUID。這會指定計量的類型特定的項目底下的子區段。|  
|pszMetric|[in]要移除度量。 這會對應至特定值的名稱。|  
|pszAltRoot|[in]若要使用替代的登錄根目錄。 若要設定`NULL`使用預設值。|  
  
### <a name="enummetricsections-method"></a>EnumMetricSections 方法  
 列舉在登錄中的不同計量的區段。  
  
```cpp  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|參數|描述|  
|---------------|-----------------|  
|pszMachine|[in]將寫入其註冊，可能是遠端機器的名稱 (`NULL`表示本機電腦)。|  
|pszType|[in]其中一個計量的類型。|  
|rgguidSections|[in、 out]預先配置的 Guid，以填入的陣列。|  
|pdwSize|[in]Guid 可以在儲存的最大數目`rgguidSections`陣列。|  
|pszAltRoot|[in]若要使用替代的登錄根目錄。 若要設定`NULL`使用預設值。|  
  
## <a name="expression-evaluator-functions"></a>運算式評估工具函式  
  
|功能|描述|  
|--------------|-----------------|  
|GetEEMetric|從登錄擷取的基準值。|  
|SetEEMetric|在登錄中設定指定的度量值。|  
|RemoveEEMetric|從登錄中移除指定的計量。|  
|GetEEMetricFile|取得檔案名稱，從指定的計量並將其載入，以字串傳回檔案內容。|  
  
## <a name="exception-functions"></a>例外狀況的函式  
  
|功能|描述|  
|--------------|-----------------|  
|GetExceptionMetric|從登錄擷取的基準值。|  
|SetExceptionMetric|在登錄中設定指定的度量值。|  
|RemoveExceptionMetric|從登錄中移除指定的計量。|  
|RemoveAllExceptionMetrics|從登錄移除所有的例外狀況計量。|  
  
## <a name="symbol-provider-functions"></a>符號提供者函式  
  
|功能|描述|  
|--------------|-----------------|  
|GetSPMetric|從登錄擷取的基準值。|  
|SetSPMetric|在登錄中設定指定的度量值。|  
|RemoveSPMetric|從登錄中移除指定的計量。|  
  
## <a name="enumeration-functions"></a>列舉型別函式  
  
|功能|描述|  
|--------------|-----------------|  
|EnumMetricSections|列舉指定的計量類型的所有度量。|  
|EnumDebugEngine|列舉已註冊的偵錯引擎。|  
|EnumEEs|列舉已註冊的運算式評估工具。|  
|EnumExceptionMetrics|列舉所有例外狀況的度量。|  
  
## <a name="metric-definitions"></a>計量定義  
 這些定義可以用於預先定義的計量名稱。 名稱對應至各種登錄機碼和值名稱都是定義為寬字元字串： 例如， `extern LPCWSTR metrictypeEngine`。  
  
|預先定義的計量類型|描述：基底機碼...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|所有偵錯引擎的計量。|  
|metrictypePortSupplier|所有連接埠供應商的計量。|  
|metrictypeException|所有例外狀況的度量。|  
|metricttypeEEExtension|所有的運算式評估工具延伸模組。|  
  
|偵錯引擎屬性|描述|  
|-----------------------------|-----------------|  
|metricAddressBP|設定為非零值，表示支援位址中斷點。|  
|metricAlwaysLoadLocal|設定為非零值以一律載入在本機的偵錯引擎。|  
|metricLoadInDebuggeeSession|未使用|  
|metricLoadedByDebuggee|設定為非零值，表示具有或正在進行偵錯程式，一律會載入偵錯引擎。|  
|metricAttach|設定為非零值以表示支援以便附加到現有的程式。|  
|metricCallStackBP|設定為非零值，表示支援呼叫堆疊中斷點。|  
|metricConditionalBP|設定為非零值以表示支援的設定條件式中斷點。|  
|metricDataBP|設定為非零值以表示支援在資料變更中斷點的設定。|  
|metricDisassembly|設定為非零，表示反組譯碼清單的生產環境的支援。|  
|metricDumpWriting|設定為非零值以表示傾印寫入 （傾印至輸出裝置的記憶體） 的支援。|  
|metricENC|設定為非零，表示支援編輯後繼續。 **注意：** 自訂的偵錯引擎應該永遠不會將此設定，或應一律設為 0。|  
|metricExceptions|設定為非零值以表示支援的例外狀況。|  
|metricFunctionBP|設定為非零值，表示支援具名中斷點 （中斷呼叫特定函式名稱時的中斷點）。|  
|metricHitCountBP|設定為非零值以表示支援 「 點擊點 」 的中斷點 （只有在達到特定次數之後，才會觸發的中斷點） 的設定。|  
|metricJITDebug|設定為非零，表示支援在 just-in-time 偵錯 （偵錯工具啟動時執行的處理序中發生例外狀況）。|  
|metricMemory|未使用|  
|metricPortSupplier|如果，設定這個連接埠提供者的 clsid 實作其中一個。|  
|metricRegisters|未使用|  
|metricSetNextStatement|設定為非零值以表示支援的設定下一個陳述式 （這會略過中繼的陳述式執行）。|  
|metricSuspendThread|設定為非零值以表示支援暫止執行緒的執行。|  
|metricWarnIfNoSymbols|設定為非零值，表示沒有符號時，會通知使用者。|  
|metricProgramProvider|設定為程式提供者的 CLSID。|  
|metricAlwaysLoadProgramProviderLocal|將此設為非零，表示程式提供者應該一律會載入在本機的。|  
|metricEngineCanWatchProcess|設定為非零值，指出偵錯引擎會監看處理程序事件，而程式的提供者。|  
|metricRemoteDebugging|設定為非零值以表示遠端偵錯的支援。|  
|metricEncUseNativeBuilder|將此設為非零，表示編輯後繼續的管理員應該使用偵錯引擎的 encbuild.dll 編輯後繼續建置的。 **注意：** 自訂的偵錯引擎應該永遠不會將此設定，或應一律設為 0。|  
|metricLoadUnderWOW64|將此設為非零值，表示在 WOW 下偵錯項目處理序中應該載入，偵錯引擎，當偵錯 64 位元處理程序;否則，偵錯引擎會載入 Visual Studio 處理序 （這在 WOW64 下執行） 中。|  
|metricLoadProgramProviderUnderWOW64|將此設為非零值表示 64 位元處理序在 WOW; 下進行偵錯時，程式提供者，應該在偵錯項目程序中載入否則，會載入 Visual Studio 處理序中。|  
|metricStopOnExceptionCrossingManagedBoundary|設定為非零值，表示跨 managed/unmanaged 程式碼界限擲回未處理的例外狀況時，應該停止處理程序。|  
|metricAutoSelectPriority|設定為自動選擇的偵錯引擎 （優先順序較高的值等於更高版本） 的優先權。|  
|metricAutoSelectIncompatibleList|登錄機碼包含所指定要忽略的偵錯引擎 Guid 中自動選取項目。 這些項目都是數字 （0、 1、 2，依此類推） 使用以字串表示的 GUID。|  
|metricIncompatibleList|登錄機碼包含所指定的 Guid，偵錯引擎與此偵錯引擎不相容的項目。|  
|metricDisableJITOptimization|設定為非零值表示應該在偵錯期間停用 （適用於 managed 程式碼）-just-in-time 最佳化。|  
  
|運算式評估工具內容|描述|  
|-------------------------------------|-----------------|  
|metricEngine|這會保留偵錯引擎，支援指定的運算式評估工具的數目。|  
|metricPreloadModules|設定為非零值表示的運算式評估工具對程式啟動時，應預先載入的模組。|  
|metricThisObjectName|設定為"this"的物件名稱。|  
  
|運算式評估工具延伸模組屬性|描述|  
| - |-----------------|  
|metricExtensionDll|支援此延伸模組 dll 名稱。|  
|metricExtensionRegistersSupported|支援的暫存器的清單。|  
|metricExtensionRegistersEntryPoint|用於存取暫存器的進入點。|  
|metricExtensionTypesSupported|支援的類型清單。|  
|metricExtensionTypesEntryPoint|進入點存取型別。|  
  
|連接埠供應商屬性|描述|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|（對話方塊使用者可以使用選取的連接埠，然後新增要用於偵錯的連接埠） 連接埠選擇器的 CLSID。|  
|metricDisallowUserEnteredPorts|如果使用者輸入連接埠無法新增至連接埠提供者為非零 （基本上是唯讀，這讓連接埠選擇器對話方塊）。|  
|metricPidBase|配置處理序識別碼時，連接埠提供者所使用的基底的處理序識別碼。|  
  
|預先定義的預存程序存放區類型|描述|  
|-------------------------------|-----------------|  
|storetypeFile|符號會儲存在個別的檔案。|  
|storetypeMetadata|符號會儲存為組件中的中繼資料。|  
  
|其他屬性|描述|  
|------------------------------|-----------------|  
|metricShowNonUserCode|設定為非零值，以顯示 nonuser 程式碼。|  
|metricJustMyCodeStepping|設定為非零值，指出要逐步執行可執行只有在使用者程式碼中。|  
|metricCLSID|針對特定的計量類型物件的 CLSID。|  
|MetricName|針對特定的計量類型物件的易記名稱。|  
|metricLanguage|語言名稱。|  
  
## <a name="registry-locations"></a>登錄位置  
 度量是讀取和寫入至登錄，具體而言是在`VisualStudio`子機碼。  
  
> [!NOTE]
>  大部分的情況下，在 HKEY_LOCAL_MACHINE 機碼會寫入計量。 不過，有時候 HKEY_CURRENT_USER 要目的地的索引鍵。 Dbgmetric.lib 會處理這兩個金鑰。 當取得度量時，它會搜尋 HKEY_CURRENT_USER 先，接著 HKEY_LOCAL_MACHINE。 當它設定計量時，參數會指定要使用哪一個最上層機碼。  
  
 *[登錄機碼]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[版本 root]*\  
  
 *[計量 root]*\  
  
 *[計量類型]*\  
  
 *[計量] = [計量值]*  
  
 *[計量] = [計量值]*  
  
 *[計量] = [計量值]*  
  
|預留位置|描述|  
|-----------------|-----------------|  
|*[登錄機碼]*|`HKEY_CURRENT_USER` 或 `HKEY_LOCAL_MACHINE`。|  
|*[版本 root]*|Visual Studio 的版本 (例如`7.0`， `7.1`，或`8.0`)。 不過，這個根目錄也可以修改使用 **/rootsuffix**切換至**devenv.exe**。 VSIP，對於這個修飾詞通常是**Exp**，因此版本根是，比方說，8.0Exp。|  
|*[計量 root]*|這是`AD7Metrics`或`AD7Metrics(Debug)`，取決於是否使用 dbgmetric.lib 的偵錯版本。 **注意：** 若要應遵守是否使用 dbgmetric.lib 時，此命名慣例，如果您有偵錯和發行之間的差異必須在登錄中反映出來的版本。|  
|*[計量類型]*|要寫入的度量類型： `Engine`， `ExpressionEvaluator`，`SymbolProvider`等等。這些全都定義如所示為 dbgmetric.h `metricTypeXXXX`，其中`XXXX`是特定型別名稱。|  
|*[計量]*|若要將度量指派值的項目名稱。 實際組織的度量取決於計量的類型。|  
|*[計量值]*|指派給計量的值。 此值應該有 （字串、 數字等） 的類型取決於計量。|  
  
> [!NOTE]
>  所有的 Guid 會儲存在格式`{GUID}`。 例如， `{123D150B-FA18-461C-B218-45B3E4589F9B}` 。  
  
### <a name="debug-engines"></a>偵錯引擎  
 以下是在登錄中的偵錯引擎度量資訊的組織。 `Engine` 是偵錯引擎的計量類型名稱，以及對應至 *[計量類型]* 上述的登錄樹狀子目錄中。  
  
 `Engine`\  
  
 *[引擎 guid]*\  
  
 `CLSID` = *[類別 guid]*  
  
 *[計量] = [計量值]*  
  
 *[計量] = [計量值]*  
  
 *[計量] = [計量值]*  
  
 `PortSupplier`\  
  
 `0` = *[連接埠供應商 guid]*  
  
 `1` = *[連接埠供應商 guid]*  
  
|預留位置|描述|  
|-----------------|-----------------|  
|*[引擎 guid]*|偵錯引擎的 GUID。|  
|*[類別 guid]*|實作此偵錯引擎的類別 GUID。|  
|*[連接埠供應商 guid]*|如果有的話，連接埠供應商的 GUID。 許多偵錯引擎會使用預設連接埠提供者，並因此不會指定他們自己的供應商。 在此情況下，子機碼`PortSupplier`就不會有。|  
  
### <a name="port-suppliers"></a>連接埠提供者  
 以下是在登錄中的連接埠供應商度量資訊的組織。 `PortSupplier` 為連接埠提供者的度量型別名稱且對應於 *[計量類型]*。  
  
 `PortSupplier`\  
  
 *[連接埠供應商 guid]*\  
  
 `CLSID` = *[類別 guid]*  
  
 *[計量] = [計量值]*  
  
 *[計量] = [計量值]*  
  
|預留位置|描述|  
|-----------------|-----------------|  
|*[連接埠供應商 guid]*|連接埠提供者的 GUID|  
|*[類別 guid]*|類別會實作此連接埠提供者的 GUID|  
  
### <a name="symbol-providers"></a>符號提供者  
 以下是在登錄中的符號供應商度量資訊的組織。 `SymbolProvider` 符號提供者的度量型別名稱和對應至 *[計量類型]*。  
  
 `SymbolProvider`\  
  
 *[符號提供者 guid]*\  
  
 `file`\  
  
 `CLSID` = *[類別 guid]*  
  
 *[計量] = [計量值]*  
  
 *[計量] = [計量值]*  
  
 `metadata`\  
  
 `CLSID` = *[類別 guid]*  
  
 *[計量] = [計量值]*  
  
 *[計量] = [計量值]*  
  
|預留位置|描述|  
|-----------------|-----------------|  
|*[符號提供者 guid]*|符號提供者 GUID|  
|*[類別 guid]*|類別會實作這個符號提供者的 GUID|  
  
### <a name="expression-evaluators"></a>運算式評估工具  
 以下是在登錄中的運算式評估工具度量資訊的組織。 `ExpressionEvaluator` 運算式評估工具的計量類型名稱，並對應至 *[計量類型]*。  
  
> [!NOTE]
>  計量類型，如`ExpressionEvaluator`中未定義 dbgmetric.h，因為它會假設所有計量變更運算式評估工具會通過適當的運算式評估工具計量函式 (的版面配置`ExpressionEvaluator`子機碼有點變得複雜，因此詳細資料會隱藏 dbgmetric.lib 內）。  
  
 `ExpressionEvaluator`\  
  
 *[語言 guid]*\  
  
 *[供應商 guid]*\  
  
 `CLSID` = *[類別 guid]*  
  
 *[計量] = [計量值]*  
  
 *[計量] = [計量值]*  
  
 `Engine`\  
  
 `0` = *[偵錯引擎 guid]*  
  
 `1` = *[偵錯引擎 guid]*  
  
|預留位置|描述|  
|-----------------|-----------------|  
|*[語言 guid]*|一種語言的 GUID|  
|*[供應商 guid]*|供應商的 GUID|  
|*[類別 guid]*|類別會實作此運算式評估工具的 GUID|  
|*[偵錯引擎 guid]*|此運算式評估工具的運作方式與偵錯引擎的 GUID|  
  
### <a name="expression-evaluator-extensions"></a>運算式評估工具延伸模組  
 以下是在登錄中的運算式評估工具擴充計量的組織。 `EEExtensions` 是計量的類型名稱的運算式評估工具延伸模組和對應至 *[計量類型]*。  
  
 `EEExtensions`\  
  
 *[延伸模組 guid]*\  
  
 *[計量] = [計量值]*  
  
 *[計量] = [計量值]*  
  
|預留位置|描述|  
|-----------------|-----------------|  
|*[延伸模組 guid]*|運算式評估工具延伸模組的 GUID|  
  
### <a name="exceptions"></a>例外狀況  
 以下是在登錄中的例外狀況度量資訊的組織。 `Exception` 例外狀況的度量型別名稱和對應至 *[計量類型]*。  
  
 `Exception`\  
  
 *[偵錯引擎 guid]*\  
  
 *[例外狀況類型]*\  
  
 *[例外狀況]*\  
  
 *[計量] = [計量值]*  
  
 *[計量] = [計量值]*  
  
 *[例外狀況]*\  
  
 *[計量] = [計量值]*  
  
 *[計量] = [計量值]*  
  
|預留位置|描述|  
|-----------------|-----------------|  
|*[偵錯引擎 guid]*|支援例外狀況，偵錯引擎的 GUID。|  
|*[例外狀況類型]*|識別可以處理的例外狀況類別的子機碼一般標題。 一般名稱**c + + 例外狀況**， **Win32 例外狀況**， **Common Language Runtime 例外狀況**，以及**原生執行階段檢查**。 這些名稱也會用來識別特定類別的例外狀況給使用者。|  
|*[例外狀況]*|例外狀況的名稱： 例如， **_com_error**或是**Control-break**。 這些名稱也會用來識別使用者的特定例外狀況。|  
  
## <a name="requirements"></a>需求  
 這些檔案位於[!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)]SDK 安裝目錄 (根據預設， *[磁碟機]* \Program Files\Microsoft Visual Studio 2010 SDK\\)。  
  
 標頭： includes\dbgmetric.h  
  
 程式庫： libs\ad2de.lib、 libs\dbgmetric.lib  
  
## <a name="see-also"></a>另請參閱  
 [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)