---
title: HOW TO：在 IDE 中四處移動 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.NextDocumentWindowNav
- IDE navigator
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94629a2e64d154313711b3e8968b28959d3341e8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805415"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>HOW TO：在 Visual Studio IDE 中四處移動
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

整合式開發環境 (IDE) 經過設計，可讓您使用數種不同方式，執行視窗至視窗以及檔案至檔案之間的移動 (根據您的喜好或專案需求而定)。 您可選擇在編輯器中循環瀏覽開啟的檔案，或是在 IDE 中循環瀏覽所有使用中的工具視窗。 您亦可在編輯器中直接切換至任何開啟的檔案，而忽略上次存取檔案的順序。 這些功能可協助您提升使用 IDE 工作時的生產力。

> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊可用選項，以及功能表命令的名稱和位置，可能會與 [說明] 中描述的有所不同。 當我們撰寫這個說明頁面時，主要是考慮 [一般開發設定]。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)

## <a name="keyboard-shortcuts"></a>鍵盤快速鍵
 在 Visual Studio 中幾乎所有功能表命令皆具有鍵盤快速鍵。 您亦可建立專屬的自訂快速鍵。 如需詳細資訊，請參閱[識別及自訂鍵盤快速鍵](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。

## <a name="navigating-among-files-in-the-editor"></a>在編輯器中的檔案之間巡覽
 您可以使用數種方法，在編輯器中開啟的檔案之間移動。 您可根據存取的順序來移動所有檔案，使用「IDE 瀏覽器」快速尋找任何目前開啟的檔案，或是將我的最愛檔案鎖定至索引標籤以一律顯示該檔案。

 根據存取順序，在編輯器中使用「向後巡覽」與「向前巡覽」方式來循環瀏覽開啟的檔案，其與在 Microsoft Internet Explorer 中使用 [上一頁] 和 [下一頁] 檢視記錄非常近似。

#### <a name="to-move-through-open-files-in-order-of-use"></a>依使用順序移動開啟的檔案

- 若要依最近存取的順序啟動開啟的文件，請按 CTRL + 減號。

- 若要依相反順序啟動開啟的文件，請按 CTRL + SHIFT + 減號。

  > [!NOTE]
  >  [向後巡覽] 和 [向前巡覽] 位於 [檢視] 功能表中。

  您亦可使用 [IDE 瀏覽器]、編輯器的 [使用中的檔案] 清單或 [Windows] 對話方塊，切換至編輯器中已開啟的特定檔案而忽略上次存取檔案的時間。

  [IDE 瀏覽器] 運作方式十分類似 Windows 應用程式切換器。 其僅可使用快速鍵來存取，而無法透過功能表使用。 您可使用兩個命令存取 [IDE 瀏覽器]\(如下所示)，以依據所需的循環瀏覽順序，循環瀏覽檔案。

  ![Visual Studio IDE 導覽器](../ide/media/vs2015-ide-navigator.png "VS2015_IDE_Navigator")

  `Window.PreviousDocumentWindowNav` 可讓您移至最近存取的檔案，並`Window.NextDocumentWindowNav`可讓您依相反順序移動。 「一般開發設定」會將 CTRL + SHIFT + TAB 指派至 `Window.PreviousDocumentWindowNav`，並將 CTRL + TAB 指派至 `Window.NextDocumentWindowNav`。

> [!NOTE]
>  若您使用的設定組合尚未將快速鍵組合指派至此命令，您可使用 [選項] 對話方塊的 [鍵盤] 頁面，指派專屬的自訂命令。 如需詳細資訊，請參閱[識別及自訂鍵盤快速鍵](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。

#### <a name="to-switch-to-specific-files-in-the-editor"></a>切換至編輯器中的特定檔案

-   按 CTRL + TAB，以顯示 [IDE 瀏覽器]。 按住 CTRL 鍵並重複按 TAB，直到您選取您想要切換前往的檔案。

    > [!TIP]
    >  若要反轉瀏覽 [使用中的檔案] 清單的順序，請按住 CTRL + SHIFT 鍵並按 TAB。

     \-或-

-   在編輯器的右上角，選擇 [使用中的檔案] 按鈕，然後從清單中選取要切換的檔案。

     \-或-

-   在功能表列上，依序選擇 [視窗]、[Windows]。

-   在清單中，選取您想要檢視的檔案，然後選擇 [啟動]。

## <a name="navigating-among-tool-windows-in-the-ide"></a>在 IDE 中的各個工具視窗之間巡覽
 [IDE 瀏覽器] 可讓您循環瀏覽已在 IDE 中開啟的工具視窗。 您可使用兩個命令存取 [IDE 瀏覽器]，以依據所需的循環瀏覽順序，循環瀏覽檔案。 `Window.PreviousToolWindowNav` 可讓您移至最近存取的檔案，並`Window.NextToolWindowNav`可讓您依相反順序移動。 「一般開發設定」會將 SHIFT + ALT + F7 指派至 `Window.PreviousDocumentWindowNav`，並將 ALT + F7 指派至 `Window.NextDocumentWindowNav`。

> [!NOTE]
>  若您使用的設定組合尚未將快速鍵組合指派至此命令，您可使用 [選項] 對話方塊的 [鍵盤] 頁面，指派專屬的自訂命令。 如需詳細資訊，請參閱[識別及自訂鍵盤快速鍵](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。

#### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>切換至 IDE 中的特定工具視窗

-   按下 ALT+F7 以顯示 [IDE 瀏覽器]。 按住 ALT 鍵並重複按 F7，直到您選取想要切換前往的視窗。

    > [!TIP]
    >  若要反轉瀏覽 [使用中的工具視窗] 清單的順序，請按住 SHIFT + ALT 鍵並按 F7。

## <a name="see-also"></a>請參閱
 [自訂視窗版面配置](../ide/customizing-window-layouts-in-visual-studio.md)[預設鍵盤快速鍵](../ide/default-keyboard-shortcuts-in-visual-studio.md)
