---
title: "SDK 協助程式進行偵錯 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "dbgmetric.lib"
  - "登錄中，偵錯 sdk 》"
  - "偵錯 SDK，登錄位置"
  - "dbgmetric.h"
  - "度量 [偵錯 SDK]"
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# SDK 協助程式進行偵錯
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這些函式和宣告都是通用的 helper 函式，來實作 \[c \+ \+ 中的 \[偵錯引擎、 運算式評估工具和符號的提供者。  
  
> [!NOTE]
>  此時有不受管理的版本，這些函式和宣告。  
  
## 概觀  
 為了讓偵錯引擎、 運算式評估工具和符號的提供者所 Visual Studio 的使用，它們必須先註冊。  這是藉由設定登錄子機碼和項目，或稱為 「 設定度量資訊 」。 下列的全域函式的設計，被為了簡化更新這些測量標準程序。  在登錄位置，以找出每一個登錄子機碼所更新這些函式的版面配置，請參閱\] 區段。  
  
## 一般公制函式  
 這些是偵錯引擎所使用的一般功能。  運算式評估工具來進行特製化函式，並稍後會詳細說明符號提供者。  
  
### GetMetric 方法  
 從登錄中擷取一個公制值。  
  
```cpp#  
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
|--------|--------|  
|pszMachine|\[in\]將寫入的暫存器的可能是遠端機器名稱 \(`NULL`表示本機電腦\)。|  
|pszType|\[in\]一種單位類型。|  
|guidSection|\[in\]特定的引擎、 評估工具、 例外等等的 GUID。  這會指定特定項目的的單位類型\] 下的子區段。|  
|pszMetric|\[in\]取得度量資訊。  這會對應到特定值的名稱。|  
|pdwValue|\[in\]度量的值之儲存位置。  有多種類別的 DWORD \(如下例所示\)、 BSTR、 GUID 或一系列的 Guid 可以傳回的 GetMetric。|  
|pszAltRoot|\[in\]若要使用替代的登錄根目錄。  設定成`NULL`若要使用預設值。|  
  
### SetMetric 方法  
 設定登錄中指定的單位值。  
  
```cpp#  
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
|--------|--------|  
|pszType|\[in\]一種單位類型。|  
|guidSection|\[in\]特定的引擎、 評估工具、 例外等等的 GUID。  這會指定特定項目的的單位類型\] 下的子區段。|  
|pszMetric|\[in\]取得度量資訊。  這會對應到特定值的名稱。|  
|dwValue|\[in\]儲存位置的計量值中的值。  有多種類別的 DWORD \(在本例中\)、 BSTR、 GUID 或 Guid 的陣列可儲存的 SetMetric。|  
|fUserSpecific|\[in\]如果度量是特定的使用者，而且應該寫入使用者的 hive，而不是本機電腦 hive 的則為 TRUE。|  
|pszAltRoot|\[in\]若要使用替代的登錄根目錄。  設定成`NULL`若要使用預設值。|  
  
### RemoveMetric 方法  
 從登錄中移除指定的度量資訊。  
  
```cpp#  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|參數|描述|  
|--------|--------|  
|pszType|\[in\]一種單位類型。|  
|guidSection|\[in\]特定的引擎、 評估工具、 例外等等的 GUID。  這會指定特定項目的的單位類型\] 下的子區段。|  
|pszMetric|\[in\]要移除計量值。  這會對應到特定值的名稱。|  
|pszAltRoot|\[in\]若要使用替代的登錄根目錄。  設定成`NULL`若要使用預設值。|  
  
### EnumMetricSections 方法  
 列舉的公制的各章節，在登錄中。  
  
```cpp#  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|參數|描述|  
|--------|--------|  
|pszMachine|\[in\]將寫入的暫存器的可能是遠端機器名稱 \(`NULL`表示本機電腦\)。|  
|pszType|\[in\]一種單位類型。|  
|rgguidSections|輸入 \[、 輸出\]預先配置的 Guid，以填入的陣列。|  
|pdwSize|\[in\]可以儲存在中的 Guid 的最大數目`rgguidSections`陣列。|  
|pszAltRoot|\[in\]若要使用替代的登錄根目錄。  設定成`NULL`若要使用預設值。|  
  
## 運算式評估工具功能  
  
|Function|描述|  
|--------------|--------|  
|GetEEMetric|從登錄中擷取一個公制值。|  
|SetEEMetric|設定登錄中指定的單位值。|  
|RemoveEEMetric|從登錄中移除指定的度量資訊。|  
|GetEEMetricFile|取得檔案名稱，從指定的度量資訊，並載入，以字串形式傳回檔案內容。|  
  
## 例外狀況的函式  
  
|Function|描述|  
|--------------|--------|  
|GetExceptionMetric|從登錄中擷取一個公制值。|  
|SetExceptionMetric|設定登錄中指定的單位值。|  
|RemoveExceptionMetric|從登錄中移除指定的度量資訊。|  
|RemoveAllExceptionMetrics|從登錄中移除所有的例外狀況度量資訊。|  
  
## 符號提供者函式  
  
|Function|描述|  
|--------------|--------|  
|GetSPMetric|從登錄中擷取一個公制值。|  
|SetSPMetric|設定登錄中指定的單位值。|  
|RemoveSPMetric|從登錄中移除指定的度量資訊。|  
  
## 列舉型別函式  
  
|Function|描述|  
|--------------|--------|  
|EnumMetricSections|列舉指定的單位類型的所有度量資訊。|  
|EnumDebugEngine|列舉已註冊的偵錯引擎。|  
|EnumEEs|列舉已註冊的運算式評估工具。|  
|EnumExceptionMetrics|列舉所有的例外狀況度量資訊。|  
  
## 公制定義  
 這些定義可用的預先定義的單位名稱。  名稱對應到不同的登錄機碼和值的名稱都定義為寬字元字串： 例如， `extern LPCWSTR metrictypeEngine`。  
  
|預先定義的單位類型|描述: 主要機碼。...|  
|---------------|------------------|  
|metrictypeEngine|所有偵錯引擎度量資訊。|  
|metrictypePortSupplier|所有連接埠的供應商度量資訊。|  
|metrictypeException|所有例外狀況的度量資訊。|  
|metricttypeEEExtension|所有的運算式評估工具擴充功能。|  
  
|偵錯引擎屬性|描述|  
|------------|--------|  
|metricAddressBP|設定為非零值以指示支援位址中斷點。|  
|metricAlwaysLoadLocal|設定為非零值，除了永遠載入偵錯引擎在本機上。|  
|metricLoadInDebuggeeSession|保留至以後使用|  
|metricLoadedByDebuggee|設定為非零值以表示使用或正在偵錯的程式，一定會載入偵錯引擎。|  
|metricAttach|設定為零指示以便附加到現有的程式的支援。|  
|metricCallStackBP|設定為非零值，表示呼叫堆疊中斷點的支援。|  
|metricConditionalBP|設定為非零值以指示支援條件式中斷點的設定值。|  
|metricDataBP|設定為非零值以指示支援的資料變更的中斷點設定。|  
|metricDisassembly|設定為非零值，指出反組譯碼清單的生產環境的支援。|  
|metricDumpWriting|設定為零指示傾印寫入 \(傾的輸出裝置的記憶體\) 的支援。|  
|metricENC|設定為非零值，指出支援編輯後繼續\]。 **Note:**  自訂的偵錯引擎應該永遠不會設定這個值，或應該一律設為 0。|  
|metricExceptions|設定為非零值以指出例外狀況的支援。|  
|metricFunctionBP|設定為非零值以指示為具名中斷點 \(中斷呼叫特定函式名稱時的中斷點\) 的支援。|  
|metricHitCountBP|設定為非零值來指示 「 點擊點"中斷點 \(只有在被叫用特定次數後，便會觸發中斷點\) 設定的支援。|  
|metricJITDebug|設定為非零值以指示只要精準偵錯 \(正在執行的程序中發生例外狀況時，就會啟動偵錯工具\) 的支援。|  
|metricMemory|保留至以後使用|  
|metricPortSupplier|如果其中一個實作後，請將此設定為連接埠提供者的 CLSID。|  
|metricRegisters|保留至以後使用|  
|metricSetNextStatement|設定為零指示設定下一個陳述式 \(這會略過執行中繼的陳述式\) 的支援。|  
|metricSuspendThread|設定為零指示暫止執行緒執行的支援。|  
|metricWarnIfNoSymbols|設定為零表示沒有符號時，會通知使用者。|  
|metricProgramProvider|設定為程式提供者的 CLSID。|  
|metricAlwaysLoadProgramProviderLocal|將此設為非零值，表示該程式提供者應永遠排在載入本機的。|  
|metricEngineCanWatchProcess|設定為非零值，指出偵錯引擎會等待處理程序事件，而不程式提供者。|  
|metricRemoteDebugging|設定為非零值，指出遠端偵錯支援。|  
|metricEncUseNativeBuilder|將此設為非零值，指出編輯後繼續的管理員應該使用偵錯引擎的 encbuild.dll 來編輯後繼續建置的。 **Note:**  自訂的偵錯引擎應該永遠不會設定這個值，或應該一律設為 0。|  
|metricLoadUnderWOW64|將它設定為非零值以表示在 WOW 下偵錯項目程序中應該載入偵錯引擎，當偵錯 64 位元的處理程序。 否則，偵錯引擎會載入 Visual Studio 的程序 \(這在 WOW64 下執行\)。|  
|metricLoadProgramProviderUnderWOW64|將它設定為非零值，指出偵錯 64 位元處理程序在 WOW ； 下時，程式提供者應該在偵錯項處理程序中載入 否則，將它們載入 Visual Studio 的程序中。|  
|metricStopOnExceptionCrossingManagedBoundary|設定為非零值，指出如果跨越的界限管理\/不受管理的程式碼擲回未處理的例外狀況，應該停止處理程序。|  
|metricAutoSelectPriority|將此設為自動選擇偵錯引擎 \(較高值等於較高優先順序\) 的優先順序。|  
|metricAutoSelectIncompatibleList|登錄機碼含有指定 Guid 的偵錯引擎，以略過自動選取範圍中的項目。  這些項目是一個數字 \(0、 1、 2，依此類推\) 以表示為字串的 GUID。|  
|metricIncompatibleList|登錄機碼包含與這個偵錯引擎不相容的偵錯引擎指定 Guid 的項目。|  
|metricDisableJITOptimization|設定為非零值表示應該停用偵錯期間只精準最佳化 \(適用於 managed 程式碼\)。|  
  
|運算式評估工具內容|描述|  
|---------------|--------|  
|metricEngine|這會保留偵錯引擎數的支援指定的運算式評估工具。|  
|metricPreloadModules|設定為非零值表示的運算式評估工具對程式啟動時，預先載入的模組。|  
|metricThisObjectName|設定為"this"的物件名稱。|  
  
|運算式評估工具的擴充屬性|描述|  
|------------------|--------|  
|metricExtensionDll|支援此副檔名的 dll 名稱。|  
|metricExtensionRegistersSupported|支援的暫存器的清單。|  
|metricExtensionRegistersEntryPoint|用來存取暫存器的進入點。|  
|metricExtensionTypesSupported|支援的類型清單。|  
|metricExtensionTypesEntryPoint|進入點，用於存取型別。|  
  
|連接埠的供應商內容|描述|  
|---------------|--------|  
|metricPortPickerCLSID|\(對話方塊，使用者可以使用選取的連接埠，並將用來偵錯的連接埠\) 的連接埠選擇器的 CLSID。|  
|metricDisallowUserEnteredPorts|非零值，如果使用者輸入的連接埠不能加入連接埠提供者 \(本質上是唯讀，這使得連接埠選擇器對話方塊\)。|  
|metricPidBase|配置處理序 Id 時使用的連接埠提供者的基底的處理序 ID。|  
  
|預先定義的預存程序存放區類型|描述|  
|--------------------|--------|  
|storetypeFile|這些符號會儲存在不同的檔案。|  
|storetypeMetadata|這些符號會儲存為組件中的中繼資料。|  
  
|其他的屬性|描述|  
|-----------|--------|  
|metricShowNonUserCode|設定為非零值，以顯示 nonuser 的程式碼。|  
|metricJustMyCodeStepping|設定為非零值來表示逐步執行可以只能出現在使用者程式碼。|  
|metricCLSID|特定的公制型別的物件的 CLSID。|  
|metricName|特定的公制型別的物件的使用者易記名稱。|  
|metricLanguage|語言名稱。|  
  
## 登錄位置  
 度量資訊會讀取和寫入至登錄中，特別是在`VisualStudio`子機碼。  
  
> [!NOTE]
>  大多數情況下，度量資訊會寫入的作用中計時間索引鍵。  不過，有時候 HKEY\_CURRENT\_USER 會目的索引鍵。  Dbgmetric.lib 會處理這兩個機碼。  當取得度量資訊，它會搜尋 HKEY\_CURRENT\_USER： 首先，那麼作用中計時間。  當它正在設定度量單位時，參數會指定要使用哪一個最上層機碼。  
  
 *\[登錄機碼\]*\\  
  
 `Software`\\  
  
 `Microsoft`\\  
  
 `VisualStudio`\\  
  
 *\[版本 root\]*\\  
  
 *\[公制 root\]*\\  
  
 *\[公制類型\]*\\  
  
 *\[公制\] \= \[公制值\]*  
  
 *\[公制\] \= \[公制值\]*  
  
 *\[公制\] \= \[公制值\]*  
  
|預留位置|描述|  
|----------|--------|  
|*\[登錄鍵\]*|`HKEY_CURRENT_USER` 或 `HKEY_LOCAL_MACHINE`。|  
|*\[版本 root\]*|Visual Studio 的版本 \(例如， `7.0`， `7.1`，或`8.0`\)。  不過，這個根目錄也可以修改使用 **\/rootsuffix**切換到**devenv.exe**。  VSIP，如這個修飾詞通常是到期，因此版本根目錄，例如，8.0Exp。|  
|*\[公制 root\]*|這可能是`AD7Metrics`或`AD7Metrics(Debug)`，視是否使用 dbgmetric.lib 的偵錯版本。 **Note:**  是否使用 dbgmetric.lib 時，此命名慣例應遵守偵錯和發行版本之間的差異，才必須反映在登錄中的版本。|  
|*\[公制類型\]*|量測可寫入的型別： `Engine`， `ExpressionEvaluator`， `SymbolProvider`等。  這些都定義為在 dbgmetric.h 與`metricTypeXXXX`，其中`XXXX`是特定型別名稱。|  
|*\[公制\]*|若要設定度量指派值的項目名稱。  計量的實際的組織單位的型別而定。|  
|*\[公制值\]*|硌巖緻公制值。  值應該有 \(字串，數字，等\) 的型別而定計量值。|  
  
> [!NOTE]
>  所有的 Guid 格式儲存在的`{GUID}`。  例如 `{123D150B-FA18-461C-B218-45B3E4589F9B}`。  
  
### 偵錯引擎  
 以下是在登錄中的偵錯引擎度量資訊的組織。  `Engine`偵錯引擎的公制的型別名稱，而對應的 *\[公制類型\]* 在上述的登錄樹狀子目錄中。  
  
 `Engine`\\  
  
 *\[發動機 guid\]*\\  
  
 `CLSID`\=  *\[類別 guid\]*  
  
 *\[公制\] \= \[公制值\]*  
  
 *\[公制\] \= \[公制值\]*  
  
 *\[公制\] \= \[公制值\]*  
  
 `PortSupplier`\\  
  
 `0`\=  *\[連接埠的供應商 guid\]*  
  
 `1`\=  *\[連接埠的供應商 guid\]*  
  
|預留位置|描述|  
|----------|--------|  
|*\[引擎 guid\]*|偵錯引擎的 GUID。|  
|*\[類別 guid\]*|實作這個偵錯引擎的類別的 GUID。|  
|*\[連接埠的供應商 guid\]*|如果有任何連接埠提供者的 GUID。  許多偵錯引擎會使用預設連接埠提供者，並因此未指定他們自己的供應商。  在此情況下，子機碼`PortSupplier`將會不存在。|  
  
### 連接埠的供應商  
 以下是在登錄中的連接埠的供應商度量資訊的組織。  `PortSupplier`連接埠提供者的公制的型別名稱，而對應的 *\[公制類型\]*。  
  
 `PortSupplier`\\  
  
 *\[連接埠的供應商 guid\]*\\  
  
 `CLSID`\=  *\[類別 guid\]*  
  
 *\[公制\] \= \[公制值\]*  
  
 *\[公制\] \= \[公制值\]*  
  
|預留位置|描述|  
|----------|--------|  
|*\[連接埠的供應商 guid\]*|連接埠提供者的 GUID 來|  
|*\[類別 guid\]*|實作這個連接埠提供者類別的 GUID|  
  
### 符號提供者  
 以下是在登錄中的符號供應商度量資訊的組織。  `SymbolProvider`符號提供者的公制的型別名稱，而對應的 *\[公制類型\]*。  
  
 `SymbolProvider`\\  
  
 *\[提供者的 guid 的符號\]*\\  
  
 `file`\\  
  
 `CLSID`\=  *\[類別 guid\]*  
  
 *\[公制\] \= \[公制值\]*  
  
 *\[公制\] \= \[公制值\]*  
  
 `metadata`\\  
  
 `CLSID`\=  *\[類別 guid\]*  
  
 *\[公制\] \= \[公制值\]*  
  
 *\[公制\] \= \[公制值\]*  
  
|預留位置|描述|  
|----------|--------|  
|*\[提供者的 guid 的符號\]*|符號提供者的 GUID|  
|*\[類別 guid\]*|實作此符號的提供者類別的 GUID|  
  
### 運算式評估工具  
 以下是在登錄中的運算式評估工具度量資訊的組織。  `ExpressionEvaluator`運算式評估工具的公制的型別名稱，而對應的 *\[公制類型\]*。  
  
> [!NOTE]
>  公制的型別，如`ExpressionEvaluator`不定義在 dbgmetric.h，因為它會假設所有的運算式評估工具計量的變更都會經過適當的運算式評估工具公制函式 \(版面配置的`ExpressionEvaluator`子機碼是有點複雜，因此詳細資料會隱藏在 dbgmetric.lib 內\)。  
  
 `ExpressionEvaluator`\\  
  
 *\[語言 guid\]*\\  
  
 *\[供應商 guid\]*\\  
  
 `CLSID`\=  *\[類別 guid\]*  
  
 *\[公制\] \= \[公制值\]*  
  
 *\[公制\] \= \[公制值\]*  
  
 `Engine`\\  
  
 `0`\=  *\[偵錯引擎 guid\]*  
  
 `1`\=  *\[偵錯引擎 guid\]*  
  
|預留位置|描述|  
|----------|--------|  
|*\[語言 guid\]*|一種語言的 GUID 來|  
|*\[供應商 guid\]*|廠商的 GUID 來|  
|*\[類別 guid\]*|實作這個運算式評估工具類別的 GUID|  
|*\[偵錯引擎 guid\]*|此運算式評估工具所使用的偵錯引擎的 GUID 來|  
  
### 運算式評估工具擴充功能  
 以下是在登錄中的運算式評估工具擴充功能度量資訊的組織。  `EEExtensions`是公制的型別名稱的運算式評估工具擴充功能，而對應的 *\[公制類型\]*。  
  
 `EEExtensions`\\  
  
 *\[延伸 guid\]*\\  
  
 *\[公制\] \= \[公制值\]*  
  
 *\[公制\] \= \[公制值\]*  
  
|預留位置|描述|  
|----------|--------|  
|*\[延伸 guid\]*|運算式評估工具擴充功能的 GUID|  
  
### 例外狀況  
 以下是在登錄中的例外狀況度量資訊的組織。  `Exception`例外狀況的公制的型別名稱，而對應的 *\[公制類型\]*。  
  
 `Exception`\\  
  
 *\[偵錯引擎 guid\]*\\  
  
 *\[例外狀況型別\]*\\  
  
 *\[例外\]*\\  
  
 *\[公制\] \= \[公制值\]*  
  
 *\[公制\] \= \[公制值\]*  
  
 *\[例外\]*\\  
  
 *\[公制\] \= \[公制值\]*  
  
 *\[公制\] \= \[公制值\]*  
  
|預留位置|描述|  
|----------|--------|  
|*\[偵錯引擎 guid\]*|支援例外狀況的偵錯引擎的 GUID。|  
|*\[例外狀況型別\]*|用來識別可處理的例外狀況的類別之子機碼的一般標題。  Typical names are **C\+\+ Exceptions**, **Win32 Exceptions**, **Common Language Runtime Exceptions**, and **Native Run\-Time Checks**.  這些名稱也用來識別使用者的例外狀況的特定類別中。|  
|*\[例外\]*|例外狀況的名稱： 例如， **\_com\_error**或**Control\-Break**。  這些名稱也用來識別特定的例外狀況，向使用者中。|  
  
## 需求  
 這些檔案都位於[!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK 的安裝目錄 \(預設情況下，  *\[磁碟機\]*\\Program Files\\Microsoft Visual Studio 2010 SDK\\\)。  
  
 標頭: includes\\dbgmetric.h  
  
 圖書館: libs\\ad2de.lib、 libs\\dbgmetric.lib  
  
## 請參閱  
 [應用程式開發介面參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)