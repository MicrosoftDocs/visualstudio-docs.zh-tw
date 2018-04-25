---
title: 匯入 XCode 專案 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
ms.technology: vs-ide-mobile
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 500dce15e695cf53a061f8405919e808b8f7c493
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="import-an-xcode-project"></a>匯入 XCode 專案
適用於跨平台行動裝置開發的 Microsoft Visual C++ 內含將您的 XCode 專案移至 Visual Studio 的支援，您可以在其中建立跨平台的程式庫，並與其他專案共用程式碼。 [從 XCode 匯入] 精靈可簡化下列流程：在 XCode 目標中匯入專案，並分割 C++ 程式碼，以用來做為靜態程式庫或共用程式碼專案。 您可以在 Visual Studio 中管理 iOS 特有的程式碼，但仍能使用 XCode 來執行分鏡腳本和組建。 如需如何輕鬆地在 Visual Studio 和 XCode 之間來回移動程式碼的相關資訊，請參閱＜在 XCode 和 Visual Studio之間移動變更＞。  
  
## <a name="using-the-import-from-xcode-wizard"></a>使用 [從 XCode 匯入] 精靈  
 本主題示範如何將 XCode 專案移到 Visual Studio，以利用共用程式碼和跨平台解決方案。 必要條件是您必須先將 Mac 與 Visual studio 配對，才能匯入、匯出和建置專案。 如需如何設定配對的相關指示，請參閱[安裝和設定工具以使用 iOS 進行建置](../cross-platform/install-and-configure-tools-to-build-using-ios.md)。 您也必須透過網路共用您的 XCode 專案，或將它移至 Visual Studio 電腦以使用 [從 XCode 匯入] 精靈。  
  
#### <a name="import-from-xcode"></a>從 XCode 匯入  
  
1.  在 [檔案] 功能表上，選擇 [新增]、[匯入]、[從 XCode 匯入]。 這會啟動 [從 XCode 匯入] 精靈對話方塊。  
  
     ![選擇要匯入的 XCode 目標專案](../cross-platform/media/cppmdd_u2_importxcode_choose.PNG "CPPMDD_U2_ImportXCode_Choose")  
  
2.  在 [選擇專案] 窗格中，選擇 [瀏覽] 按鈕來選取 XCode.pbxproj 檔案。 在 [選取 XCode 專案檔] 對話方塊中瀏覽至專案檔，然後選擇 [開啟]。  
  
     ![在 [選取 Xcode 專案檔] 對話方塊中選取專案檔](../cross-platform/media/cppmdd_u2_importxcode_browse.PNG "CPPMDD_U2_ImportXCode_Browse")  
  
     在 [從 XCode 匯入] 精靈中，選擇 [下一步]。  
  
3.  在 [目的目標] 窗格中，選擇要從 XCode 專案匯入 Visual Studio 專案的目標。 XCode 目標與 Visual Studio 專案類似；大部分都是可產生二進位檔的程式碼與資源組合。 [從 XCode 匯入] 精靈只允許匯入會產生二進位檔，但不會產生靜態程式庫的目標，以做為目的目標。 XCode 靜態程式庫的目標是下一個步驟的主題。  
  
     ![[從 XCode 匯入] 精靈的 [目的目標] 窗格](../cross-platform/media/cppmdd_u2_importxcode_destination.jpg "CPPMDD_U2_ImportXCode_Destination")  
  
     針對 [要匯入的目標] 中選取的每一個目標，精靈會自動偵測可分割成不同靜態程式庫專案的 C++ 程式碼檔案，並將它們放入 [C++ 專案項目] 區段中。 其他程式碼和資源則會保留在 [XCode 專案項目] 區段中。 當精靈完成匯入程序時，這些會在 Visual Studio 中變成不同的靜態程式庫和應用程式專案。 根據預設，精靈不會將單元測試和架構目標分割成不同的專案。  
  
     若要變更每個專案中有哪些檔案，請使用向上和向下按鈕。 當您滿意每個專案中的檔案時，選擇 [下一步] 繼續。  
  
4.  在 [目的目標] 窗格中，選擇要將哪些靜態程式庫目標從 XCode 專案匯入 Visual Studio 專案。 在此窗格中，您可以選擇要將哪些檔案放在共用程式碼專案中，以及要將哪些檔案放在靜態程式庫專案中。 在 [要匯入的目標] 清單的每一個目標中，您可以使用向上和向下按鈕，來控制 [共用程式碼專案項目] 和 [靜態程式庫專案項目] 中要放入哪些檔案。  
  
     ![從 XCode [程式庫目標] 窗格匯入](../cross-platform/media/cppmdd_u2_importxcode_library.jpg "CPPMDD_U2_ImportXCode_Library")  
  
     共用程式碼專案是在 Visual Studio 中的專案之間共用一組原始程式碼檔案的一種方式。 系統會建置程式碼，做為包含該程式碼的專案一部分，而不是程式碼本身的專案。 由於包含共用程式碼的專案可能有不同的架構和組態，因此，可以使用這個最佳方式來提供單一專案，以包含可能針對多種平台建置的程式碼。  
  
     當您滿意每個專案中的檔案時，選擇 [下一步] 繼續。  
  
5.  [全域屬性] 窗格可用來設定 Visual Studio 中，適用於所有 iOS 專案的架構搜尋路徑和包含標頭搜尋路徑。 Vvisual Studio 會使用這些路徑來瀏覽原始程式碼，以及供 IntelliSense 使用。 當您建立要使用一組通用標頭和架構的 iOS 專案時，這些全域路徑就很實用。  
  
     ![從 XCode [全域屬性] 窗格匯入](../cross-platform/media/cppmdd_u2_importxcode_global.jpg "CPPMDD_U2_ImportXCode_Global")  
  
     這些全域路徑也可以在 Visual Studio 中的 [選項] 對話方塊中加以設定。 若要尋找它們，在 [工具] 功能表上，選取 [選項]。 在 [選項] 對話方塊中，依序展開 [跨平台]、[C++]、[iOS] 及 [全域屬性]。  
  
     選擇 [下一步]  繼續進行。  
  
6.  [架構] 窗格可用來設定 Visual Studio 用於瀏覽的路徑，以及供您專案使用的 IntelliSense。 Visual Studio 必須能夠存取路徑，以供您 XCode 專案所參考的每一個架構使用。 精靈會檢查 XCode 專案中的架構參考，並顯示 Visual Studio 是否可以找到該架構。 Visual Studio 應該探索任何您已經在全域屬性中設定的路徑。 例外狀況會列在 [架構] 清單中。 針對使用 X 列出的每一個架構，為 Visual Studio 提供電腦可存取路徑以尋找架構。 您可以使用瀏覽按鈕 […]，利用 [選取資料夾] 對話方塊來尋找路徑。 架構路徑可以是本機複本，或是 Mac 上的網路可存取共用。  
  
     ![從 XCode [架構] 窗格匯入](../cross-platform/media/cppmdd_u2_importxcode_frameworks.jpg "CPPMDD_U2_ImportXCode_Frameworks")  
  
     選擇 [下一步]  繼續進行。  
  
7.  [專案設定] 窗格可讓您變更架構，並包含標頭搜尋路徑設定，以供精靈所建立的每個專案使用。 使用此窗格，來設定不同於通用設定的專案特定路徑。  
  
     若要設定特定專案的路徑，在 [目的專案] 下拉式清單中，選取專案檔，然後在 [架構搜尋路徑] 和 [包含標頭搜尋路徑] 控制項中設定值。 您可以使用每個控制項旁邊的瀏覽按鈕 […]，利用 [選取資料夾] 對話方塊來尋找路徑。  
  
     ![從 XCode 專案窗格匯入](../cross-platform/media/cppmdd_u2_importxcode_projects.jpg "CPPMDD_U2_ImportXCode_Projects")  
  
     如果未在 Visual Studio 中將遠端 Mac 與此 PC 配對，即會顯示 [設定遠端電腦] 連結。 如需如何設定配對的相關指示，請參閱[安裝和設定工具以使用 iOS 進行建置](../cross-platform/install-and-configure-tools-to-build-using-ios.md)。  
  
     若要使用精靈設定來匯入 XCode 專案，請選擇 [匯入]。  
  
 [從 XCode 匯入] 精靈會在 Visual Studio 中建立專案，以對應到選取的 XCode 專案目標。 系統會將可與其他 C++ 專案共用的程式碼分割成不同的共用程式碼和靜態程式庫專案。 其餘的程式碼則會放在 iOS 程式庫和應用程式專案中，而這類專案是可透過 Visual Studio 從遠端建置的專案。 如需在 Visual Studio 和 XCode 之間移動程式碼的詳細資訊，請參閱[同步處理 XCode 和 Visual Studio 之間的變更](../cross-platform/sync-changes-between-xcode-and-visual-studio.md)。