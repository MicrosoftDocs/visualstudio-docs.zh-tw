---
title: 逐步解說：以程式設計方式捕捉圖形資訊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7533c205b95b016c43bd2eef614b4c2825596e74
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835650"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>逐步解說：以程式設計方式擷取圖形資訊
您可以使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 圖形診斷，透過程式設計方式從 Direct3D 應用程式擷取圖形資訊。

在下列這類情況下，程式設計擷取十分有用：

- 圖形應用程式未使用現有的 Swapchain 時 (例如呈現為材質時)，會以程式設計方式開始擷取。

- 應用程式未呈現時 (例如使用 DirectCompute 執行計算時)，會以程式設計方式開始擷取。

- `CaptureCurrentFrame`當轉譯問題很容易預期並在手動測試中捕捉時呼叫，但可以使用應用程式在執行時間的狀態相關資訊，以程式設計方式預測。

## <a name="programmatic-capture-in-windows-10"></a><a name="CaptureDX11_2"></a> Windows 10 中的程式設計擷取
這部分的逐步解說示範如何在 Windows 10 上使用 DirectX 11.2 API 的應用程式中進行程式設計擷取 (使用穩固擷取方法)。

本節顯示如何執行這些工作：

- 準備應用程式以使用程式設計擷取

- 取得 IDXGraphicsAnalysis 介面

- 擷取圖形資訊

> [!NOTE]
> 舊版的程式設計捕獲依賴 Visual Studio 遠端工具來提供捕捉功能。

### <a name="preparing-your-app-to-use-programmatic-capture"></a>準備應用程式以使用程式設計擷取
若要在應用程式中使用程式設計擷取，它必須包括必要的標頭。 這些標頭是 Windows 10 SDK 的一部分。

##### <a name="to-include-programmatic-capture-headers"></a>包括程式設計擷取標頭

- 將這些標頭併入您將定義 IDXGraphicsAnalysis 介面的原始程式檔中：

    ```cpp
    #include <DXGItype.h>
    #include <dxgi1_2.h>
    #include <dxgi1_3.h>
    #include <DXProgrammableCapture.h>
    ```

    > [!IMPORTANT]
    > 請勿包括標頭檔 vsgcapture.h (其支援 Windows 8.0 (含) 以前版本上的程式設計擷取)，以在 Windows 10 應用程式中執行程式設計擷取。 此標頭與 DirectX 11.2 不相容。 如果在包含 d3d11_2 .h 標頭之後包含此檔案，則編譯器會發出警告。 如果 d3d11_2 .h 之前包含 vsgcapture.h，應用程式將不會啟動。

    > [!NOTE]
    > 如果在電腦上安裝 2010 年 6 月 DirectX SDK，而且專案的 Include 路徑包含 `%DXSDK_DIR%includex86`，請將它移至 Include 路徑結尾。 請對程式庫路徑執行相同的處理。

### <a name="getting-the-idxgraphicsanalysis-interface"></a>取得 IDXGraphicsAnalysis 介面
您需要先取得 DXGI 偵錯介面，才能從 DirectX 11.2 擷取圖形資訊。

> [!IMPORTANT]
> 使用程式設計的 capture 時，您仍然必須在圖形診斷下執行您的應用程式（中的 Alt + F5 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ），或在[命令列捕獲工具](command-line-capture-tool.md)底下執行。

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>取得 IDXGraphicsAnalysis 介面

- 請使用下列程式碼將 IDXGraphicsAnalysis 介面連結到 DXGI 偵錯介面。

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  請務必檢查 DXGIGetDebugInterface1 所 `HRESULT` 傳回的[DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) ，以確保您在使用有效的介面之前，先加以取得：

  ```cpp
  if (FAILED(getAnalysis))
  {
      // Abort program or disable programmatic capture in your app.
  }
  ```

  > [!NOTE]
  > 如果在 `DXGIGetDebugInterface1` 傳回 `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`)，請確定應用程式是在圖形診斷下執行 ( [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中的 Alt+F5)。

### <a name="capturing-graphics-information"></a>擷取圖形資訊
現在，您具有有效的 `IDXGraphicsAnalysis` 介面，可以使用 `BeginCapture` 和 `EndCapture` 來擷取圖形資訊。

##### <a name="to-capture-graphics-information"></a>擷取圖形資訊

- 若要開始擷取圖形資訊，請使用 `BeginCapture`：

    ```cpp
    ...
    pGraphicsAnalysis->BeginCapture();
    ...
    ```

    擷取會在呼叫 `BeginCapture` 時立即開始，並不會等到下一個畫面格才開始。 擷取會在目前畫面格存在或呼叫 `EndCapture`時停止：

    ```cpp
    ...
    pGraphicsAnalysis->EndCapture();
    ...
    ```

- 呼叫之後 `EndCapture` ，釋放繪圖物件。

## <a name="next-steps"></a>後續步驟
此逐步解說示範如何透過程式設計方式擷取圖形資訊。 下一步是考慮此選項：

- 了解如何使用圖形診斷工具分析擷取到的圖形資訊。 請參閱[總覽](overview-of-visual-studio-graphics-diagnostics.md)。

## <a name="see-also"></a>另請參閱
- [逐步解說：擷取圖形資訊](walkthrough-capturing-graphics-information.md)
- [擷取圖形資訊](capturing-graphics-information.md)
- [命令列擷取工具](command-line-capture-tool.md)
