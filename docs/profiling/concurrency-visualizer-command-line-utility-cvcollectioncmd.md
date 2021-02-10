---
title: 平行存取視覺化命令列公用程式
description: 使用命令列公用程式 CVCollectionCmd.exe 來收集可在平行存取視覺化程式中查看的追蹤。 您不需要安裝 Visual Studio。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.cvcollectioncmd
ms.assetid: 476601be-1608-4014-af15-5aba6ccbed1c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 47da8ae405dc24cad5bab4c98384ad5db5a97ef2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941173"
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>並行視覺化檢視命令列公用程式 (CVCollectionCmd)
您可以使用並行視覺化檢視命令列公用程式 (*CVCollectionCmd.exe*) 從命令列收集追蹤，以便在 Visual Studio 的並行視覺化檢視中進行檢視。 此工具可在未安裝 Visual Studio 的電腦上使用。

> [!NOTE]
> 從 Visual Studio 2013 開始，並行視覺化檢視是選擇性擴充功能。  (先前已包含在 Visual Studio 中。 ) 您可以從下載中心下載 [適用于 Visual Studio 2015 的並行視覺化檢視集合工具](https://www.microsoft.com/download/details.aspx?id=49103) 。

## <a name="download-the-concurrency-visualizer-command-line-utility"></a>下載並行視覺化檢視命令列公用程式
 若要下載及安裝此命令列公用程式，請移至 Microsoft 下載中心網站上的 [Visual Studio 2015 的並行視覺化檢視收集工具](https://www.microsoft.com/download/details.aspx?id=49103) ，並遵循指示進行。 根據預設， *CVCollectionCmd.exe* 安裝在 x64 電腦上的%ProgramFiles%\Microsoft 並行視覺化收集工具 \ (% ProgramFiles (x86) % \ Microsoft 並行視覺效果集合工具 \) 。

## <a name="collect-a-trace-with-cvcollectioncmd"></a>使用 CVCollectionCmd 收集追蹤
 您可以使用 CVCollectionCmd 啟動應用程式，或將 CVCollectionCmd 附加至應用程式，來收集追蹤。 請參閱下列與選項相關的命令參考。 例如：

```cmd
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data
```

## <a name="commands-and-parameters"></a>命令和參數
 若要取得命令列公用程式中命令和參數的說明，請在命令提示字元中輸入下列命令：

 **CvCollectionCmd /?**

|選項|描述|參數|傳回值|
|------------|-----------------|----------------|-------------------|
|查詢|傳回是否可以開始收集。|無|0，表示準備開始收集。<br /><br /> 1，表示收集已在進行中。<br /><br /> 2，表示收集不在進行中，但已啟用一或多個所需的 [ETW](/dotnet/framework/wcf/samples/etw-tracing) 工作階段。|
|啟動|在並行視覺化檢視下執行指定的處理序。|可執行檔的路徑。|0，表示執行成功。<br /><br /> 1，表示執行失敗，因為無法啟動目標應用程式。<br /><br /> 13，表示執行失敗，因為 CVCollectionCmd 沒有足夠的權限可寫入指定的輸出目錄。|
|Attach|開始收集系統範圍追蹤；如果指定處理序，則附加至該處理序。|無。|0，表示附加成功。<br /><br /> 1，表示附加失敗，因為指定的處理序無效或模稜兩可。<br /><br /> 13，表示附加失敗，因為 CVCollectionCmd 沒有足夠的權限可寫入指定的輸出目錄。|
|中斷連結|停止收集。|無。|0，表示中斷連結成功。<br /><br /> 1，表示中斷連結失敗，因為目前正在收集。<br /><br /> 2，表示中斷連結失敗，因為無法停止收集。|
|分析|分析指定的追蹤。|CVTrace 檔案的完整路徑。|0，表示分析成功。<br /><br /> 1，表示無法開始分析，因為指定的追蹤是系統範圍追蹤，但未指定目標處理序。<br /><br /> 2，表示無法開始分析，因為追蹤不是系統範圍追蹤，但已指定處理序。<br /><br /> 3，表示分析失敗，因為指定的處理序無效。<br /><br /> 4，表示分析失敗，因為指定的 CVTrace 檔案無效。|
|LaunchArgs|指定目標可執行檔引數。 這個選項僅適用於 Launch 命令。|傳遞給應用程式的命令列引數。|無。|
|Outdir|指定要在其中儲存追蹤檔案的目錄。 適用於 Launch 和 Attach 命令。|目錄路徑或相對路徑。|無。|
|處理序|指定執行 Attach 命令時要附加的處理序，或執行 Analyze 命令時要在追蹤中分析的處理序。 適用於 Attach 和 Analyze 命令。|處理序的 PID 或名稱。|無。|
|Config|指定組態檔的路徑 (如果需要預設值以外的收集設定)。   適用於 Launch、Attach 和 Analyze 命令。|XML 組態檔的目錄路徑或相對路徑。|無。|

## <a name="customize-configuration-settings"></a>自訂組態設定
 如果您使用 CVCollectionCmd 收集追蹤並想自訂收集設定，請使用組態檔指定這些設定。

> [!NOTE]
> 當您使用 Visual Studio 收集追蹤時，不要直接修改組態檔。  請改用 [[進階設定]](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 對話方塊來修改設定。

 若要修改收集設定，請在您要執行 CVCollectionCmd 公用程式的電腦上建立組態檔。 您可以從頭開始建立組態檔，也可以從已安裝 Visual Studio 的電腦上複製組態檔，再進行修改。 檔案名稱為 *UserConfig.xml*，並位在 *Local AppData* 資料夾中。 當您執行公用程式時，請搭配 Launch、Attach 或 Analyze 命令使用 Config 選項。  在與 Config 選項相關聯的參數中，指定組態檔的路徑。

### <a name="configuration-file-tags"></a>組態檔標記
 組態檔採用 XML 格式。 以下是有效的標記和值：

| 標籤 | 描述 | 值 |
|-------------------------| - | - |
| Config | 標示整個組態檔。 | 必須包含下列項目：<br /><br /> -   MinorVersion<br />-   MajorVersion |
| MajorVersion | 指定組態檔的主要版本。 | [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 專案必須是 1。 如果不是 1，公用程式將無法運作。 |
| MinorVersion | 指定組態檔的次要版本。 | [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 專案必須是 0。 如果不是 0，公用程式將無法運作。 |
| IncludeEnvSymbolPath | 設定值，決定是否使用環境符號路徑 (_NT_SYMBOL_PATH)。 | -   True<br />-   False |
| DeleteEtlsAfterAnalysis | 設定值，決定是否在分析完成時刪除 ETL 檔案。 | -   True<br />-   False |
| DeleteEtlsAfterAnalysis | 指定符號伺服器的路徑。 如需詳細資訊，請參閱 [使用 Microsoft 符號伺服器取得偵錯符號檔](/windows/win32/dxtecharts/debugging-with-symbols)。 | 目錄名稱或 URL。 |
| 標記 | 包含標記提供者的清單。 | 可包含零個或多個 MarkerProvider 項目。 |
| MarkerProvider | 指定單一標記提供者。 | 必須包含下列項目：<br /><br /> -   Level<br />-   GUID<br />-   Name<br /><br /> 可包含下列項目：<br /><br /> -   Categories<br />-   IsEnabled |
| 層級 | 設定 MarkerProvider 的重要性層級。 | -   Low<br />-   Normal<br />-   High<br />-   Critical<br />-   Everything |
| Guid | ETW 標記提供者的全域唯一識別項。 | GUID。 |
| 名稱 | 指定標記提供者的描述。 | 字串。 |
| 類別 | 指定標記提供者所收集的分類。 | 以逗號分隔字串表示多個數字或多個範圍的數字。 |
| IsEnabled | 設定值，決定是否啟用標記提供者進行收集。 | -   True<br />-   False |
| FilterConfig | 指定從收集篩選之 ETW 事件的組態選項清單。 | 可包含下列項目：<br /><br /> -   CollectClrEvents<br />-   ClrCollectionOptions<br />-   CollectSampleEvents<br />-   CollectGpuEvents<br />-   CollectFileIO |
| CollectClrEvents | 設定值，決定是否收集 CLR 事件。 | -   True<br />-   False |
| ClrCollectionOptions | 指定是否收集原生應用程式的 CLR 事件，以及是否收集 NGEN 取消事件。 | 可包含下列一個或兩個值，或者不包含任何值：<br /><br /> -   CollectForNative<br />-   DisableNGenRundown |
| CollectSampleEvents | 設定值，決定是否收集取樣事件。 | -   True<br />-   False |
| CollectGpuEvents | 設定值，決定是否收集 DX 產生的事件。 | -   True<br />-   False |
| CollectFileIO | 設定值，決定是否收集檔案 I/O 事件。 | -   True<br />-   False |
| UserBufferSettings | 指定使用者緩衝區設定參數的清單。 | 必須包含下列項目：<br /><br /> -   BufferFlushTimer<br />-   BufferSize<br />-   MinimumBuffers<br />-   MaximumBuffers |
| KernelBufferSettings | 指定核心緩衝區設定參數的清單。 | 必須包含下列項目：<br /><br /> -   BufferFlushTimer<br />-   BufferSize<br />-   MinimumBuffers<br />-   MaximumBuffers |
| BufferFlushTimer | 指定 ETW 緩衝區的清除計時器。 | 正整數。 |
| BufferSize | 配置給每個事件追蹤工作階段緩衝區的記憶體數量 (以 KB 為單位)。 | 0 至 1024 之間的數字。 |
| MinimumBuffers | 配置給事件追蹤工作階段之緩衝集區的緩衝區數目下限。 | 大於或等於邏輯核心數目兩倍的正整數。 |
| MaximumBuffers | 配置給事件追蹤工作階段之緩衝集區的緩衝區數目上限。 | 大於或等於 MinimumBuffers 的數字。 |
| JustMyCode | 指定 Just My Code 目錄的清單。 | 零個或多個 MyCodeDirectory 項目的清單。 |
| MyCodeDirectory | 指定包含程式碼的目錄。 | 絕對路徑。 |

### <a name="example"></a>範例
 您可以複製下列範例，然後依照您的需求進行修改，而不用從頭開始建立組態檔。

```xml
<?xml version="1.0"?>
<LocalConfig xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" MajorVersion="1" MinorVersion="0">

  <IncludeEnvSymbolPath>true</IncludeEnvSymbolPath>

  <DeleteEtlsAfterAnalysis>true</DeleteEtlsAfterAnalysis>

  <TraceLocation>C:\traces</TraceLocation>

  <SymbolPath>http://symweb</SymbolPath>

  <Markers>
    <MarkerProvider Name="Default" Guid="8d4925ab-505a-483b-a7e0-6f824a07a6f0" Level="Low" />
    <MarkerProvider Name="TPL" Guid="2e5dba47-a3d2-4d16-8ee0-6671ffdcd7b5" Level="Normal" />
    <MarkerProvider Name="TPL Dataflow" Guid="16f53577-e41d-43d4-b47e-c17025bf4025" Level="Normal" />
    <MarkerProvider Name="TPL Synchronization" Guid="ec631d38-466b-4290-9306-834971ba0217" Level="Normal" />
    <MarkerProvider Name="PLINQ" Guid="159eeeec-4a14-4418-a8fe-faabcd987887" Level="Normal" />
    <MarkerProvider Name="Concurrency Runtime" Guid="f7b697a3-4db5-4d3b-be71-c4d284e6592f" Level="Normal" />
    <MarkerProvider Name="Scenario Markers" Guid="fb9244c9-f23a-4966-8a9c-97a51f8c355b" Level="Low" />

    <!-- The IsEnabled and Categories elements are optional -->
    <MarkerProvider Name="myMarker1" Guid="d0dbb3a3-895c-4ce6-96d9-28f69d664dc3" Level="Critical" IsEnabled="false" Categories="0,1,3-5,8" />
    <MarkerProvider Name="myMarker2" Guid="03452127-a617-4302-9e30-c0d10442e4ee" Level="Low" IsEnabled="false" Categories="0,1,3-5,8-10,11-13" />
  </Markers>

  <FilterConfig>
    <CollectClrEvents>true</CollectClrEvents>
    <ClrCollectionOptions>CollectForNative DisableNGenRundown</ClrCollectionOptions>
    <CollectSampleEvents>true</CollectSampleEvents>
    <CollectGpuEvents>true</CollectGpuEvents>
    <CollectFileIO>true</CollectFileIO>
  </FilterConfig>

  <UserBufferSettings>
    <BufferFlushTimer>0</BufferFlushTimer>
    <BufferSize>256</BufferSize>
    <MinimumBuffers>512</MinimumBuffers>
    <MaximumBuffers>1024</MaximumBuffers>
  </UserBufferSettings>

  <KernelBufferSettings>
    <BufferFlushTimer>0</BufferFlushTimer>
    <BufferSize>256</BufferSize>
    <MinimumBuffers>512</MinimumBuffers>
    <MaximumBuffers>1024</MaximumBuffers>
  </KernelBufferSettings>

  <!-- List of MyCodeDirectory directories -->
  <JustMyCode>
    <MyCodeDirectory>C:\myBinaries1</MyCodeDirectory>
    <MyCodeDirectory>C:\myBinaries2</MyCodeDirectory>
  </JustMyCode>
</LocalConfig>

```
