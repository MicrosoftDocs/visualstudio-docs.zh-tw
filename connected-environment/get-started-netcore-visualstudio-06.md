---
title: 使用 Visual Studio 在雲端中以使用 Kubernetes 的容器建立 .NET Core 開發環境 - 步驟 6 - 了解小組開發 | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 04/05/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: douge
ms.openlocfilehash: b4bc1f44e63614346f4e2d149e76becabdcb8c71
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>使用 .NET Core 和 Visual Studio 開始使用已連線的環境

上一個步驟：[呼叫其他容器](get-started-netcore-visualstudio-05.md)

## <a name="learn-about-team-development"></a>了解小組開發

截至目前為止，我們一直在執行我們的應用程式程式碼，就好像自己是唯一使用此應用程式的開發人員一樣。 在本節中，我們會了解已連線的環境如何簡化小組開發：
* 讓一組開發人員在相同的開發環境中工作。
* 支援每位開發人員在隔離狀態下重複他們的程式碼，不用擔心中斷其他人的程式碼。
* 在認可程式碼之前，以端對端方式測試程式碼，不必建立模型或模擬相依性。

## <a name="challenges-with-developing-microservices"></a>開發微服務的挑戰
我們的範例應用程式目前還不是很複雜。 但是在真實世界的開發中，挑戰很快就會出現，因為會新增很多的服務和開發小組。

請想像您正在使用與數十項其他服務互動的服務。

1. 因開發工作而在本機執行所有項目很不切實際。 您的開發電腦可能沒有足夠的資源，無法執行整個應用程式。 或者，您的應用程式可能有需要公開連接的端點 (例如，您的應用程式會回應來自 SaaS 應用程式的 Webhook)。
1. 您可以嘗試只執行您依存的服務，但這表示您需要知道相依性的完整結束 (例如，相依性的相依性)。 或者，因為您並未使用它們，只是不太了解如何建置和執行您的相依性。
1. 有些開發人員會模擬許多服務相依性或建立它們的模型。 這種方法有的時候有用，但管理這些模擬很快就會消耗開發的棈力。 再者，這會讓您的開發環境與生產環境相去甚遠，以至開始出現細微的 Bug。
1. 它會隨著執行任何類型的端對端測試而變得難以處理。 整合測試實際上只會發生在認可後，這表示我們會到開發週期的後期才發現問題。

    ![](media/microservices-challenges.png)

## <a name="work-in-a-shared-development-environment"></a>在共用的開發環境中工作
在已連線的環境中，您可以在 Azure 中設定「共用」的開發環境。 每位開發人員可以只專注於他們的應用程式部分，並可以在已包含其案例所依存之所有其他服務和雲端資源的環境中，反覆開發「預先認可程式碼」。 相依性一律保持最新狀態，而開發人員會以鏡像處理生產環境的方式工作。

## <a name="work-in-your-own-space"></a>在您自己的空間中工作
當您為您的服務開發程式碼，且在準備好要將它簽入之前，程式碼通常不會處於良好狀態。 您仍然要使用解決方案對它進行反覆成形、測試及實驗。 已連線的環境會提供**空間**的概念，讓您能夠在隔離的狀況下工作，不用擔心中斷您小組成員的工作。

請執行下列動作，以確定我們的 `webfrontend` 和 `mywebapi` 服務都在我們的開發環境**和 `mainline` 空間**中執行。
1. 關閉這兩項服務的任何 F5/偵錯工作階段，但在其 Visual Studio 視窗中保持專案開啟。
2. 切換至 `mywebapi` 專案的 Visual Studio 視窗，然後按 Ctrl+F5 執行服務，但不附加偵錯工具
3. 切換至 `webfrontend` 專案的 Visual Studio 視窗，然後也按 Ctrl+F5 執行它。

> [!Note]
有時候在按下 Ctrl+F5 顯示最初網頁後，重新整理瀏覽器是必要的。

開啟公用 URL 並巡覽至 Web 應用程式的任何人都會叫用我們之前寫入，透過這兩項服務使用預設 `mainline` 空間執行的程式碼路徑。 現在假設我們想要繼續開發 `mywebapi` - 我們該如何執行此作業，卻不中斷使用此開發環境之其他開發人員的工作？ 若要這樣做，我們要設定自己的空間。

### <a name="create-a-new-space"></a>建立新的空間
您可以在 Visual Studio 中建立其他的空間，在您以 F5 或 Ctrl+F5 執行服務時使用。 您可以用任何名稱稱呼空間，什麼意思都可以 (例如 `sprint4` 或 `demo`)。

若要建立新的空間，請執行下列動作：
1. 切換至 `mywebapi` 專案的 Visual Studio 視窗。
2. 以滑鼠右鍵按一下 [方案總管] 的專案，然後選取 [屬性]。
3. 選取左邊的 [偵錯] 索引標籤以顯示已連線的環境設定。
4. 您可以在此變更或建立當您使用 F5 或 Ctrl+F5 時所用之已連線的環境及/或空間。 「請確定選取您稍早建立之已連線的環境」。
5. 在 [空間] 下拉式清單中選取 [<Create New Space…>] (<建立新的空間...>)。

    ![](images/Settings.png)

6. 在 [Add Space] (新增空間) 對話方塊中鍵入空間的名稱，按一下 [確定]。 我用自己的名字 ("scott") 為新空間命名，方便我的同事辦識那是我工作的空間。

    ![](images/AddSpace.png)

7. 您現在應該會看到您的開發環境及專案屬性頁面上選取的新空間。

    ![](images/Settings2.png)

### <a name="update-code-for-mywebapi"></a>更新 *mywebapi* 的程式碼

1. 在 `mywebapi`專案中，變更 `ValuesController.cs` 檔案中 `string Get(int id)` 方法的程式碼，如下所示：
 
    ```csharp
    [HttpGet("{id}")]
    public string Get(int id)
    {
        return "mywebapi now says something new";
    }
    ```

2. 在程式碼的這個更新區塊中設定中斷點 (您從前可能已經設定了一個)。
3. 點擊 F5 啟動 `mywebapi` 服務。 這會使用選取的空間啟動您開發環境中的服務，這在我的例子中是 `scott`。

以下是協助您了解不同空間如何運作的圖表。 藍色路徑顯示透過 `mainline` 空間的要求，如果 URL 未附加任何空間，這就是預設使用的路徑。 綠色的路徑顯示透過 `scott` 空間的要求。

![](media/Space-Routing.png)

已連線的環境這項內建功能可讓您在共用環境中以端對端方式測試程式碼，不需要每位開發人員在其空間內重新建立完整的服務堆疊。 請注意，此路由需要在您的應用程式程式碼中轉送傳播標頭，如本指南上一個步驟中所示。

## <a name="test-code-running-in-the-scott-space"></a>測試在 `scott` 空間中執行的程式碼
若要測試我們的新版 `mywebapi` 搭配 `webfrontend`，請在您的瀏覽器中開啟 `webfrontend` 的公用存取點 URL (例如 https://webfrontend-teamenv.vsce.io) 並移至 [關於] 頁面。 您應該會看到原始訊息 "Hello from webfrontend and Hello from mywebapi"。

現在，將 "scott-" 部分新增至 URL，讓它看起來像 https://scott-webfrontend-teamenv.vsce.io，然後重新整理瀏覽器。 您在 `mywebapi` 專案中設定的中斷點應該會被點擊。 按一下 F5 繼續，您現在應該會在瀏覽器中看到新的訊息 "Hello from webfrontend and mywebapi now says something new"。 這是因為您在 `mywebapi` 中的已更新程式碼路徑正在 `scott` 空間中執行。

> [!div class="nextstepaction"]
> [摘要](get-started-netcore-visualstudio-07.md)