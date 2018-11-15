---
title: 在 Visual Studio 中設計 XAML
ms.date: 07/17/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: a3adcb961e3031180054706da9d43dd04dccdedf
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348639"
---
# <a name="design-xaml-in-visual-studio"></a>在 Visual Studio 中設計 XAML

Visual Studio 和 Blend for Visual Studio 都提供視覺化工具，用於為各種應用程式類型建立更吸引人的使用者介面和豐富的媒體體驗。 兩種工具都具有一組共同的功能，包括視覺 XAML 編輯器，但是 Blend for Visual Studio 提供更進階工作的其他設計工具，例如動畫和行為。

設計應用程式的程序取決於您選擇的工具和目標平台。 本文會比較 Visual Studio 和 Blend for Visual Studio 中的 XAML 設計工具。 如需使用工具的更詳細逐步解說，請參閱下列主題：

- [在 Visual Studio 中使用 XAML 設計工具建立 UI](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
- [使用 Blend for Visual Studio 建立 UI](creating-a-ui-by-using-blend-for-visual-studio.md)

## <a name="choose-the-right-tool"></a>選擇正確的工具

您多半是取決於您的技能組合選擇設計工具。 如果您偏向於程式碼導向，可以在 Visual Studio 中撰寫 XAML 程式碼來完成進階的設計工作。 如果您偏向於設計導向，Blend for Visual Studio 可讓您無須撰寫程式碼也能執行進階的工作。

您可以在 Visual Studio 和 Blend for Visual Studio 之間來回切換，甚至可以同時開啟相同的專案。 當您切換到其他 IDE 時，可以透過自動重新載入，套用在單一 IDE 中對 XAML 檔案所做的變更。 您可以在任一 IDE 中透過 [工具] > [選項] 對話方塊中的選項控制重新載入行為。

### <a name="shared-capabilities"></a>共用的功能

如需最基本的工作，Visual studio IDE 和 Blend for Visual Studio 共用一組相同的視窗和功能，其中只有些微的差異。 一些重點包括：

- **一致的使用者介面：** 您可以在熟悉的 Visual Studio 使用者介面環境中設計應用程式，讓在 IDE 之間切換成為更愉快且更有生產力的經驗。 Blend for Visual Studio 會使用 Visual Studio 暗色調佈景主題，藉由改善您的內容與使用者介面之間的對比，協助您專注於正在設計的內容。 請參閱[使用 XAML 設計工具建立 UI](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)。

     ![Blend for Visual Studio IDE](../designers/media/blendide.png)

- **XAML IntelliSense：** 兩者的 IDE 都支援您預期之所有來自 IntelliSense 的通用功能，包括陳述式完成、支援一般編輯器作業，像是註解和格式化程式碼，以及巡覽至資源、繫結和程式碼。

- **基本偵錯功能：** 您現在可以在 Blend 中偵錯，包括在程式碼中設定中斷點來執行中的偵錯應用程式。 為了維持與 Visual Studio 一致的偵錯體驗，Blend for Visual Studio 包含大部分的 Visual Studio 偵錯視窗和工具列。 進階偵錯功能，例如診斷和程式碼分析，只能在 Visual Studio 中使用。 請參閱[在 Visual Studio 中偵錯](../debugger/debugging-in-visual-studio.md)。

- **檔案重新載入經驗：** 您可以在 Blend for Visual Studio 或 Visual Studio 中編輯 XAML 檔案，當您在已編輯的檔案之間切換時，會讓它們自動重新載入。 若要降低工作流程中斷，您現在可以在 [檔案重新載入] 對話方塊中設定您的檔案重新載入喜好。

     ![檔案重新載入體驗](../designers/media/blendfilereload.png)

- **同步處理的配置和設定：** 自訂配置可讓您儲存並套用工具視窗配置的自訂項目。 當您使用相同的 Microsoft 帳戶登入時，Visual Studio 會跨電腦同步處理 Visual Studio 和 Blend for Visual Studio 的這些自訂項目和喜好設定。 請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

- **常見的 [方案總管]：**[方案總管] 會提供您的專案和其檔案的組織化檢視，而且也已準備好存取與其相關聯的命令。 使用 [方案總管]，使用大型企業專案更加輕鬆。 請參閱[解決方案和專案](../ide/solutions-and-projects-in-visual-studio.md)。

- **Team Explorer：** 您可以使用 [Team Explorer] 管理您具有 GIT 或 TFS 儲存機制的專案，有助於團隊共同作業。 請參閱 [在 Team Explorer 中工作](/azure/devops/user-guide/work-team-explorer)。

- **NuGet：** 可以管理在 Visual Studio 和 Blend for Visual Studio 中的 NuGet 封裝。 NuGet 是 .NET Framework 的封裝管理員，簡化了從方案安裝與移除封裝。

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Blend for Visual Studio 中的進階功能

若要提升產能，請考慮使用 Blend for Visual Studio 來處理下列工作。 這些都是 Blend for Visual Studio 可提供比 Visual Studio 設計工具或程式碼本身更快速度和更多功能之處。

|以|Visual Studio|Blend for Visual Studio|詳細資訊|
|--------|-------------------| - | - |
|**建立動畫**|動畫沒有設計工具，您必須以程式設計方式來建立動畫。 這需要了解動畫、WPF 中的計時系統以及大量編碼專業知識。|您能以視覺化方式建立動畫，並在 Blend for Visual Studio 中預覽。 這比在程式碼中建置動畫來得更多更精準。 您可以新增觸發程序來處理使用者互動，而且可以切換到程式碼以加入事件處理常式和其他功能。|[製作物件動畫](../designers/animate-objects-in-xaml-designer.md)|
|**將圖形和文字轉換成更容易操作的路徑**|不支援。|您可以將圖形轉換成路徑，使其更好編輯控制，藉此稍微或大幅變更圖形 (例如矩形和橢圓形)。 您可以調整形狀或合併路徑，並從多個圖形中建立複合路徑。<br /><br /> 您也可以將文字區塊轉換成路徑，以便做為向量影像來操作。|[繪製圖案與路徑](../designers/draw-shapes-and-paths.md)|
|**將互動功能加入至 UI 設計**|需要 C#、Visual Basic 或 C++ 程式碼。|在控制項上進行拖放行為以將互動功能加入到靜態設計中。 這些行為屬於隨即可用的程式碼片段，可封裝像是拖/放、縮放及視覺狀態變更等的功能。 有越來越多的行為可供選擇，也可建立自己的行為。<br /><br /> 您可以之後在 Blend for Visual Studio 中變更行為的屬性或將事件處理常式加入至程式碼中，藉此自訂每個行為。|[插入控制項並修改其行為](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)|
|**使用 Adobe 作品**|不支援。|匯入 Adobe FXG、PhotoShop 或 Illustrator 的作品，並在 Blend for Visual Studio 中實作此 UI。|[插入影像、視訊和音訊剪輯](../designers/insert-images-videos-and-audio-clips-in-xaml-designer.md)|
|**編輯控制項、範本和樣式**|需要編碼並具備 WPF 樣式和範本的知識。|將任何影像轉換成控制項。<br /><br /> 只要按幾下滑鼠，即可使用範本編輯工具來變更控制項、樣式和範本。<br /><br /> 例如，您可以使用 Blend for Visual Studio 樣式資源來實作常見 WPF 控制項 (例如按鈕、清單方塊，捲軸列、功能表等)，並直接在 Blend for Visual Studio 中變更其色彩、樣式或基礎範本。 之後如果想要的話，您可以切換到程式碼做最後修飾。|[修改物件的樣式](../designers/modify-the-style-of-objects-in-blend.md)|
|**將 UI 連接到資料**|您可以從資源 (例如 SQL Server 資料庫、WCF 或 Web 服務、物件或 SharePoint 清單) 建立資料來源，然後將資料來源繫結至 UI 控制項。<br /><br /> 設計階段資料必須以手動方式建立才能獲得互動式的設計體驗。|輕鬆建立範例資料以用於原型設計和測試。 準備好時切換到即時資料。<br /><br /> Blend for Visual Studio 的資料產生功能相當傑出 (您可以輕鬆地即時新增名稱、數字、URL、相片)，為您節省許多時間。<br /><br /> 對於即時資料，您可以將 UI 控制項繫結至 XML 檔案，或任何 CLR 資料來源。|[顯示資料](../designers/display-data-in-blend.md)|

如需進階 XAML 設計的詳細資訊，請參閱[使用 Blend for Visual Studio 建立 UI](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)。
