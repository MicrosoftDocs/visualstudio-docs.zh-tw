---
title: 用於偵錯工具的 SDK 協助程式 |Microsoft Docs
description: 深入瞭解函式和宣告，這些函式和宣告是全域 helper 函式，可在 c + + 中執行 debug 引擎、運算式評估工具和符號提供者
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b98914d4e7fc2d63fd6cc9f79789c389e19b784
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935998"
---
# <a name="sdk-helpers-for-debugging"></a>適用於偵錯的 SDK 協助程式
這些函式和宣告都是全域 helper 函式，可用於在 c + + 中執行 debug 引擎、運算式評估工具和符號提供者。

> [!NOTE]
> 目前沒有這些函數和宣告的 managed 版本。

## <a name="overview"></a>概觀
 為了讓 Visual Studio 要使用的偵錯工具引擎、運算式評估工具和符號提供者，必須先註冊它們。 這是藉由設定登錄子機碼和專案來完成，也就是所謂的「設定計量」。 下列全域函式的設計目的是要簡化更新這些計量的流程。 請參閱登錄位置一節，以瞭解這些函式所更新的每個登錄子機碼的版面配置。

## <a name="general-metric-functions"></a>一般標準函式
 這些是偵錯工具引擎所使用的一般函式。 運算式評估工具和符號提供者的特殊函式將于稍後詳述。

### <a name="getmetric-method"></a>>getmetric 方法
 從登錄抓取度量值。

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

|參數|Description|
|---------------|-----------------|
|pszMachine|在可能會寫入註冊 (的遠端電腦名稱稱， `NULL` 表示本機電腦) 。|
|pszType|在其中一個度量類型。|
|guidSection|在特定引擎、評估工具、例外狀況等的 GUID。這會指定特定專案之度量類型下的子區段。|
|pszMetric|在要取得的度量。 這會對應到特定的值名稱。|
|pdwValue|在度量值的儲存位置。 有數種 >getmetric 可傳回 DWORD (，如下列範例所示) 、BSTR、GUID 或 Guid 陣列。|
|pszAltRoot|在要使用的替代登錄根目錄。 將設定為， `NULL` 以使用預設值。|

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

|參數|Description|
|---------------|-----------------|
|pszType|在其中一個度量類型。|
|guidSection|在特定引擎、評估工具、例外狀況等的 GUID。這會指定特定專案之度量類型下的子區段。|
|pszMetric|在要取得的度量。 這會對應到特定的值名稱。|
|dwValue|在度量中值的儲存位置。 在此範例中，有數種 SetMetric 可儲存 DWORD () 、BSTR、GUID 或 Guid 陣列。|
|fUserSpecific|在如果計量是使用者專屬的，且應寫入使用者的 hive 而非本機電腦 hive，則為 TRUE。|
|pszAltRoot|在要使用的替代登錄根目錄。 將設定為， `NULL` 以使用預設值。|

### <a name="removemetric-method"></a>RemoveMetric 方法
 從登錄中移除指定的度量。

```cpp
HRESULT RemoveMetric(
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   LPCWSTR pszAltRoot
);
```

|參數|Description|
|---------------|-----------------|
|pszType|在其中一個度量類型。|
|guidSection|在特定引擎、評估工具、例外狀況等的 GUID。這會指定特定專案之度量類型下的子區段。|
|pszMetric|在要移除的度量。 這會對應到特定的值名稱。|
|pszAltRoot|在要使用的替代登錄根目錄。 將設定為， `NULL` 以使用預設值。|

### <a name="enummetricsections-method"></a>EnumMetricSections 方法
 列舉登錄中的各種度量區段。

```cpp
HRESULT EnumMetricSections(
   LPCWSTR pszMachine,
   LPCWSTR pszType,
   GUID *  rgguidSections,
   DWORD * pdwSize,
   LPCWSTR pszAltRoot
);
```

|參數|Description|
|---------------|-----------------|
|pszMachine|在可能會寫入註冊 (的遠端電腦名稱稱， `NULL` 表示本機電腦) 。|
|pszType|在其中一個度量類型。|
|rgguidSections|[in，out]要填入的預先配置 Guid 陣列。|
|pdwSize|在可以儲存在陣列中的最大 Guid 數目 `rgguidSections` 。|
|pszAltRoot|在要使用的替代登錄根目錄。 將設定為， `NULL` 以使用預設值。|

## <a name="expression-evaluator-functions"></a>運算式評估工具函數

|函式|描述|
|--------------|-----------------|
|GetEEMetric|從登錄抓取度量值。|
|SetEEMetric|在登錄中設定指定的度量值。|
|RemoveEEMetric|從登錄中移除指定的度量。|
|GetEEMetricFile|從指定的度量取得檔案名，並將其載入，並以字串形式傳回檔案內容。|

## <a name="exception-functions"></a>例外狀況函式

|函式|描述|
|--------------|-----------------|
|GetExceptionMetric|從登錄抓取度量值。|
|SetExceptionMetric|在登錄中設定指定的度量值。|
|RemoveExceptionMetric|從登錄中移除指定的度量。|
|RemoveAllExceptionMetrics|從登錄中移除所有例外狀況度量。|

## <a name="symbol-provider-functions"></a>符號提供者函式

|函式|描述|
|--------------|-----------------|
|GetSPMetric|從登錄抓取度量值。|
|SetSPMetric|在登錄中設定指定的度量值。|
|RemoveSPMetric|從登錄中移除指定的度量。|

## <a name="enumeration-functions"></a>列舉函數

|函式|描述|
|--------------|-----------------|
|EnumMetricSections|列舉指定之計量類型的所有計量。|
|EnumDebugEngine|列舉已註冊的調試引擎。|
|EnumEEs|列舉已註冊的運算式評估工具。|
|EnumExceptionMetrics|列舉所有例外狀況度量。|

## <a name="metric-definitions"></a>計量定義
 這些定義可以用於預先定義的度量名稱。 這些名稱會對應至各種登錄機碼和值名稱，而且全都定義為寬字元字串：例如， `extern LPCWSTR metrictypeEngine` 。

|預先定義的度量類型|描述：的基底索引鍵 .。。|
|-----------------------------|---------------------------------------|
|metrictypeEngine|所有的 debug engine 度量。|
|metrictypePortSupplier|所有埠供應商度量。|
|metrictypeException|所有例外狀況度量。|
|metricttypeEEExtension|所有運算式評估工具延伸模組。|

|Debug Engine 屬性|Description|
|-----------------------------|-----------------|
|metricAddressBP|設定為非零，表示支援位址中斷點。|
|metricAlwaysLoadLocal|設定為非零，以便永遠在本機載入 debug engine。|
|metricLoadInDebuggeeSession|未使用|
|metricLoadedByDebuggee|設定為非零，表示將一律使用或由正在進行調試的程式載入 debug engine。|
|metricAttach|設定為非零，表示支援附加至現有的程式。|
|metricCallStackBP|設定為非零，表示支援呼叫堆疊中斷點。|
|metricConditionalBP|設定為非零，表示支援條件式中斷點的設定。|
|metricDataBP|設定為非零，表示支援在資料變更時設定中斷點。|
|metricDisassembly|設定為非零，表示支援反組解碼清單。|
|metricDumpWriting|設定為非零，表示支援傾印寫入 (將記憶體傾印寫入輸出裝置) 。|
|metricENC|設定為非零，表示支援編輯後繼續。 **注意：**  自訂的 debug engine 永遠不應該設定此設定，或一律將它設定為0。|
|metricExceptions|設定為非零，表示支援例外狀況。|
|metricFunctionBP|設定為非零，表示支援已命名中斷點 (中斷點會在呼叫特定函式名稱) 時中斷。|
|metricHitCountBP|設定為非零，表示支援「叫用點」中斷點的設定 (中斷點只會在達到特定次數) 時才觸發。|
|metricJITDebug|設定為非零表示支援即時偵錯工具 (當執行中的進程) 發生例外狀況時，就會啟動偵錯工具。|
|metricMemory|未使用|
|metricPortSupplier|將此設定為埠供應商的 CLSID （如果有的話）。|
|metricRegisters|未使用|
|metricSetNextStatement|設定為非零，表示支援設定下一個語句 (這會略過) 中繼語句的執行。|
|metricSuspendThread|設定為非零，表示支援暫停執行緒執行。|
|metricWarnIfNoSymbols|設定為非零，表示如果沒有符號，應通知使用者。|
|metricProgramProvider|將此設定為程式提供者的 CLSID。|
|metricAlwaysLoadProgramProviderLocal|將此設定為非零，表示應該一律將程式提供者載入至本機。|
|metricEngineCanWatchProcess|將此設定為非零，表示 debug engine 會監看進程事件，而不是程式提供者。|
|metricRemoteDebugging|將此設定為非零，表示支援遠端偵錯程式。|
|metricEncUseNativeBuilder|將此設為非零，表示「編輯後繼續」管理員應該使用 debug engine 的 encbuild.dll 來建立「編輯後繼續」。 **注意：**  自訂的 debug engine 永遠不應該設定此設定，或一律將它設定為0。|
|metricLoadUnderWOW64|將此設為非零值，表示在偵錯工具64位進程時，應在 WOW 下將 debug engine 載入至物件進程;否則，將會在 WOW64) 下執行的 Visual Studio 進程 (中載入 debug engine。|
|metricLoadProgramProviderUnderWOW64|將此設定為非零，表示在 WOW 下進行64位進程的偵錯工具時，應將程式提供者載入偵錯工具進程中。否則，它會載入 Visual Studio 進程中。|
|metricStopOnExceptionCrossingManagedBoundary|將此設定為非零，表示如果跨受控/非受控程式碼界限擲回未處理的例外狀況，則會停止處理常式。|
|metricAutoSelectPriority|將此值設定為自動選取 debug engine 的優先順序， (更高的值等於優先順序較高的) 。|
|metricAutoSelectIncompatibleList|包含專案的登錄機碼，這些專案會指定要在自動選取範圍內忽略之 debug 引擎的 Guid。 這些專案是數位 (0、1、2，依此類推，) 具有以字串表示的 GUID。|
|metricIncompatibleList|包含專案的登錄機碼，這些專案會指定與此 debug engine 不相容的 debug engine Guid。|
|metricDisableJITOptimization|將此設為非零，表示 managed 程式碼) 的即時優化 (應在偵錯工具期間停用。|

|運算式評估工具屬性|Description|
|-------------------------------------|-----------------|
|metricEngine|這會保留支援指定運算式評估工具的偵錯工具引擎數目。|
|metricPreloadModules|將此設定為非零，表示在針對程式啟動運算式評估工具時，應該預先載入模組。|
|metricThisObjectName|將此設定為 "this" 物件名稱。|

|運算式評估工具延伸模組屬性|Description|
| - |-----------------|
|metricExtensionDll|支援此延伸模組之 dll 的名稱。|
|metricExtensionRegistersSupported|支援的暫存器清單。|
|metricExtensionRegistersEntryPoint|存取暫存器的進入點。|
|metricExtensionTypesSupported|支援的類型清單。|
|metricExtensionTypesEntryPoint|存取類型的進入點。|

|埠供應商屬性|Description|
|------------------------------|-----------------|
|metricPortPickerCLSID|埠選擇器的 CLSID (一個對話方塊，使用者可使用此對話方塊來選取埠，並新增用來) 進行偵錯工具的埠。|
|metricDisallowUserEnteredPorts|如果使用者輸入的埠無法新增至埠供應商，則為非零 (這會讓 [埠選擇器] 對話方塊本質上是唯讀) 。|
|metricPidBase|配置處理常式識別碼時，埠供應商所使用的基底處理序識別碼。|

|預先定義的 SP 存放區類型|Description|
|-------------------------------|-----------------|
|storetypeFile|符號會儲存在不同的檔案中。|
|storetypeMetadata|符號會以中繼資料的形式儲存在元件中。|

|其他屬性|Description|
|------------------------------|-----------------|
|metricShowNonUserCode|將此設定為非零，以顯示 nonuser 程式碼。|
|metricJustMyCodeStepping|將此設定為非零，表示逐步執行只能在使用者程式碼中執行。|
|metricCLSID|特定度量類型之物件的 CLSID。|
|metricName|特定度量類型之物件的易記名稱。|
|metricLanguage|語言名稱。|

## <a name="registry-locations"></a>登錄位置
 系統會在登錄中讀取和寫入度量，特別是在子機碼中 `VisualStudio` 。

> [!NOTE]
> 大部分的情況下，計量會寫入 HKEY_LOCAL_MACHINE 金鑰。 不過，有時候 HKEY_CURRENT_USER 將會是目的地金鑰。 Dbgmetric 會處理這兩個索引鍵。 取得度量時，會先搜尋 HKEY_CURRENT_USER，然後再 HKEY_LOCAL_MACHINE。 當設定計量時，參數會指定要使用的最上層金鑰。

 *[登錄機碼]*\

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[版本根目錄]*\

 *[計量根目錄]*\

 *[度量類型]*\

 *[度量] = [度量值]*

 *[度量] = [度量值]*

 *[度量] = [度量值]*

|預留位置|描述|
|-----------------|-----------------|
|*[登錄機碼]*|`HKEY_CURRENT_USER` 或 `HKEY_LOCAL_MACHINE`。|
|*[版本根目錄]*|Visual Studio 的版本 (例如，、 `7.0` `7.1` 或 `8.0`) 。 不過，您也可以使用 **/rootsuffix** 參數將此根修改為 **devenv.exe**。 對於 VSIP 而言，此修飾詞通常是 **Exp**，因此版本根目錄會是，例如 8.0 Exp。|
|*[計量根目錄]*|這是 `AD7Metrics` 或 `AD7Metrics(Debug)` ，視是否使用 dbgmetric 的偵錯工具版本而定。 **注意：**  無論是否使用 dbgmetric，如果必須反映在登錄中的 debug 和 release 版本之間有差異，應該遵守此命名慣例。|
|*[度量類型]*|要寫入的度量類型： `Engine` 、、等等 `ExpressionEvaluator` `SymbolProvider` 。這些全都定義為 dbgmetric 中 `metricTypeXXXX` 的，其中 `XXXX` 是特定的類型名稱。|
|*美制*|要為其指派值的專案名稱，以便設定度量。 計量的實際組織取決於度量類型。|
|*[度量值]*|指派給度量的值。 值應該有 (字串、數位等的型別 ) 取決於度量。|

> [!NOTE]
> 所有 Guid 都會以的格式儲存 `{GUID}` 。 例如： `{123D150B-FA18-461C-B218-45B3E4589F9B}` 。

### <a name="debug-engines"></a>Debug 引擎
 以下是在登錄中的「debug 引擎」度量組織。 `Engine` 這是偵測引擎的計量型別名稱，而且對應于上述登錄子樹中的 *[計量類型]* 。

 `Engine`\

 *[引擎 guid]*\

 `CLSID` = *[類別 guid]*

 *[度量] = [度量值]*

 *[度量] = [度量值]*

 *[度量] = [度量值]*

 `PortSupplier`\

 `0` = *[埠供應商 guid]*

 `1` = *[埠供應商 guid]*

|預留位置|描述|
|-----------------|-----------------|
|*[引擎 guid]*|Debug 引擎的 GUID。|
|*[類別 guid]*|實作為此偵錯工具引擎之類別的 GUID。|
|*[埠供應商 guid]*|埠供應商的 GUID （如果有的話）。 許多 debug engine 都使用預設的埠供應商，因此不會指定自己的供應商。 在此情況下，子機碼 `PortSupplier` 將不存在。|

### <a name="port-suppliers"></a>連接埠提供者
 以下是登錄中的埠供應商計量組織。 `PortSupplier` 是埠供應商的度量類型名稱，並對應至 *[計量類型]*。

 `PortSupplier`\

 *[埠供應商 guid]*\

 `CLSID` = *[類別 guid]*

 *[度量] = [度量值]*

 *[度量] = [度量值]*

|預留位置|描述|
|-----------------|-----------------|
|*[埠供應商 guid]*|埠供應商的 GUID|
|*[類別 guid]*|可執行此埠供應商之類別的 GUID|

### <a name="symbol-providers"></a>符號提供者
 以下是登錄中符號供應商計量的組織。 `SymbolProvider` 這是符號提供者的度量型別名稱，而且會對應到 *[公制 type]*。

 `SymbolProvider`\

 *[符號提供者 guid]*\

 `file`\

 `CLSID` = *[類別 guid]*

 *[度量] = [度量值]*

 *[度量] = [度量值]*

 `metadata`\

 `CLSID` = *[類別 guid]*

 *[度量] = [度量值]*

 *[度量] = [度量值]*

|預留位置|描述|
|-----------------|-----------------|
|*[符號提供者 guid]*|符號提供者的 GUID|
|*[類別 guid]*|實作為符號提供者之類別的 GUID|

### <a name="expression-evaluators"></a>運算式評估工具
 以下是登錄中運算式評估工具度量的組織。 `ExpressionEvaluator` 這是運算式評估工具的度量類型名稱，並且對應至 *[計量類型]*。

> [!NOTE]
> 的計量類型 `ExpressionEvaluator` 未定義于 dbgmetric 中，因為假設運算式評估工具的所有計量變更都將經過適當的運算式評估工具度量函式 (子機碼的版面配置 `ExpressionEvaluator` 有點複雜，因此詳細資料會隱藏在 dbgmetric) 內。

 `ExpressionEvaluator`\

 *[語言 guid]*\

 *[廠商 guid]*\

 `CLSID` = *[類別 guid]*

 *[度量] = [度量值]*

 *[度量] = [度量值]*

 `Engine`\

 `0` = *[debug engine guid]*

 `1` = *[debug engine guid]*

|預留位置|描述|
|-----------------|-----------------|
|*[語言 guid]*|語言的 GUID|
|*[廠商 guid]*|廠商的 GUID|
|*[類別 guid]*|實作為此運算式評估工具之類別的 GUID|
|*[debug engine guid]*|此運算式評估工具可搭配使用的偵錯工具的 GUID|

### <a name="expression-evaluator-extensions"></a>運算式評估工具延伸模組
 以下是登錄中運算式評估工具延伸計量的組織。 `EEExtensions` 這是運算式評估工具延伸模組的度量類型名稱，並對應至 *[計量類型]*。

 `EEExtensions`\

 *[擴充 guid]*\

 *[度量] = [度量值]*

 *[度量] = [度量值]*

|預留位置|描述|
|-----------------|-----------------|
|*[擴充 guid]*|運算式評估工具延伸模組的 GUID|

### <a name="exceptions"></a>例外狀況
 以下是登錄中的例外狀況度量組織。 `Exception` 這是例外狀況的計量型別名稱，而且會對應到 *[計量類型]*。

 `Exception`\

 *[debug engine guid]*\

 *[例外狀況類型]*\

 *意外*\

 *[度量] = [度量值]*

 *[度量] = [度量值]*

 *意外*\

 *[度量] = [度量值]*

 *[度量] = [度量值]*

|預留位置|描述|
|-----------------|-----------------|
|*[debug engine guid]*|支援例外狀況之偵錯工具引擎的 GUID。|
|*[例外狀況類型]*|子機碼的一般標題，可識別可處理的例外狀況類別。 一般名稱是 **c + + 例外** 狀況、 **Win32 例外** 狀況、 **Common Language Runtime 例外** 狀況，以及 **原生 Run-Time 檢查**。 這些名稱也用來識別使用者的特定例外狀況類別。|
|*意外*|例外狀況的名稱：例如 **_com_error** 或 **控制中斷**。 這些名稱也用來識別使用者的特定例外狀況。|

## <a name="requirements"></a>規格需求
 這些檔案位於 [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK 安裝目錄 (預設為 *[磁片磁碟機]* \Program FILES\MICROSOFT Visual Studio 2010 SDK \\) 。

 標頭： includes\dbgmetric。h

 程式庫： libs\ad2de.lib、libs\dbgmetric.lib

## <a name="see-also"></a>另請參閱
- [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
