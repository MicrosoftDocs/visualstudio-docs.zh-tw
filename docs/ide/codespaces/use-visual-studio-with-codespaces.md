---
title: 'Codespace (Preview 的 Visual Studio) '
description: 瞭解如何使用 Visual Studio IDE 搭配 GitHub Codespaces 進行 Windows 開發。
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: add43a5d130d8938193774d50bb643f48ecc3f8c
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104673043"
---
# <a name="how-to-use-visual-studio-with-a-codespace-preview"></a>如何搭配使用 Visual Studio 與 codespace (Preview) 

> [!Important] 
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 我們建議您參與我們的 [開發人員社區論壇](https://developercommunity.visualstudio.com/home) ，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。 

Visual Studio 在 GitHub Codespaces 中有絕佳的開發支援。 您可以建立並連接到 codespace，並具備 Visual Studio 的完整功能，以在遠端裝載的環境上處理您的專案。 即使您的原始程式碼和工具是在 codespace 中，而且您的編譯和偵錯工具是在雲端中進行，您的開發體驗仍會像是在本機工作一樣快速且不會發生。

> [!NOTE]
> 本文特別說明如何使用 Visual Studio 連接到 GitHub Codespaces。 您可以在 [Visual Studio Code](https://docs.github.com/github/developing-online-with-codespaces/connecting-to-your-codespace-from-visual-studio-code) 或 [GitHub](https://docs.github.com/github/developing-online-with-codespaces/developing-in-a-codespace) 檔中瞭解如何使用其他用戶端連接到 codespace。

> [!NOTE]
> 如果您尚未安裝 [Visual Studio 2019 Preview](https://aka.ms/vspreview) ，您可以從 [visualstudio.microsoft.com](https://aka.ms/vspreview)下載。

## <a name="enable-connect-to-github-codespaces"></a>啟用連接到 GitHub Codespaces

預設不會啟用使用 Visual Studio 2019 Preview 連線到 GitHub Codespaces，因此您必須先啟用 [預覽功能] 選項。

1. 在 Visual Studio 2019 Preview 中，請使用 [**工具**  >  **選項**] 功能表項目來開啟 [選項] 對話方塊。

2. 在 [ **環境**] 下，選取 [ **預覽功能** ]，然後選取 [連線 **至 GitHub Codespaces 預覽]** 功能。

   ![選取 [連線至 GitHub Codespaces 預覽] 功能](media/connect-to-github-codespaces-preview-feature.png)

3. 您將需要重新開機 Visual Studio，才能使用此功能。

## <a name="create-a-codespace"></a>建立 codespace

如果您還沒有 codespace，可以從 Visual Studio 建立一個。

1. 當您啟動 Visual Studio 時，開始視窗會顯示 [開始使用] 底下的 **[連線至 Codespace]** 按鈕。

   ![使用連線到 codespace 的 [開始] 視窗 Visual Studio](media/visual-studio-start-window.png)

2. 選取 **[連線至 Codespace]** ，系統將會提示您登入 GitHub。 您也可以建立 GitHub 帳戶（如果您還沒有的話）。

   ![Visual Studio 登入 GitHub](media/visual-studio-sign-in-to-github.png)

   當您選取 [登 **入 github**] 之後，請遵循線上 GitHub 登入工作流程。

3. 如果您從未建立過 codespace，系統會提示您建立一個。

   在 [Codespace 詳細資料] 底下，您需要提供存放 **庫 URL**。 GitHub Codespaces 會在建立時將指定的存放庫複製到您的 codespace。

   您也可以修改 **實例類型** ，並 **在 timeout 之後** 透過其下拉式清單暫停。 設定 codespace 詳細資料之後，請選取 [ **建立並連接]** 按鈕。

   ![Visual Studio codespace 詳細資料](media/visual-studio-codespace-details.png)

   GitHub Codespaces 會在 codespace 準備就緒之後，開始準備 codespace 並開啟 Visual Studio。

   Codespace 名稱將會出現在功能表列的遠端指示器中。

   ![Visual Studio 連線至 eShopOnWeb 儲存機制 codespace](media/visual-studio-eshoponweb-codespace.png)

4. 開始使用 Visual Studio，就像在本機工作一樣。 可以嘗試的方法：

   * 流覽原始程式碼。
   * 選取方案檔，然後)  (**Ctrl + Shift + B** 來建立方案。
   * 在原始程式檔中設定中斷點，然後按 **F5** 以在偵錯工具中啟動應用程式。
   * 進行變更，並將其認可至您的存放庫。   

> [!NOTE]
> 目前，您無法透過 GitHub [Codespaces 入口網站](https://github.com/codespaces)來建立 Visual Studio 的 github Codespaces。 您只能使用 Visual Studio 建立它們。

## <a name="connect-to-a-codespace"></a>連接到 codespace

建立 codespace 之後，您可以直接從 Visual Studio 開啟您的 codespace。

1. 當您啟動 Visual Studio 時，開始視窗會顯示 [開始使用] 底下的 **[連線至 Codespace]** 按鈕。

   ![使用連線到 codespace 的 [開始] 視窗 Visual Studio](media/visual-studio-start-window.png)

   如果您已經在 Visual Studio 中，您可以 **使用 [檔案**  >  **連接至 Codespace]** 功能表項目。

   ![Visual Studio 檔案連接至 codespace 功能表項目](media/visual-studio-file-connect-to-codespace.png)

2. 選取 **[連線至 Codespace]**。 如果您尚未登入，系統會提示您登入 GitHub。

3. 接著，您將會看到所有的 GitHub codespaces，以及其在右面板中顯示的詳細資料。

   ![Visual Studio 顯示可用的 GitHub codespaces 和詳細資料](media/visual-studio-connect-codespace.png)

   複製 Azure DevOps 存放庫的任何 codespaces 只會顯示在 Visual Studio，而不是在 GitHub 的 [Codespaces] 頁面上。

4. 選擇 codespace，然後選取 [連線 **]** 按鈕。 如果 codespace 已暫止，將會重新開機，且 Visual Studio 會開啟連接到該 codespace。

   Codespace 名稱將會出現在功能表列的遠端指示器中。

   ![Visual Studio 連線至 eShopOnWeb 儲存機制 codespace](media/visual-studio-eshoponweb-codespace.png)

5. 開始使用 Visual Studio，就像在本機工作一樣。 可以嘗試的方法：

   * 流覽原始程式碼。
   * 選取方案檔，然後)  (**Ctrl + Shift + B** 來建立方案。
   * 在原始程式檔中設定中斷點，然後按 **F5** 以在偵錯工具中啟動應用程式。
   * 進行變更，並將其認可至您的存放庫。

<!-- TBD ## Suspend a codespace -->

<!-- TBD ## Disconnect from a codespace -->

## <a name="see-also"></a>另請參閱

* [什麼是 GitHub Codespaces？](codespaces-overview.md)
* [如何自訂 codespace](customize-codespaces.md)
* [支援的 Visual Studio 功能](supported-features-codespaces.md)
