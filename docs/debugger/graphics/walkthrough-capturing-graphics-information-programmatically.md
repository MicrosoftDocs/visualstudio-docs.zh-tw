---
title: 逐步解說： 以程式設計方式擷取圖形資訊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7652f05bf6028dd7d5b14d207fdd0b83a73ef5ad
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227627"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>逐步解說：以程式設計方式擷取圖形資訊
您可以使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 圖形診斷，透過程式設計方式從 Direct3D 應用程式擷取圖形資訊。

在下列這類情況下，程式設計擷取十分有用：

- 圖形應用程式未使用現有的 Swapchain 時 (例如呈現為材質時)，會以程式設計方式開始擷取。

- 應用程式未呈現時 (例如使用 DirectCompute 執行計算時)，會以程式設計方式開始擷取。

- 如果呈現問題很難預期以及在手動測試中擷取，但是可以在執行階段使用應用程式狀態資訊，透過程式設計方式進行預測，請呼叫 `CaptureCurrentFrame`。

## <a name="CaptureDX11_2"></a> Windows 10 中的程式設計擷取
這部分的逐步解說示範如何在 Windows 10 上使用 DirectX 11.2 API 的應用程式中進行程式設計擷取 (使用穩固擷取方法)。

本節顯示如何執行這些工作：

- 準備應用程式以使用程式設計擷取

- 取得 IDXGraphicsAnalysis 介面

- 擷取圖形資訊

> [!NOTE]
> 先前的程式設計擷取實作依賴針對 Visual studio 遠端工具[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]來提供擷取功能。

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
    > 請勿包括標頭檔 vsgcapture.h (其支援 Windows 8.0 (含) 以前版本上的程式設計擷取)，以在 Windows 10 應用程式中執行程式設計擷取。 此標頭與 DirectX 11.2 不相容。 如果此檔案包含之後會包含 d3d11_2.h 標頭，則編譯器會發出警告。 如果包含 vsgcapture.h d3d11_2.h 之前，將不會啟動應用程式。

    > [!NOTE]
    > 如果在電腦上安裝 2010 年 6 月 DirectX SDK，而且專案的 Include 路徑包含 `%DXSDK_DIR%includex86`，請將它移至 Include 路徑結尾。 請對程式庫路徑執行相同的處理。

### <a name="getting-the-idxgraphicsanalysis-interface"></a>取得 IDXGraphicsAnalysis 介面
您需要先取得 DXGI 偵錯介面，才能從 DirectX 11.2 擷取圖形資訊。

> [!IMPORTANT]
> 當使用程式設計擷取時，您仍然必須執行您的應用程式在圖形診斷下 (中的 alt+f5 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) 或底下[命令列擷取工具](command-line-capture-tool.md)。

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>取得 IDXGraphicsAnalysis 介面

- 請使用下列程式碼將 IDXGraphicsAnalysis 介面連結到 DXGI 偵錯介面。

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  請務必檢查`HRESULT`所傳回[DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1)以確保您會取得有效的介面，才能使用它：

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

- 若要在呼叫之後`EndCapture`，釋出的圖形物件。

## <a name="next-steps"></a>後續步驟
此逐步解說示範如何透過程式設計方式擷取圖形資訊。 下一步是考慮此選項：

- 了解如何使用圖形診斷工具分析擷取到的圖形資訊。 請參閱[概觀](overview-of-visual-studio-graphics-diagnostics.md)。

## <a name="see-also"></a>請參閱
[逐步解說：擷取圖形資訊](walkthrough-capturing-graphics-information.md)  
[Capturing Graphics Information](capturing-graphics-information.md)  
[命令列擷取工具](command-line-capture-tool.md)
