---
title: "Visual Studio Tools for Unity Azure 逐步解說準備 | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: B921C2AC-B5D6-4B24-918E-511F83D57275
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 7554380435c77750eb48a5ce261cc0a2b3885ccd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="prepare-the-development-environment"></a>準備開發環境

在 Unity 中使用 Azure Mobile Client SDK 有一些必要條件。

## <a name="download-and-install-unity-2017"></a>下載和安裝 Unity 2017

需要 Unity 2017.1 或更新版本。 所有 Unity 計劃都可搭配本逐步解說使用，包括免費的個人計劃。 從 https://store.unity.com/ 下載 Unity。

## <a name="download-and-install-visual-studio-2017"></a>下載和安裝 Visual Studio 2017

本逐步解說需要 Visual Studio 2017 15.3 和更新版本，才能使用 Unity 工作負載進行遊戲開發。 所有 Visual Studio 2017 版本都可搭配本逐步解說使用，包括免費的 Community Edition。

1. 在 https://www.visualstudio.com/ 下載 Visual Studio 2017。

2. 安裝 Visual Studio 2017 並確定啟用 [使用 Unity 進行遊戲開發]。

 ![選取 Unity 工作負載](media/vstu_azure-prepare-dev-environment-image0.png)

 > [!NOTE]
 > 如果已安裝 Visual Studio 2017，您可以執行 Visual Studio 安裝程式來檢視及修改工作負載。

## <a name="create-a-new-3d-unity-project"></a>建立新的 3D Unity 專案

啟動 Unity 並建立新的 3D 專案。

![建立新的 Unity 專案](media/vstu_azure-prepare-dev-environment-image1.png)

## <a name="set-the-script-editor-to-visual-studio-preview-2017"></a>將指令碼編輯器設定為 Visual Studio Preview 2017

您可能已將 Visual Studio 2017 設定為 Unity 的外部指令碼編輯器，但請務必確定選取 15.3 預覽版本。

1. 從 Unity 的 [編輯] 功能表，選擇 [編輯] > [喜好設定...]。

  ![開啟 [喜好設定] 功能表](media/vstu_azure-prepare-dev-environment-image1.2.png)

2. 當 Unity 的 [喜好設定] 視窗出現時，選取左邊的 [外部工具] 索引標籤。

3. 在 [External Script Editor] (外部指令碼編輯器) 下拉式功能表中，選取 [Visual Studio 2017]。

  ![設定外部指令碼編輯器](media/vstu_azure-prepare-dev-environment-image3.png)

## <a name="change-the-unity-scripting-runtime-to-net-46"></a>將 Unity 指令碼執行階段變更為 .NET 4.6
本逐步解說需要 .NET 4.6，才能使用 Azure Mobile Client SDK 及其相依項目。

1. 從 Unity 的 [檔案] 功能表，選擇 [檔案] > [組建設定...]。

  ![開啟 [組建設定]](media/vstu_azure-prepare-dev-environment-image4.png)

2. 按一下 [播放程式設定...] 按鈕。

  ![開啟 [播放程式設定]](media/vstu_azure-prepare-dev-environment-image5.png)

3. [播放程式設定] 會在 Unity 的 [檢查] 視窗中開啟。 在 [設定] 標題下，按一下 [Scripting Runtime Version (指令碼執行階段版本)] 下拉式清單，然後選取 [Experimental (.NET 4.6 Equivalent)] (實驗性 (.NET 4.6 對等項目))。 這會顯示對話方塊，要求您重新啟動 Unity。 選取 [重新啟動]。

  ![選取 .NET 4.6](media/vstu_azure-prepare-dev-environment-image6.png)

## <a name="add-a-reference-to-systemnethttpdll"></a>將參考新增至 System.Net.Http.dll

Unity.NET 4.6 對等指令碼執行階段允許使用 System.Net.Http 套件，Azure Mobile Client SDK 需要此套件。 此 DLL 檔案隨附於 Unity，不過必須加入參考才能使用。

1. 在 Unity 編輯器的 [專案] 視窗中，**以滑鼠右鍵按一下** **Assets** 資料夾，然後選取 [Show in Explorer] (在檔案總管中顯示)。

  ![在檔案總管中顯示 Assets 資料夾](media/vstu_azure-prepare-dev-environment-image7.png)

2. 在出現的檔案總管視窗中，按兩下 **Assets** 目錄將它開啟。

3. 在 Assets 目錄中，**按一下滑鼠右鍵**並選取 [新增] > [文字文件]。

4. 在文字編輯器中開啟新的文字文件，並新增下列一行：`-r:System.Net.Http.dll`

5. 儲存並關閉文件。

4. 將新的文字文件重新命名為 "**mcs.rsp**"，並確定刪除 .txt 副檔名。

  * 如果您有隱藏的副檔名，您必須變更資料夾檢視選項才能顯示這些檔案。
  * 開啟 [開始] 功能表，並鍵入「資料夾選項」進行搜尋。 選取 [檔案總管選項]。
  * 選取 [檢視] 索引標籤，然後在 [進階設定] 中，確定取消核取 [隱藏已知檔案類型的副檔名]。

    ![在檔案總管中顯示 Assets 資料夾](media/vstu_azure-prepare-dev-environment-image8.png)

完成這些步驟之後，Unity 專案的根 **Assets** 目錄中應該會有名為 **mcs.rsp** 且包含 `r:System.Net.Http.dll` 行的檔案。

>[!NOTE]
> 參考功能需要 Visual Studio Tools for Unity 3.3 和更新版本，Visual Studio 15.3+ Unity 工作負載隨附此版本。 如果這個步驟對您不適用，請確定您安裝的是正確的 VSTU 版本。

## <a name="add-the-newtonsoftjson-nuget-package-to-your-project"></a>將 Newtonsoft.Json NuGet 套件新增至您的專案

Azure Mobile Client SDK 需要 Newtonsoft.Json 套件。 不幸的是，Unity 不支援 NuGet。 如果您在 Visual Studio 中開啟 Unity 專案並新增 NuGet 套件，Unity 會在您下次於 Unity 編輯器中開啟專案時將它清除。 不過，您可以手動將 NuGet 套件新增至 Unity 專案。

1. 在 Unity 專案的 Assets 目錄中建立新的資料夾，並命名為 "**NuGet Packages**"。 這僅供組織使用。

2. 前往 https://www.nuget.org/packages/Newtonsoft.Json/，並按一下 [手動下載] 按鈕。 下載 .nupkg 檔案。

  ![在檔案總管中顯示 Assets 資料夾](media/vstu_azure-prepare-dev-environment-image9.png)

3. 找出新下載的檔案，並將副檔名從 .nupkg 變更為 **.zip**。 這可讓您檢視和解壓縮包含的檔案，就像是任何其他 ZIP 檔案。

4. 將壓縮目錄開啟或解壓縮，並瀏覽至 **\lib\net45**。

5. 將 **Newtonsoft.Json.dll** 檔案複製到 Unity 專案的 **Assets\NuGet Packages** 目錄。

## <a name="add-the-azure-mobile-client-sdk-nuget-package-to-your-project"></a>將 Azure Mobile Client SDK NuGet 套件新增至您的專案

Azure Mobile Client SDK 包含可輕鬆讀取及寫入至 Azure 簡易表的功能。

1. 前往 https://www.nuget.org/packages/Microsoft.Azure.Mobile.Client/，並按一下 [手動下載] 按鈕。 下載 .nupkg 檔案。

2. 找出新下載的檔案，並將副檔名從 .nupkg 變更為 **.zip**。 這可讓您檢視和解壓縮包含的檔案，就像是任何其他 ZIP 檔案。

3. 將壓縮目錄開啟或解壓縮，並瀏覽至 **\lib\net45**。

4. 將 **Microsoft.Azure.Mobile.Client.dll** 檔案複製到 Unity 專案的 **Assets\NuGet Packages** 目錄。

>[!WARNING]
> 完成這些步驟之後，請務必重新啟動 Unity 和 Visual Studio，否則 InteliSense 可能無法辨識剛剛新增的套件。

## <a name="conclusion"></a>結論

完成這些步驟之後，您的 Unity 專案應該已設定好使用 Azure Mobile Client SDK。 您可以在 Unity 專案中建立新的 C# 指令碼，在 Visual Studio 中將它開啟，然後在最上方鍵入下列 using 陳述式，來測試您的開發環境：
```
using System.Net.Http;
using Newtonsoft.Json;
using Microsoft.WindowsAzure.MobileServices;
```

如果 InteliSense 偵測到這些 using 陳述式，設定便已正確完成。 如果有任何錯誤或 InteliSense 無法辨識這些套件，請嘗試重新啟動 Unity 和 Visual Studio。 如果仍然無法運作，請重新審視上述步驟。

## <a name="next-step"></a>後續步驟

* [建立資料模型類別](visual-studio-tools-for-unity-azure-data.md)
