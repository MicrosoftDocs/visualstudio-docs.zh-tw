---
title: "偵錯 SDK Helper |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b87756f52cb1506be30014331d63eec5d15beff4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sdk-helpers-for-debugging"></a>SDK 進行偵錯的協助程式
這些函式和宣告是 c + + 中實作偵錯引擎，運算式評估工具，符號提供者的全域 helper 函式。  
  
> [!NOTE]
>  在此時間有不受管理的這些函式和宣告版本。  
  
## <a name="overview"></a>總覽  
 為了讓偵錯引擎，運算式評估工具，符號提供者使用由 Visual Studio，您必須註冊它們。 這是藉由設定登錄子機碼和項目，亦稱為 「 設定度量 」。 下列全域函式被為了讓您輕鬆更新這些度量的程序。 若要找出這些函式會更新每個登錄子機碼的版面配置的登錄位置上，請參閱 > 一節。  
  
## <a name="general-metric-functions"></a>一般標準函式  
 這些是一般的偵錯引擎所使用的功能。 針對運算式評估工具特製化函式，並稍後詳述符號提供者。  
  
### <a name="getmetric-method"></a>GetMetric 方法  
 從登錄擷取公制值。  
  
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
|pszMachine|[in]將寫入其登錄可能是遠端電腦名稱 (`NULL`表示本機電腦)。|  
|pszType|[in]其中一種衡量標準的類型。|  
|guidSection|[in]特定引擎、 評估工具、 例外狀況和其他內容的 GUID。這會指定度量的型別特定的項目底下的子區段。|  
|pszMetric|[in]取得度量。 這會對應至特定值的名稱。|  
|pdwValue|[in]從度量值的儲存位置。 有數款 GetMetric 可傳回 DWORD （如此範例所示）、 BSTR、 GUID 或陣列的 Guid。|  
|pszAltRoot|[in]若要使用替代的登錄根目錄。 設定為`NULL`使用預設值。|  
  
### <a name="setmetric-method"></a>SetMetric 方法  
 設定登錄中指定的度量值。  
  
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
|pszType|[in]其中一種衡量標準的類型。|  
|guidSection|[in]特定引擎、 評估工具、 例外狀況和其他內容的 GUID。這會指定度量的型別特定的項目底下的子區段。|  
|pszMetric|[in]取得度量。 這會對應至特定值的名稱。|  
|dwValue|[in]度量中值的儲存位置。 有數款 SetMetric 可以儲存 （在此範例中） 的 DWORD、 BSTR、 GUID 或陣列的 Guid。|  
|fUserSpecific|[in]如果度量是特定使用者，且應該寫入使用者的登錄區，而不是本機電腦的登錄區，則為 TRUE。|  
|pszAltRoot|[in]若要使用替代的登錄根目錄。 設定為`NULL`使用預設值。|  
  
### <a name="removemetric-method"></a>RemoveMetric 方法  
 從登錄移除指定的標準。  
  
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
|pszType|[in]其中一種衡量標準的類型。|  
|guidSection|[in]特定引擎、 評估工具、 例外狀況和其他內容的 GUID。這會指定度量的型別特定的項目底下的子區段。|  
|pszMetric|[in]要移除度量。 這會對應至特定值的名稱。|  
|pszAltRoot|[in]若要使用替代的登錄根目錄。 設定為`NULL`使用預設值。|  
  
### <a name="enummetricsections-method"></a>EnumMetricSections 方法  
 列舉在登錄中的不同度量區段。  
  
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
|pszMachine|[in]將寫入其登錄可能是遠端電腦名稱 (`NULL`表示本機電腦)。|  
|pszType|[in]其中一種衡量標準的類型。|  
|rgguidSections|[in、 out]預先配置的 Guid，以填入陣列。|  
|pdwSize|[in]Guid 可儲存中的最大數目`rgguidSections`陣列。|  
|pszAltRoot|[in]若要使用替代的登錄根目錄。 設定為`NULL`使用預設值。|  
  
## <a name="expression-evaluator-functions"></a>運算式評估工具函式  
  
|功能|描述|  
|--------------|-----------------|  
|GetEEMetric|從登錄擷取公制值。|  
|SetEEMetric|設定登錄中指定的度量值。|  
|RemoveEEMetric|從登錄移除指定的標準。|  
|GetEEMetricFile|取得檔案名稱，從指定的度量，並載入它，以字串形式傳回檔案內容。|  
  
## <a name="exception-functions"></a>例外狀況函式  
  
|功能|描述|  
|--------------|-----------------|  
|GetExceptionMetric|從登錄擷取公制值。|  
|SetExceptionMetric|設定登錄中指定的度量值。|  
|RemoveExceptionMetric|從登錄移除指定的標準。|  
|RemoveAllExceptionMetrics|從登錄移除所有的例外狀況度量。|  
  
## <a name="symbol-provider-functions"></a>符號提供者函式  
  
|功能|描述|  
|--------------|-----------------|  
|GetSPMetric|從登錄擷取公制值。|  
|SetSPMetric|設定登錄中指定的度量值。|  
|RemoveSPMetric|從登錄移除指定的標準。|  
  
## <a name="enumeration-functions"></a>列舉函式  
  
|功能|描述|  
|--------------|-----------------|  
|EnumMetricSections|列舉指定的單位類型的所有度量。|  
|EnumDebugEngine|列舉已註冊的偵錯引擎。|  
|EnumEEs|列舉已註冊的運算式評估工具。|  
|EnumExceptionMetrics|列舉所有例外狀況的度量。|  
  
## <a name="metric-definitions"></a>度量定義  
 這些定義可以用於預先定義的度量名稱。 名稱會對應至不同的登錄機碼和值名稱都是定義為寬字元字串： 例如， `extern LPCWSTR metrictypeEngine`。  
  
|預先定義的標準類型|描述： 基底金鑰...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|所有偵錯引擎度量。|  
|metrictypePortSupplier|所有連接埠供應商的度量。|  
|metrictypeException|所有例外狀況的度量。|  
|metricttypeEEExtension|所有的運算式評估工具擴充功能。|  
  
|偵錯引擎屬性|描述|  
|-----------------------------|-----------------|  
|metricAddressBP|設為非零，表示支援位址中斷點。|  
|metricAlwaysLoadLocal|設為非零，若要永遠載入偵錯引擎在本機。|  
|metricLoadInDebuggeeSession|未使用|  
|metricLoadedByDebuggee|設為非零，表示使用或程式偵錯時，一律會載入偵錯引擎。|  
|metricAttach|設為非零，表示支援以便附加到現有的程式。|  
|metricCallStackBP|設為非零，表示支援呼叫堆疊中斷點。|  
|metricConditionalBP|設為非零，表示支援之設定的條件式中斷點。|  
|metricDataBP|設為非零，表示支援的設定資料中的變更時的中斷點。|  
|metricDisassembly|設定為非零，表示支援反組譯碼清單的生產環境。|  
|metricDumpWriting|設為非零，表示傾印寫入 （傾印至輸出裝置記憶體） 的支援。|  
|metricENC|設定為非零，表示支援編輯後繼續。 **注意：**自訂偵錯引擎應該永遠不會將此設定，或應該一律將它設定為 0。|  
|metricExceptions|設為非零，表示支援的例外狀況。|  
|metricFunctionBP|設為非零，表示具名中斷點 （中斷呼叫某些函式名稱時的中斷點） 的支援。|  
|metricHitCountBP|設為非零，表示支援"hit 點"中斷點 （叫用特定次數之後，才會觸發中斷點） 的設定。|  
|metricJITDebug|設定為非零，表示支援在 just-in-time 偵錯 （偵錯工具啟動時執行的處理序中發生例外狀況）。|  
|metricMemory|未使用|  
|metricPortSupplier|設定為連接埠供應商的 CLSID 如果實作其中一個。|  
|metricRegisters|未使用|  
|metricSetNextStatement|設為非零，表示支援的設定下一個陳述式 （這會略過中繼陳述式執行）。|  
|metricSuspendThread|設為非零，表示支援暫止執行緒的執行。|  
|metricWarnIfNoSymbols|設為非零，表示沒有符號時，會通知使用者。|  
|metricProgramProvider|設定為程式提供者的 CLSID。|  
|metricAlwaysLoadProgramProviderLocal|將此設為非零，表示程式提供者應該一律會載入在本機的。|  
|metricEngineCanWatchProcess|將此設為非零，表示偵錯引擎將會監視程序事件，而程式的提供者。|  
|metricRemoteDebugging|將此設為非零，表示支援遠端偵錯。|  
|metricEncUseNativeBuilder|將此設為非零，表示編輯後繼續的管理員應該使用偵錯引擎的 encbuild.dll 來建置編輯後繼續的。 **注意：**自訂偵錯引擎應該永遠不會將此設定，或應該一律將它設定為 0。|  
|metricLoadUnderWOW64|將此設為非零，表示在 WOW 下偵錯項目處理序中應該載入的偵錯引擎，當偵錯 64 位元處理序中;否則，偵錯引擎會載入 Visual Studio 處理序 （這在 WOW64 下執行） 中。|  
|metricLoadProgramProviderUnderWOW64|將此設為非零，表示在 WOW; 下的 64 位元處理序進行偵錯時程式提供者應該會在偵錯項目處理序中載入否則，它會載入 Visual Studio 處理序中。|  
|metricStopOnExceptionCrossingManagedBoundary|將此設為非零，表示如果跨越界限的 managed/unmanaged 程式碼擲回未處理的例外狀況，應該停止處理程序。|  
|metricAutoSelectPriority|設定為自動選擇的偵錯引擎 （較高的值等於較高優先順序） 的優先權。|  
|metricAutoSelectIncompatibleList|登錄機碼包含所指定要忽略 Guid 的偵錯引擎中自動選取項目。 這些項目都是數字 （0、 1、 2，依此類推） 以 GUID 表示為字串。|  
|metricIncompatibleList|登錄機碼包含所指定的偵錯引擎與此偵錯引擎不相容的 Guid 項目。|  
|metricDisableJITOptimization|將此設為非零，表示應該在偵錯期間停用在 just-in-time （適用於 managed 程式碼） 的最佳化。|  
  
|運算式評估工具內容|描述|  
|-------------------------------------|-----------------|  
|metricEngine|這會保留偵錯引擎支援指定的運算式評估工具的數目。|  
|metricPreloadModules|將此設為非零，表示應該預先運算式評估工具對程式啟動時載入模組。|  
|metricThisObjectName|設定為"this"的物件名稱。|  
  
|運算式評估工具的擴充屬性|描述|  
|-----------------------------------------------|-----------------|  
|metricExtensionDll|支援這項擴充功能 dll 名稱。|  
|metricExtensionRegistersSupported|支援的暫存器的清單。|  
|metricExtensionRegistersEntryPoint|用於存取暫存器的進入點。|  
|metricExtensionTypesSupported|支援的類型清單。|  
|metricExtensionTypesEntryPoint|存取類型的進入點。|  
  
|連接埠供應商屬性|描述|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|（對話方塊使用者可以使用選取的連接埠，並加入要用於偵錯的連接埠） 的連接埠選取器的 CLSID。|  
|metricDisallowUserEnteredPorts|為非零，如果使用者輸入連接埠不能加入至連接埠供應商 （基本上是唯讀，這會連接埠選取器對話方塊）。|  
|metricPidBase|配置處理序識別碼時，連接埠提供者所使用的基底的處理序識別碼。|  
  
|預先定義的預存程序存放區型別|描述|  
|-------------------------------|-----------------|  
|storetypeFile|符號會儲存在個別的檔案。|  
|storetypeMetadata|符號會儲存為組件中的中繼資料。|  
  
|其他屬性|描述|  
|------------------------------|-----------------|  
|metricShowNonUserCode|將此設為非零，以顯示 nonuser 程式碼。|  
|metricJustMyCodeStepping|將此設為非零，表示只會在使用者程式碼可以發生逐步執行。|  
|metricCLSID|特定的衡量標準類型的物件的 CLSID。|  
|metricName|特定的衡量標準類型的物件的使用者易記名稱。|  
|metricLanguage|語言名稱。|  
  
## <a name="registry-locations"></a>登錄位置  
 從讀取和寫入登錄中，特別是在計量`VisualStudio`子機碼。  
  
> [!NOTE]
>  大部分的情況下，度量資訊會寫入 HKEY_LOCAL_MACHINE 機碼。 不過，有時候 HKEY_CURRENT_USER 要目的索引鍵。 Dbgmetric.lib 處理兩個索引鍵。 當取得度量資訊，它會搜尋 HKEY_CURRENT_USER 先，接著 HKEY_LOCAL_MACHINE。 當它正在設定的度量時，參數會指定要使用的最上層機碼。  
  
 *[登錄機碼]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[版本 root]*\  
  
 *[度量 root]*\  
  
 *[度量 type]*\  
  
 *[度量] = [公制值]*  
  
 *[度量] = [公制值]*  
  
 *[度量] = [公制值]*  
  
|預留位置|描述|  
|-----------------|-----------------|  
|*[登錄機碼]*|`HKEY_CURRENT_USER` 或 `HKEY_LOCAL_MACHINE`。|  
|*[版本 root]*|Visual Studio 版本 (例如， `7.0`， `7.1`，或`8.0`)。 不過，這個根目錄也可以修改使用**/rootsuffix**切換至**devenv.exe**。 VSIP，對於此修飾詞通常是**Exp**，因此版本根為，比方說，8.0Exp。|  
|*[度量 root]*|這可能是`AD7Metrics`或`AD7Metrics(Debug)`，取決於是否使用 dbgmetric.lib 的偵錯版本。 **注意：**到應遵守是否使用 dbgmetric.lib 時，此命名慣例，如果您有偵錯和發行之間的差異必須反映在登錄中的版本。|  
|*[度量 type]*|要寫入標準的類型： `Engine`， `ExpressionEvaluator`，`SymbolProvider`等等。這些所有定義如所示為 dbgmetric.h `metricTypeXXXX`，其中`XXXX`是特定型別名稱。|  
|*[度量]*|若要將度量指派值的項目名稱。 實際的組織的度量取決於指標的類型。|  
|*[指標值]*|指定度量的值。 此值應該有 （字串、 數值、 等） 的類型取決於度量。|  
  
> [!NOTE]
>  儲存所有的 Guid，格式為`{GUID}`。 例如，`{123D150B-FA18-461C-B218-45B3E4589F9B}`。  
  
### <a name="debug-engines"></a>偵錯引擎  
 以下是在登錄中的偵錯引擎度量資訊的組織。 `Engine`偵錯引擎的度量的類型名稱，且對應至*[公制 type]*上述登錄樹狀子目錄中。  
  
 `Engine`\  
  
 *[引擎 guid]*\  
  
 `CLSID` = *[類別 guid]*  
  
 *[度量] = [公制值]*  
  
 *[度量] = [公制值]*  
  
 *[度量] = [公制值]*  
  
 `PortSupplier`\  
  
 `0` = *[連接埠供應商 guid]*  
  
 `1` = *[連接埠供應商 guid]*  
  
|預留位置|描述|  
|-----------------|-----------------|  
|*[引擎 guid]*|偵錯引擎的 GUID。|  
|*[類別 guid]*|類別可實作此偵錯引擎的 GUID。|  
|*[連接埠供應商 guid]*|如果有的話，連接埠供應商的 GUID。 許多偵錯引擎會使用預設連接埠供應商，並因此不會指定自己的供應商。 在此情況下，子機碼`PortSupplier`將不會。|  
  
### <a name="port-suppliers"></a>連接埠供應商  
 以下是在登錄中的連接埠供應商度量資訊的組織。 `PortSupplier`是一個連接埠的供應商的度量的類型名稱，而對應*[公制 type]*。  
  
 `PortSupplier`\  
  
 *[連接埠供應商 guid]*\  
  
 `CLSID` = *[類別 guid]*  
  
 *[度量] = [公制值]*  
  
 *[度量] = [公制值]*  
  
|預留位置|描述|  
|-----------------|-----------------|  
|*[連接埠供應商 guid]*|連接埠供應商的 GUID|  
|*[類別 guid]*|實作此連接埠供應商類別 GUID|  
  
### <a name="symbol-providers"></a>符號提供者  
 以下是在登錄中的符號供應商度量資訊的組織。 `SymbolProvider`是的符號提供者的度量的類型名稱，而對應*[公制 type]*。  
  
 `SymbolProvider`\  
  
 *[符號提供者 guid]*\  
  
 `file`\  
  
 `CLSID` = *[類別 guid]*  
  
 *[度量] = [公制值]*  
  
 *[度量] = [公制值]*  
  
 `metadata`\  
  
 `CLSID` = *[類別 guid]*  
  
 *[度量] = [公制值]*  
  
 *[度量] = [公制值]*  
  
|預留位置|描述|  
|-----------------|-----------------|  
|*[符號提供者 guid]*|符號提供者 GUID|  
|*[類別 guid]*|類別會實作這個符號提供者的 GUID|  
  
### <a name="expression-evaluators"></a>運算式評估工具  
 以下是在登錄中的運算式評估工具度量資訊的組織。 `ExpressionEvaluator`運算式評估工具的度量的類型名稱，且對應至*[公制 type]*。  
  
> [!NOTE]
>  指標類型`ExpressionEvaluator`中未定義 dbgmetric.h，因為它會假設運算式評估工具的所有度量的變更將會移到適當的運算式評估工具度量函式 (的版面配置`ExpressionEvaluator`子機碼有點複雜，因此詳細資料會隱藏 dbgmetric.lib 內）。  
  
 `ExpressionEvaluator`\  
  
 *[語言 guid]*\  
  
 *[廠商 guid]*\  
  
 `CLSID` = *[類別 guid]*  
  
 *[度量] = [公制值]*  
  
 *[度量] = [公制值]*  
  
 `Engine`\  
  
 `0` = *[偵錯引擎 guid]*  
  
 `1` = *[偵錯引擎 guid]*  
  
|預留位置|描述|  
|-----------------|-----------------|  
|*[語言 guid]*|一種語言的 GUID|  
|*[廠商 guid]*|供應商的 GUID|  
|*[類別 guid]*|類別會實作這個運算式評估工具的 GUID|  
|*[偵錯引擎 guid]*|這個運算式評估工具的運作方式與偵錯引擎的 GUID|  
  
### <a name="expression-evaluator-extensions"></a>運算式評估工具擴充功能  
 以下是標準的運算式評估工具擴充功能中登錄的組織。 `EEExtensions`是度量的型別名稱的運算式評估工具擴充功能，而對應*[公制 type]*。  
  
 `EEExtensions`\  
  
 *[延伸模組 guid]*\  
  
 *[度量] = [公制值]*  
  
 *[度量] = [公制值]*  
  
|預留位置|描述|  
|-----------------|-----------------|  
|*[延伸模組 guid]*|運算式評估工具延伸模組的 GUID|  
  
### <a name="exceptions"></a>例外狀況  
 以下是在登錄中的例外狀況度量資訊的組織。 `Exception`例外狀況的度量的類型名稱，且對應至*[公制 type]*。  
  
 `Exception`\  
  
 *[偵錯引擎 guid]*\  
  
 *[例外狀況型別]*\  
  
 *[例外狀況]*\  
  
 *[度量] = [公制值]*  
  
 *[度量] = [公制值]*  
  
 *[例外狀況]*\  
  
 *[度量] = [公制值]*  
  
 *[度量] = [公制值]*  
  
|預留位置|描述|  
|-----------------|-----------------|  
|*[偵錯引擎 guid]*|偵錯引擎，可支援例外狀況的 GUID。|  
|*[例外狀況型別]*|識別可處理的例外狀況類別的子機碼一般的標題。 一般名稱是**c + + 例外狀況**， **Win32 例外狀況**， **Common Language Runtime 例外**，和**原生執行階段會檢查**。 這些名稱也可用來識別特定類別的例外狀況給使用者。|  
|*[例外狀況]*|例外狀況的名稱： 例如， **_com_error**或**Control-break**。 這些名稱也可用來識別使用者特定的例外狀況。|  
  
## <a name="requirements"></a>需求  
 這些檔案位於[!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)]SDK 安裝目錄 (根據預設， *[磁碟機]*\Program Files\Microsoft Visual Studio 2010 的 SDK\\)。  
  
 標頭： includes\dbgmetric.h  
  
 程式庫： libs\ad2de.lib、 libs\dbgmetric.lib  
  
## <a name="see-also"></a>請參閱  
 [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)