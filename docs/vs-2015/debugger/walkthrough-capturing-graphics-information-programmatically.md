---
title: 逐步解說：以程式設計方式擷取圖形資訊 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a5adeff9-afaf-4047-b5ce-ef0aefe710eb
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bb12e0691d4e867a73b9c8999d0ad57cebd7ec44
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942667"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>逐步解說：以程式設計方式擷取圖形資訊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 圖形診斷，透過程式設計方式從 Direct3D 應用程式擷取圖形資訊。  
  
 在下列這類情況下，程式設計擷取十分有用：  
  
-   圖形應用程式未使用現有的 Swapchain 時 (例如呈現為材質時)，會以程式設計方式開始擷取。  
  
-   應用程式未呈現時 (例如使用 DirectCompute 執行計算時)，會以程式設計方式開始擷取。  
  
-   如果呈現問題很難預期以及在手動測試中擷取，但是可以在執行階段使用應用程式狀態資訊，透過程式設計方式進行預測，請呼叫 `CaptureCurrentFrame`。  
  
##  <a name="CaptureDX11_2"></a> Windows 8.1 中的程式設計擷取  
 這部分的逐步解說示範如何在 Windows 8.1 上使用 DirectX 11.2 API 的應用程式中進行程式設計擷取 (使用穩固擷取方法)。 如需如何在於 Windows 8.0 上使用舊版 DirectX 的應用程式中，使用程式設計擷取的資訊，請參閱本逐步解說稍後的 [Programmatic capture in Windows 8.0 and earlier](#CaptureDX11_1) 。  
  
 本節顯示如何執行這些工作：  
  
-   準備應用程式以使用程式設計擷取  
  
-   取得 IDXGraphicsAnalysis 介面  
  
-   擷取圖形資訊  
  
> [!NOTE]
>  先前的程式設計擷取實作依賴 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 遠端工具來提供擷取功能，但是 Windows 8.1 透過 DirectX 11.2 支援直接擷取。 因此，在 Windows 8.1 上進行程式設計擷取，已經不再需要安裝遠端工具。  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>準備應用程式以使用程式設計擷取  
 若要在應用程式中使用程式設計擷取，它必須包括必要的標頭。 這些標頭是 Windows 8.1 SDK 的一部分。  
  
##### <a name="to-include-programmatic-capture-headers"></a>包括程式設計擷取標頭  
  
-   將這些標頭併入您將定義 IDXGraphicsAnalysis 介面的原始程式檔中：  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    >  不包含標頭檔 vsgcapture.h—which 支援程式設計擷取 Windows 8.0 上及更早版本，若要在 Windows 8.1 應用程式中執行程式設計擷取。 此標頭與 DirectX 11.2 不相容。 如果此檔案包含之後會包含 d3d11_2.h 標頭，則編譯器會發出警告。 如果包含 vsgcapture.h d3d11_2.h 之前，將不會啟動應用程式。  
  
    > [!NOTE]
    >  如果在電腦上安裝 2010 年 6 月 DirectX SDK，而且專案的 Include 路徑包含 `%DXSDK_DIR%includex86`，請將它移至 Include 路徑結尾。 請對程式庫路徑執行相同的處理。  
  
#### <a name="windows-phone-81"></a>Windows Phone 8.1  
 因為 Windows Phone 8.1 SDK 不包含 DXProgrammableCapture.h 標頭，您將需要定義`IDXGraphicsAnalysis`，讓您可以使用介面自行`BeginCapture()`和`EndCapture()`方法。 包括上一節中所述的其他標頭。  
  
###### <a name="to-define-the-idxgraphicsanalysis-interface"></a>定義 IDXGraphicsAnalysis 介面  
  
- 在包括標頭檔的相同檔案中，定義 IDXGraphicsAnalysis 介面。  
  
  ```  
  interface DECLSPEC_UUID("9f251514-9d4d-4902-9d60-18988ab7d4b5") DECLSPEC_NOVTABLE  
  IDXGraphicsAnalysis : public IUnknown  
  {  
      STDMETHOD_(void, BeginCapture)() PURE;  
      STDMETHOD_(void, EndCapture)() PURE;  
  };  
  ```  
  
  為了方便起見，您可以在新的標頭檔中執行這些步驟，然後將它包括在應用程式中需要它的位置。  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>取得 IDXGraphicsAnalysis 介面  
 您需要先取得 DXGI 偵錯介面，才能從 DirectX 11.2 擷取圖形資訊。  
  
> [!IMPORTANT]
>  當使用程式設計擷取時，您仍然必須執行您的應用程式在圖形診斷下 (中的 alt+f5 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]) 或底下[命令列擷取工具](../debugger/command-line-capture-tool.md)。  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>取得 IDXGraphicsAnalysis 介面  
  
-   請使用下列程式碼將 IDXGraphicsAnalysis 介面連結到 DXGI 偵錯介面。  
  
    ```  
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     請一定要檢查 `HRESULT` 所傳回的 `DXGIGetDebugInterface1` ，以確保您先取得有效的介面，再使用它：  
  
    ```  
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    >  如果在 `DXGIGetDebugInterface1` 傳回 `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`)，請確定應用程式是在圖形診斷下執行 ( [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中的 Alt+F5)。  
  
### <a name="capturing-graphics-information"></a>擷取圖形資訊  
 現在，您具有有效的 `IDXGraphicsAnalysis` 介面，可以使用 `BeginCapture` 和 `EndCapture` 來擷取圖形資訊。  
  
##### <a name="to-capture-graphics-information"></a>擷取圖形資訊  
  
-   若要開始擷取圖形資訊，請使用 `BeginCapture`：  
  
    ```  
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     擷取會在呼叫 `BeginCapture` 時立即開始，並不會等到下一個畫面格才開始。 擷取會在目前畫面格存在或呼叫 `EndCapture`時停止：  
  
    ```  
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  
  
##  <a name="CaptureDX11_1"></a> Programmatic capture in Windows 8.0 and earlier  
 這部分的逐步解說示範如何在使用 DirectX 11.1 API 之 Windows 8.0 (含) 以前版本的應用程式中進行程式設計擷取 (使用舊版擷取方法)。 如需如何在於 Windows 8.1 上使用 DirectX 11.2 的應用程式中，使用程式設計擷取的資訊，請參閱本逐步解說稍後的 [Windows 8.1 中的程式設計擷取](#CaptureDX11_2) 。  
  
 此部分顯示下列工作：  
  
-   準備電腦以使用程式設計擷取  
  
-   準備應用程式以使用程式設計擷取  
  
-   設定圖形記錄檔的名稱和位置  
  
-   使用 `CaptureCurrentFrame` API  
  
### <a name="preparing-your-computer-to-use-programmatic-capture"></a>準備電腦以使用程式設計擷取  
 程式設計擷取 API 使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的遠端工具來提供擷取功能。 要執行應用程式的電腦必須已安裝遠端工具，即使在本機電腦上使用程式設計擷取也是一樣。 當您在本機電腦上執行程式設計擷取時，不需要執行[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
 若要在於電腦上執行的應用程式中使用遠端擷取 API，則需要先在該電腦上安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 遠端工具。 不同版本的遠端工具支援不同的硬體平台。 如需如何安裝遠端工具的資訊，請參閱 Microsoft 下載網站的 [遠端工具下載頁面](http://go.microsoft.com/fwlink/p/?LinkId=246691) 。  
  
 或者， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會安裝必要元件來執行 32 位元應用程式的遠端擷取。  
  
> [!NOTE]
>  因為 ARM 裝置的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]不支援大部分的 Windows 桌面應用程式 (包括 [!INCLUDE[win8](../includes/win8-md.md)] )，所以搭配程式設計擷取 API 使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 遠端工具，是在 ARM 裝置上擷取圖形診斷的唯一方式。  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>準備應用程式以使用程式設計擷取  
 若要使用圖形診斷工具，您需要先擷取它所依賴的圖形資訊。 您可以使用 `CaptureCurrentFrame` API，透過程式設計方式來擷取資訊。  
  
##### <a name="to-prepare-your-app-to-capture-graphics-information-programmatically"></a>準備應用程式以透過程式設計方式擷取圖形資訊  
  
1.  請確定應用程式的原始程式碼中包括 `vsgcapture.h` 標頭。 它可能只會被包括在一個位置 (例如，要呼叫程式設計擷取 API 的原始程式碼檔案中)，或在從多個原始程式碼檔案呼叫 API 的預先編譯的標頭檔中。  
  
2.  在應用程式的原始程式碼中，若要擷取目前畫面格的其餘部分，請呼叫 `g_pVsgDbg->CaptureCurrentFrame()`。 此方法不會採用任何參數，也不會傳回值。  
  
### <a name="configuring-the-name-and-location-of-the-graphics-log-file"></a>設定圖形記錄檔的名稱和位置  
 圖形記錄會建立於 `DONT_SAVE_VSGLOG_TO_TEMP` 和 `VSG_DEFAULT_RUN_FILENAME` 巨集所定義的位置中。  
  
##### <a name="to-configure-the-name-and-location-of-the-graphics-log-file"></a>設定圖形記錄檔的名稱和位置  
  
- 若要防止將圖形記錄寫入至暫存目錄，請在 `#include <vsgcapture.h>` 行前面加入下列內容：  
  
  ```  
  #define DONT_SAVE_VSGLOG_TO_TEMP  
  ```  
  
   您可以定義此值，以將圖形記錄寫入至與工作目錄對應的位置，或寫入至絕對路徑 (如果 `VSG_DEFAULT_RUN_FILENAME` 的定義是絕對路徑)。  
  
- 若要將圖形記錄儲存至不同的位置，或將它命名為不同的檔案名稱，請在 `#include <vsgcapture.h>` 行前面加入下列內容：  
  
  ```  
  #define VSG_DEFAULT_RUN_FILENAME <filename>  
  ```  
  
   如果您未執行此步驟，則檔案名稱為 default.vsglog。 如果您未定義 `DONT_SAVE_VSGLOG_TO_TEMP`，則檔案的位置是與暫存目錄相對的位置；否則，它是與工作目錄相對的位置，或在另一個位置中 (如果您已指定絕對檔案名稱)。  
  
  針對[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]應用程式，暫存目錄的位置是專門針對每個使用者及應用程式，而且通常中的位置，例如 C:\users\\*username*\AppData\Local\Packages\\ *套件系列名稱*\TempState\\。 傳統型應用程式，暫存目錄的位置是每位使用者特有而且通常位於的位置，例如 C:\Users\\*使用者名稱*\AppData\Local\Temp\\。  
  
> [!NOTE]
>  若要寫入至特定位置，您必須具有寫入至該位置的權限；否則會發生錯誤。 請記住，在寫入資料的位置方面， [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 應用程式的限制多於桌面應用程式，而且可能需要進行額外設定才能寫入至特定位置。  
  
### <a name="capturing-the-graphics-information"></a>擷取圖形資訊  
 準備好應用程式，以供進行程式設計擷取，並選擇性地設定圖形記錄檔的位置和名稱之後，請建置應用程式，然後執行它，或對它進行偵錯以擷取資料；當您使用程式設計擷取 API 時，請勿從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 啟動圖形診斷。 圖形記錄會寫入至您指定的位置。 如果您想要保留這版的記錄檔，請將它移至另一個位置；否則，將會於再次執行應用程式時遭到覆寫。  
  
> [!TIP]
>  使用程式設計擷取時，還是可以手動擷取圖形資訊；如果應用程式在焦點中，則只需要按 **Print Screen**鍵。 您可以使用此技術，擷取程式設計擷取 API 未擷取到的其他圖形資訊。  
  
## <a name="next-steps"></a>後續步驟  
 此逐步解說示範如何透過程式設計方式擷取圖形資訊。 下一步是考慮此選項：  
  
-   了解如何使用圖形診斷工具分析擷取到的圖形資訊。 請參閱[概觀](../debugger/overview-of-visual-studio-graphics-diagnostics.md)。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：擷取圖形資訊](../debugger/walkthrough-capturing-graphics-information.md)   
 [Capturing Graphics Information](../debugger/capturing-graphics-information.md)   
 [命令列擷取工具](../debugger/command-line-capture-tool.md)
