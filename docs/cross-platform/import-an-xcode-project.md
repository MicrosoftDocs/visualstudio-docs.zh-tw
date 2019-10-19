---
title: 匯入 Xcode 專案 |Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.topic: conceptual
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
ms.technology: vs-ide-mobile
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 62161b612d6c4583cd2206c3d18dc6606d2d9f0b
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588899"
---
# <a name="import-an-xcode-project"></a>匯入 Xcode 專案

適用于跨平臺行動裝置開發的 Visual Studio 工具C++包含將 Xcode 專案移至 Visual Studio 的支援，您可以在其中建立跨平臺程式庫，並與其他專案共用程式碼。 [從 Xcode 匯入] 會簡化匯入專案和分割 Xcode 目標C++中的程式碼，以作為靜態程式庫或共用程式碼專案的流程。 您可以在 Visual Studio 中管理 iOS 專屬的程式碼，並繼續使用 Xcode 來進行分鏡腳本和組建。 如需有關如何輕鬆地在 Visual Studio 和 Xcode 之間移動程式碼的詳細資訊，請參閱[同步處理 Xcode 與 Visual Studio 之間的變更](sync-changes-between-xcode-and-visual-studio.md)。

## <a name="use-the-import-from-xcode-wizard"></a>使用 [從 Xcode 匯入]

本文說明如何將 Xcode 專案移至 Visual Studio，以利用程式碼共用和跨平臺解決方案。 必要條件是，您必須將 Mac 配對到 Visual Studio，才能匯入、匯出和建立您的專案。 如需如何設定配對的相關指示，請參閱[安裝和設定工具以使用 iOS 進行建置](../cross-platform/install-and-configure-tools-to-build-using-ios.md)。 您也必須透過網路共用您的 Xcode 專案，或將它移至您的 Visual Studio 電腦，以使用 [從 Xcode 匯入]。

### <a name="import-from-xcode"></a>從 Xcode 匯入

1. 在 [檔案 **] 功能表上選擇 [** **新增**]、[匯**入**]、[**從 Xcode 匯入**] 此命令會啟動 [**從 Xcode 匯入**] 對話方塊。

   ![選擇要匯入的 Xcode 目標專案](../cross-platform/media/cppmdd_u2_importxcode_choose.PNG "選擇要匯入的 Xcode 目標專案")

1. 在 [**選擇專案**] 窗格中，選擇 [流覽] 按鈕以選取 Xcode *.pbxproj*檔案。 在 [**選取 Xcode 專案**檔] 對話方塊中，流覽至專案檔，然後選擇 [**開啟**]。

   ![在 [選取 Xcode 專案檔] 對話方塊中選取專案檔](../cross-platform/media/cppmdd_u2_importxcode_browse.PNG "在 [選取 Xcode 專案檔] 對話方塊中選取專案檔")

   在 [從 Xcode 匯入] 中，選擇 [**下一步**]。

1. 在 [**目的目標**] 窗格中，從 Xcode 專案中選擇要匯入 Visual Studio 專案的目標。 Xcode 目標類似于 Visual Studio 專案;大部分是產生二進位檔的程式碼和資源的集合。 [從 Xcode 匯入] 只允許匯入產生二進位的目標，而不是靜態程式庫，做為目的地目標。 Xcode 靜態程式庫目標是下一個步驟的主旨。

   ![從 Xcode wizard 目的地目標窗格匯入](../cross-platform/media/cppmdd_u2_importxcode_destination.jpg "從 Xcode wizard 目的地目標窗格匯入")

   針對 [要匯入的目標] 中選取的每一個目標，精靈會自動偵測可分割成不同靜態程式庫專案的 C++ 程式碼檔案，並將它們放入 [C++ 專案項目] 區段中。 其他程式碼和資源會保留在 [ **Xcode 專案專案**] 區段中。 當精靈完成匯入程序時，這些會在 Visual Studio 中變成不同的靜態程式庫和應用程式專案。 根據預設，單元測試和架構目標不會由 wizard 分割成個別的專案。

   若要變更每個專案中有哪些檔案，請使用向上和向下按鈕。 當您對每個專案中的檔案感到滿意時，請選擇 **[下一步]** 繼續進行。

1. 在 [連結**庫目標**] 窗格中，從 Xcode 專案中選擇要匯入 Visual Studio 專案的靜態程式庫目標。 在此窗格中，您可以選擇要放置在共用程式碼專案中的檔案，以及要放在靜態程式庫專案中的檔案。 在 [要匯入的**目標**] 清單的每個目標中，您可以使用 [上移] 和 [下移] 按鈕來控制要放置在**共用程式碼專案專案**中的檔案和**靜態程式庫專案**專案。

   ![從 Xcode 程式庫 [目標] 窗格匯入](../cross-platform/media/cppmdd_u2_importxcode_library.jpg "從 Xcode 程式庫 [目標] 窗格匯入")

   共用程式碼專案是一種在 Visual Studio 中的專案之間共用一組來源檔案的方式。 系統會建置程式碼，做為包含該程式碼的專案一部分，而不是程式碼本身的專案。 包含共用程式碼的專案可能會有不同的架構和設定。 共用程式碼專案是提供單一專案的最佳方式，其中包含的程式碼可能會針對許多類型的平臺而建立。

   當您對每個專案中的檔案感到滿意時，請選擇 **[下一步]** 繼續進行。

1. 使用 [**全域屬性**] 窗格來設定 Visual Studio 中所有 iOS 專案的架構搜尋路徑和 include 標頭搜尋路徑。 Vvisual Studio 會使用這些路徑來瀏覽原始程式碼，以及供 IntelliSense 使用。 當您建立要使用一組通用標頭和架構的 iOS 專案時，這些全域路徑就很實用。

   ![從 Xcode 全域屬性窗格匯入](../cross-platform/media/cppmdd_u2_importxcode_global.jpg "從 Xcode 全域屬性窗格匯入")

   這些全域路徑也可以在 Visual Studio 中的 [選項] 對話方塊中加以設定。 若要尋找它們，在 [工具] 功能表上，選取 [選項]。 在 [**選項**] 對話方塊中，展開 [**C++** **跨平臺** >   > **iOS**  > **全域屬性**]。

   選擇 [下一步] 繼續進行。

1. [架構] 窗格可用來設定 Visual Studio 用於瀏覽的路徑，以及供您專案使用的 IntelliSense。 您必須能夠存取 Xcode 專案所參考之每個架構的 Visual Studio 路徑。 Wizard 會檢查 Xcode 專案中的架構參考，並顯示 Visual Studio 是否可以找到架構。 Visual Studio 應該探索任何您已經在全域屬性中設定的路徑。 例外狀況會列在 [架構] 清單中。 針對使用 X 列出的每一個架構，為 Visual Studio 提供電腦可存取路徑以尋找架構。 您可以使用瀏覽按鈕 […]，利用 [選取資料夾] 對話方塊來尋找路徑。 架構路徑可以是本機複本，或是 Mac 上的網路可存取共用。

   ![從 Xcode 架構匯入窗格](../cross-platform/media/cppmdd_u2_importxcode_frameworks.jpg "從 Xcode 架構匯入窗格")

   選擇 [下一步] 繼續進行。

1. [專案設定] 窗格可讓您變更架構，並包含標頭搜尋路徑設定，以供精靈所建立的每個專案使用。 使用此窗格，來設定不同於通用設定的專案特定路徑。

   若要設定特定專案的路徑，請在 [**目的地專案**] 下拉式選單中選取專案檔案。 然後，設定 [**架構搜尋路徑**] 和 [**包含標頭搜尋路徑**] 控制項中的值。 您可以使用每個控制項旁邊的瀏覽按鈕 […]，利用 [選取資料夾] 對話方塊來尋找路徑。

   ![從 Xcode 專案匯入窗格](../cross-platform/media/cppmdd_u2_importxcode_projects.jpg "從 Xcode 專案匯入窗格")

   如果未在 Visual Studio 中將遠端 Mac 與此 PC 配對，即會顯示 [設定遠端電腦] 連結。 如需如何設定配對的相關指示，請參閱[安裝和設定工具以使用 iOS 進行建置](../cross-platform/install-and-configure-tools-to-build-using-ios.md)。

   若要使用 wizard 設定匯入 Xcode 專案，請選擇 [匯**入**]。

   [從 Xcode 匯入] 會在對應至所選 Xcode 專案目標的 Visual Studio 中建立專案。 系統會將可與其他 C++ 專案共用的程式碼分割成不同的共用程式碼和靜態程式庫專案。 其餘的程式碼則會放在 iOS 程式庫和應用程式專案中，而這類專案是可透過 Visual Studio 從遠端建置的專案。 如需在 Visual Studio 和 Xcode 之間移動程式碼的詳細資訊，請參閱[同步處理 Xcode 與 Visual Studio 之間的變更](../cross-platform/sync-changes-between-xcode-and-visual-studio.md)。

## <a name="see-also"></a>請參閱

- [使用安裝跨平臺行動開發C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
